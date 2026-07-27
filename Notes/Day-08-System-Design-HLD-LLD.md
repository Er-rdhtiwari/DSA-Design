# Day 8 — System Design Method, HLD Core, and LLD Basics

Today’s practice system is:

> **Design an AgentRun service that starts an agent workflow and tracks status.**

All numbers below are interview assumptions, not hidden facts. State them, ask the interviewer to confirm them, and then calculate consistently.

## A. System Design Interview Framework

### The six-phase flow

#### Phase 1: Clarify functional and non-functional requirements

A **functional requirement** says what the system does. Examples: start a run, read its status, and accept a tool callback.

A **non-functional requirement**, or **NFR**, says how well or under what constraint it must work. Examples: latency, availability, consistency, security, audit, and cost.

First define users, core use cases, scope, and what is deliberately out of scope. Separate MVP requirements from later features. Confirm what “done” means for a run and whether workflows are synchronous or asynchronous.

#### Phase 2: Estimate capacity

Estimate the order of magnitude for:

- average and peak requests per second, or **QPS**;
- storage written per day and retained over time;
- inbound and outbound bandwidth;
- background work such as tool calls and document embeddings;
- cache and queue load.

Capacity shapes the design. A service at 5 QPS can use a simpler topology than one receiving 5,000 QPS and millions of callbacks.

#### Phase 3: Define API contracts

Choose REST or gRPC based on callers and constraints. Define:

- endpoint or method names;
- request and response fields;
- authentication context;
- idempotency for retried writes;
- pagination and filters for lists;
- error model;
- API versioning;
- sync versus async behavior.

For long agent workflows, `start_run` should normally accept quickly and return a run ID. Clients poll, subscribe, or receive callbacks for later state.

#### Phase 4: Define the data model

List entities, relationships, primary keys, tenant keys, mutable status, timestamps, and retention. Then begin with the most important query patterns and add indexes for them.

Do not design tables without queries. “Last 20 runs for a project” directly suggests an index beginning with `project_id` and ordered time.

#### Phase 5: Draw the high-level architecture

Show:

- entry points and authentication;
- stateless online services;
- durable data stores;
- queues and asynchronous workers;
- caches;
- tool and external-system boundaries;
- artifact/document storage;
- telemetry and audit flow.

Explain the normal request path first. Add scale and failure behavior after the basic path is clear.

#### Phase 6: Deep dive, trade off, and summarize

Choose the riskiest parts:

- run-state consistency and duplicate messages;
- queue delivery and idempotent workers;
- tool callback security;
- multi-tenant isolation;
- database and artifact scaling;
- cancellation and long-running recovery.

Close with:

- **reliability:** timeouts, retries, idempotency, reconciliation, fallback, disaster recovery;
- **security:** authentication, authorization, least privilege, secrets, tenant isolation, audit;
- **observability:** logs, metrics, traces, SLOs, alerts, run-level debugging;
- **trade-offs:** what was chosen, what was rejected, and why;
- **summary:** request lifecycle, scale, and next evolution point.

### Reusable clarifying checklist — 18 questions

1. Who starts a run: end users, internal services, scheduled jobs, or all three?
2. What workflow types and tool integrations must the MVP support?
3. Is `start_run` asynchronous, and how quickly must it acknowledge a request?
4. Which run states and terminal outcomes are required?
5. Do clients poll, receive webhooks, or consume a status stream?
6. Can users cancel, pause, retry, or resume a run?
7. What are the expected MAU, DAU, runs per active user, and peak traffic pattern?
8. What are the p95/p99 latency SLOs for starting, reading, and listing runs?
9. What availability target applies to start and status APIs?
10. How long may a workflow run, and what timeout or deadline applies?
11. What consistency is required for status immediately after a transition?
12. Is the platform multi-tenant, and what data or compute isolation is required?
13. Which authentication, authorization, secret, encryption, and data-residency rules apply?
14. What compliance, audit, retention, deletion, and legal-hold requirements apply?
15. What monthly or per-run cost target should guide model, storage, and compute choices?
16. How large can prompts, tool results, artifacts, and ingested documents be?
17. Which external systems, protocols, rate limits, callback contracts, and network constraints must we integrate with?
18. What phase-2 growth, regions, disaster-recovery targets, and provider portability should the design anticipate?

## B. Capacity Estimation

### Core formulas

#### Users

**MAU** means monthly active users. **DAU** means daily active users.

```text
DAU = MAU × daily-active ratio
daily operations = DAU × operations per active user per day
```

The DAU/MAU ratio is a usage assumption. State it instead of quietly inventing it.

#### Average and peak QPS

```text
average QPS = daily requests / 86,400
peak QPS = average QPS × peak factor
```

The peak factor models bursts. Consumer traffic may have much higher peaks than an evenly scheduled internal batch.

#### Payload and bandwidth

```text
daily bytes = daily requests × average bytes per request/response
average bits/second = daily bytes × 8 / 86,400
peak bits/second = average bits/second × peak factor
```

Separate inbound and outbound traffic when one direction is much larger. Include internal model, tool, and artifact traffic in a real cost model.

#### Storage growth

```text
storage/day = objects/day × bytes/object
retained storage = storage/day × retention days
physical storage ≈ retained logical storage × replication/index/overhead factor
```

Break storage into run records, events, tool calls, audit, artifacts, source documents, and embeddings. Large blobs usually belong in object storage; searchable metadata belongs in a database.

#### Cache assumptions

```text
cache hits = read requests × hit ratio
database reads = read requests × (1 - hit ratio)
```

A hit ratio is an assumption, not guaranteed savings. The cache key must include tenant, permissions, object/version, and relevant filters. Status data needs a short TTL or event-based invalidation because active runs change.

### Mini-scenario 1 — AgentRun API traffic

#### Assumptions

- 1.2 million MAU.
- 25% are active daily: `DAU = 1.2M × 0.25 = 300,000`.
- Each DAU starts 12 runs/day.
- Each run receives 6 tool callbacks and 8 status reads.
- Each DAU makes 2 list requests/day.
- Peak factor is 8.
- Average payloads:
  - start request plus response: 2.5 KB;
  - status request plus response: 1.2 KB;
  - list request plus response: 20.2 KB;
  - tool callback plus response: 3.5 KB.

#### Traffic calculations

```text
runs/day = 300,000 × 12 = 3,600,000
start avg QPS = 3,600,000 / 86,400 = 41.7
start peak QPS = 41.7 × 8 = 333.6

status reads/day = 3,600,000 × 8 = 28,800,000
status avg QPS = 333.3
status peak QPS = 2,666.7

list reads/day = 300,000 × 2 = 600,000
list avg QPS = 6.9
list peak QPS = 55.6

callbacks/day = 3,600,000 × 6 = 21,600,000
callback avg QPS = 250
callback peak QPS = 2,000

total average QPS ≈ 632
total peak QPS ≈ 5,056
```

#### API bandwidth

```text
start traffic = 3.6M × 2.5 KB = 9.0 GB/day
status traffic = 28.8M × 1.2 KB = 34.56 GB/day
list traffic = 0.6M × 20.2 KB = 12.12 GB/day
callback traffic = 21.6M × 3.5 KB = 75.60 GB/day

total API traffic = 131.28 GB/day
average bandwidth ≈ 12.2 Mb/s
peak bandwidth ≈ 97.2 Mb/s
```

This excludes model traffic, artifact upload/download, replication, and protocol overhead.

#### Storage growth

Assume:

- run row: 6 KB;
- run state/event history: 20 KB/run;
- each tool execution: 4 KB;
- 8 audit entries/run at 1 KB each;
- 15% of runs create one 2 MB artifact.

```text
run rows = 3.6M × 6 KB = 21.6 GB/day
run events = 3.6M × 20 KB = 72.0 GB/day
tool executions = 3.6M × 6 × 4 KB = 86.4 GB/day
audit = 3.6M × 8 × 1 KB = 28.8 GB/day
artifacts = 3.6M × 0.15 × 2 MB = 1,080 GB/day

total logical storage ≈ 1.29 TB/day
30-day logical retention ≈ 38.7 TB
```

Artifacts dominate, so store them in object storage and apply lifecycle policies.

#### Cache effect

Status plus list reads are `29.4M/day`. With a stated 60% hit assumption:

```text
cache hits = 29.4M × 0.60 = 17.64M/day
database reads = 29.4M × 0.40 = 11.76M/day ≈ 136 QPS average
```

Without the cache, those reads average about 340 QPS. Active-run entries must expire or update quickly to avoid stale status.

### Mini-scenario 2 — Document ingestion: PDF to chunks to embeddings

#### Assumptions

- 100,000 PDFs/day.
- 8 MB average PDF.
- 40 pages/PDF.
- 500 tokens/page, so 20,000 tokens/PDF.
- 500-token chunks with 50-token overlap, giving roughly 450 new tokens per chunk.
- Peak ingestion factor is 10.
- 1,536 embedding dimensions stored as 4-byte values.
- Text plus metadata averages 2 KB/chunk.
- Vector index overhead is 30%.

#### Documents, pages, and chunks

```text
document avg rate = 100,000 / 86,400 = 1.16 PDFs/s
document peak rate = 1.16 × 10 = 11.6 PDFs/s

pages/day = 100,000 × 40 = 4,000,000
page parse avg = 46.3 pages/s
page parse peak = 463 pages/s

chunks/PDF ≈ ceil(20,000 / (500 - 50)) = 45
chunks/day = 100,000 × 45 = 4,500,000
embedding avg rate = 52.1 chunks/s
embedding peak rate = 521 chunks/s
```

In a real system, benchmark parser and embedding batch throughput and size worker pools from measured service time.

#### Bandwidth and storage

```text
raw input = 100,000 × 8 MB = 800 GB/day
raw average bandwidth ≈ 74.1 Mb/s
raw peak bandwidth ≈ 741 Mb/s

one vector = 1,536 × 4 bytes = 6,144 bytes
raw vectors = 4.5M × 6,144 bytes ≈ 27.65 GB/day
vectors with 30% index overhead ≈ 35.94 GB/day
chunk text + metadata = 4.5M × 2 KB = 9 GB/day

total logical growth ≈ 800 + 35.94 + 9 = 844.94 GB/day
```

This estimate reveals separate scaling dimensions: object storage bandwidth, parser CPU/OCR, embedding rate limits and cost, vector-index writes, and metadata persistence.

## C. API Design

### Interview expectations

- Use nouns and HTTP methods consistently.
- Version the contract, for example `/v1`.
- Return quickly for long work with `202 Accepted` and a stable run ID.
- Authenticate every request and derive tenant from trusted identity, not an arbitrary body field.
- Use cursor pagination for large or changing lists.
- Put supported filters in the contract and back common combinations with indexes.
- Use idempotency keys for retried creates, callbacks, and other state-changing requests.
- Define stable status values, timestamps, and error codes.

### The eight case-study APIs

#### 1. `start_run`

```http
POST /v1/projects/{project_id}/runs
Idempotency-Key: <client-generated-key>

{
  "agent_id": "campaign-review-v3",
  "input": {"campaign_id": "CMP-1042", "region": "IN"},
  "deadline_seconds": 900
}
```

```http
202 Accepted
{
  "run_id": "run_123",
  "status": "QUEUED",
  "created_at": "..."
}
```

The idempotency scope is tenant, caller, project, and key. Repeating the same key and payload returns the original run; the same key with a different payload returns a conflict.

#### 2. `get_status`

```http
GET /v1/runs/{run_id}
```

Returns status, timestamps, safe progress summary, terminal result reference, and a version used for conditional polling. Object-level authorization is required.

#### 3. `list_runs`

```http
GET /v1/projects/{project_id}/runs?status=RUNNING&created_after=...&limit=20&cursor=...
```

Sort by `(created_at DESC, run_id DESC)`. Return `next_cursor`; do not expose raw database offsets as the contract.

#### 4. `tool_callback`

```http
POST /v1/runs/{run_id}/tool-executions/{execution_id}/callbacks
Idempotency-Key: <provider-event-id>

{
  "status": "SUCCEEDED",
  "result_ref": "artifact://...",
  "completed_at": "..."
}
```

Authenticate the tool/provider, verify that the execution belongs to the run and expects a callback, reject invalid state transitions, and deduplicate provider events.

#### 5. `ingest_doc`

```http
POST /v1/projects/{project_id}/documents
Idempotency-Key: <source-version-key>

{
  "source_uri": "object://...",
  "content_type": "application/pdf",
  "access_policy_id": "policy_7"
}
```

Returns `202 Accepted` with an ingestion job ID. Validate size, type, malware status, source access, and tenant scope.

#### 6. `search_audit`

```http
GET /v1/tenants/{tenant_id}/audit-logs?from=...&to=...&action=TOOL_FAILED&limit=100&cursor=...
```

This requires privileged audit access, bounded time ranges, cursor pagination, and protected output.

#### 7. `cancel_run`

```http
POST /v1/runs/{run_id}/actions/cancel
Idempotency-Key: <client-generated-key>
```

Cancellation is a requested state transition, not proof that every external operation instantly stopped. Return the current state and reconcile workers/tools.

#### 8. `list_artifacts`

```http
GET /v1/runs/{run_id}/artifacts?type=REPORT&limit=20&cursor=...
```

Return metadata and short-lived authorized download references rather than large artifact bytes in the status response.

### Filtering and pagination rules

- Allow only documented filters and validate their types.
- Set default and maximum page sizes.
- Encode the last sort key and query context in an opaque signed cursor.
- Keep sort order deterministic by adding a unique tie-breaker such as `run_id`.
- Do not let a cursor change tenant, project, filters, or API version.

### Versioning

Use `/v1` for major contract changes. Add compatible optional response fields without breaking old clients. For a breaking status or callback schema, publish a new version, support a migration window, and monitor version usage.

Internal gRPC can use the same logical methods and typed contracts between trusted services, but REST is easy for external and browser-facing clients. The interview should explain the choice rather than claim one is universally better.

### Standard error response

```json
{
  "code": "INVALID_STATE_TRANSITION",
  "message": "A terminal run cannot move back to RUNNING.",
  "request_id": "req_8f91"
}
```

Map stable codes to appropriate HTTP status classes. Keep messages safe for callers; put sensitive debugging detail in protected logs correlated by `request_id`.

## D. Data Model Starter

### Entity outline

Every tenant-owned entity carries `tenant_id` so authorization and data placement are explicit.

| Entity | Primary key and relationships | Important fields |
| --- | --- | --- |
| **Tenant** | PK `tenant_id` | name, plan, region, status, created_at |
| **User** | PK `user_id`; tenant relationship | tenant_id, external_subject, roles, status |
| **Project** | PK `project_id`; belongs to Tenant | tenant_id, name, settings_version, created_at |
| **AgentRun** | PK `run_id`; belongs to Project/Tenant; created_by User | tenant_id, project_id, agent_id, status, input_ref, result_ref, state_version, idempotency_key, created_at, updated_at, terminal_at |
| **ToolExecution** | PK `execution_id`; belongs to AgentRun | tenant_id, run_id, tool_type, status, attempt, idempotency_key, request_ref, result_ref, started_at, completed_at |
| **Artifact** | PK `artifact_id`; belongs to AgentRun | tenant_id, run_id, type, object_uri, checksum, size_bytes, content_type, created_at |
| **Feedback** | PK `feedback_id`; belongs to AgentRun and User | tenant_id, run_id, user_id, rating, reason_code, comment_ref, created_at |
| **AuditLog** | PK `audit_id`; tenant-scoped, optionally links run/user | tenant_id, run_id, actor_id, action, object_type, object_id, outcome, request_id, occurred_at, protected_details_ref |

Use references to object storage for large input, result, artifact, or comment bodies. Store status and queryable metadata in the relational database.

### Relationships and state rules

```text
Tenant 1 ── * User
Tenant 1 ── * Project
Project 1 ── * AgentRun
AgentRun 1 ── * ToolExecution
AgentRun 1 ── * Artifact
AgentRun 1 ── * Feedback
Tenant 1 ── * AuditLog
```

Define an allowed run-state machine, for example:

```text
QUEUED → RUNNING → WAITING_FOR_TOOL → RUNNING
                 → WAITING_FOR_HUMAN → RUNNING
                 → SUCCEEDED | FAILED | CANCELLED | TIMED_OUT
```

Use optimistic concurrency with `state_version` so two workers do not silently overwrite one another. Persist the state change and its outbox event in one database transaction.

### Exactly five secondary indexes

Primary-key access is assumed. These five indexes support the named top queries and core operations:

1. **Last 20 runs for a project**  
   `AgentRun(project_id, created_at DESC, run_id DESC)`

2. **Tenant audit trail by time**  
   `AuditLog(tenant_id, occurred_at DESC, audit_id DESC)`

3. **Tool failures by type and status within a tenant**
   `ToolExecution(tenant_id, tool_type, status, started_at DESC, execution_id DESC)`

4. **Operational search for runs by tenant and status**  
   `AgentRun(tenant_id, status, updated_at DESC, run_id DESC)`

5. **Artifacts for one run**  
   `Artifact(run_id, created_at DESC, artifact_id DESC)`

At larger scale, include tenant in physical partitioning or index prefixes where the database and isolation strategy require it. Avoid speculative indexes: every index consumes write, storage, and maintenance capacity.

## E. LLD Basics

### Four simple ideas

**Responsibility** is the one job a class or component owns. `RunRepository` stores runs; it should not also call models.

**Cohesion** measures how closely the responsibilities inside a component belong together. High cohesion is good: all methods of `RunStateMachine` enforce run transitions.

**Coupling** measures how much one component depends on details of another. Lower coupling is usually easier to test and change. Depend on a `QueuePublisher` interface, not one queue client throughout business code.

An **interface** is a contract describing operations without forcing the caller to know the implementation. Interfaces create test seams and keep storage, queues, and tools replaceable.

### Reusable LLD template

1. **Scope and invariants**
   - Operation being designed.
   - Allowed states and rules that must always hold.
2. **Classes/components**
   - Names and one responsibility each.
3. **Interfaces**
   - Method signatures, inputs, outputs, and errors.
4. **Data and state**
   - Entities, state transitions, concurrency/version rules.
5. **Sequence flow**
   - Ordered calls on success.
6. **Edge cases and failure flow**
   - Duplicate request, timeout, concurrent update, invalid transition, dependency failure.
7. **Tests**
   - Unit, contract, integration, concurrency, and failure tests.

### LLD sketch for `start_run`

| Class/component | Responsibility |
| --- | --- |
| `RunController` | Parse HTTP request and map service result to API response |
| `RunService` | Coordinate validation, idempotency, persistence, and enqueue |
| `RunValidator` | Validate agent, input, deadline, and tenant/project rules |
| `RunStateMachine` | Enforce allowed state transitions |
| `RunRepository` | Read/write run and idempotency records with optimistic concurrency |
| `UnitOfWork` | Commit run plus outbox event atomically |
| `QueuePublisher` | Publish committed outbox work to the workflow queue |
| `AuditWriter` | Record protected security and lifecycle audit events |

Example interfaces:

```python
class RunRepository:
    def find_by_idempotency(self, scope: str, key: str) -> AgentRun | None: ...
    def insert(self, run: AgentRun) -> None: ...
    def get(self, tenant_id: str, run_id: str) -> AgentRun | None: ...
    def update_if_version(self, run: AgentRun, expected_version: int) -> bool: ...

class QueuePublisher:
    def publish_start(self, run_id: str, event_id: str) -> None: ...

class RunStateMachine:
    def transition(self, run: AgentRun, target: RunStatus) -> AgentRun: ...
```

### Sequence flow

```text
Client
  → RunController: start request + idempotency key
  → RunService: authenticated command
  → RunRepository: find existing key
      ├─ same payload found → return original run
      └─ no record
  → RunValidator: validate project, agent, input, deadline
  → UnitOfWork: insert QUEUED run + outbox event
  → commit
  → outbox publisher: enqueue event
  → AuditWriter: record accepted outcome
  → Client: 202 + run_id
```

The outbox makes “database commit succeeded but queue publish failed” recoverable. A relay retries unpublished outbox events.

### Edge cases

- Same idempotency key with the same payload.
- Same key with a different payload.
- User may access tenant but not the project.
- Agent definition is disabled during request.
- Database commit times out with uncertain outcome.
- Outbox relay delivers the event twice.
- Two workers update the same run version.
- Cancellation races with tool completion.
- Run deadline expires while waiting externally.
- Artifact or input exceeds limits.

### Test plan

- Unit-test validation and every state-machine transition.
- Unit-test idempotent same/different-payload behavior.
- Contract-test repository, queue, tool callback, and audit interfaces.
- Integration-test atomic run/outbox commit and relay retry.
- Concurrency-test competing state updates and cancellation.
- Fault-test duplicate queue delivery, timeouts, and worker restart.
- Security-test tenant/object authorization and callback authentication.
- Load-test start/status/list paths at estimated peak and beyond.

## F. Case Study — AgentRun Service

### Deliverable 1: Functional and NFR list

#### MVP functional requirements

- Start a run for an authorized tenant project and agent definition.
- Return a run ID immediately and execute asynchronously.
- Track validated lifecycle states and timestamps.
- Get one run’s current status and result reference.
- List recent project runs with filters and cursor pagination.
- Dispatch tool work and accept authenticated idempotent callbacks.
- Cancel a non-terminal run on a best-effort basis.
- Store artifact metadata and protected object references.
- Ingest a document asynchronously for agent retrieval.
- Search tenant audit events for authorized operators.

#### Phase-2 functional requirements

- Pause/resume and human approval.
- Real-time status stream and outbound webhooks.
- Run retry/fork from a checkpoint.
- Scheduled and batch runs.
- Multi-region execution and tenant placement.
- Model/tool routing policies and per-tenant budgets.
- Advanced evaluation, feedback, and replay.

#### MVP NFRs

- `start_run` p95 under 200 ms and `get_status` p95 under 150 ms, excluding client network.
- 99.9% monthly availability for start and status APIs.
- Durable accepted runs: no loss after returning `202`.
- At-least-once queue delivery with idempotent workers and callbacks.
- Strong tenant/object authorization and encryption in transit/at rest.
- Immutable or integrity-protected audit for security-sensitive events.
- Horizontal API/worker scaling to the estimated 5,056 peak QPS mix.
- Per-run deadlines, tool/model limits, and cost attribution.
- Correlated logs, metrics, and traces with protected payloads.

#### Phase-2 NFRs

- 99.95% availability and defined regional disaster recovery.
- Regional data residency and configurable retention/legal hold.
- Recovery-point and recovery-time objectives agreed per data tier.
- Predictable noisy-neighbor isolation and tenant quotas.
- Provider portability tested behind stable interfaces.
- Automated SLO-based rollout, canary, and rollback gates.

### Deliverable 2: Capacity table

| Dimension | Average | Peak | Storage/day | Bandwidth |
| --- | ---: | ---: | ---: | ---: |
| Start runs | 41.7 QPS | 333.6 QPS | Included below | Included below |
| Status reads | 333.3 QPS | 2,666.7 QPS | — | Included below |
| List reads | 6.9 QPS | 55.6 QPS | — | Included below |
| Tool callbacks | 250 QPS | 2,000 QPS | Included below | Included below |
| Combined API | about 632 QPS | about 5,056 QPS | about 1.29 TB/day logical, artifact-heavy | about 131.28 GB/day; 12.2 Mb/s average, 97.2 Mb/s peak |
| PDF ingestion | 1.16 PDFs/s; 52.1 chunks/s | 11.6 PDFs/s; 521 chunks/s | about 844.94 GB/day logical | about 74.1 Mb/s raw average, 741 Mb/s peak |

Key design effect: online APIs, asynchronous workflow workers, document ingestion workers, relational records, object storage, and vector indexing scale independently.

### Deliverable 3: API set

The eight required APIs are defined in Section C:

1. `start_run`
2. `get_status`
3. `list_runs`
4. `tool_callback`
5. `ingest_doc`
6. `search_audit`
7. `cancel_run`
8. `list_artifacts`

### Deliverable 4: Data model and five indexes

The eight source-required entities and exactly five secondary indexes are defined in Section D. The three priority access paths are:

- last 20 runs for a project;
- tenant audit trail ordered by time;
- tool failures filtered by tenant, tool type, and status.

### High-level architecture

```text
Clients
  → API Gateway / identity / rate limits
  → AgentRun API (stateless)
       ├─ relational DB: run, tool, feedback, audit metadata
       ├─ cache: hot status/list results
       ├─ object store: inputs, results, artifacts, documents
       └─ transactional outbox
             → queue
                 → workflow workers
                      ├─ model gateway
                      ├─ tool gateway / external tools
                      ├─ retrieval service / vector store
                      └─ checkpoint/state updates

Tool providers → authenticated callback API → state transition + outbox
Document API → ingestion queue → parse/chunk/embed workers → vector store
All services → logs, metrics, traces; security events → protected audit
```

#### Start path

The API authenticates and authorizes, resolves idempotency, writes the `QUEUED` run plus outbox event in one transaction, and returns `202`. A relay publishes the event. A worker claims it, moves the run to `RUNNING` with optimistic concurrency, and starts the workflow.

#### Status path

The status API checks object authorization, reads a short-lived cache, falls back to the database, and returns a small safe summary. Large results use signed, short-lived object references.

#### Tool callback path

The callback endpoint authenticates the provider, verifies the expected execution and run, deduplicates the provider event, validates the transition, stores result metadata, writes a continuation outbox event, and responds. The workflow worker resumes asynchronously.

#### Reliability deep dive

- Transactional outbox prevents accepted runs from being lost between DB and queue.
- At-least-once delivery plus idempotent event/tool keys handles duplicates.
- Optimistic versions protect state transitions.
- Leases and heartbeats detect stuck workers.
- Dead-letter queues hold repeatedly failing messages for controlled recovery.
- Reconciliation finds queued-but-unpublished, stale-running, or callback-mismatch cases.
- Per-stage deadlines, bounded retries, jitter, and circuit breakers limit dependency failures.
- Database backups, object versioning, restore drills, and later regional failover support recovery.

#### Security deep dive

- Gateway authentication plus service-side tenant/object authorization.
- Tenant IDs come from verified identity and stored relationships.
- Short-lived service credentials and least-privilege tool identities.
- Callback signatures or mutual authentication plus replay protection.
- Encryption, secret management, data minimization, and malware scanning.
- Protected audit records for access and state-changing actions.
- Prompt/tool inputs are untrusted and cannot bypass execution policy.

#### Observability and cost deep dive

- Trace one `request_id`, `run_id`, event ID, and tool execution ID across services.
- Measure API and queue latency, run duration, status transitions, retries, stuck runs, tool/model error rates, tokens, artifacts, cache hit rate, and cost per successful run.
- Alert on SLO burn, queue age, terminal failure spikes, callback authentication failures, outbox lag, and cost anomalies.
- Keep restricted prompts, tool results, and artifacts out of ordinary logs.

### Deliverable 5: 6-minute-15-second interview script

#### 0:00–0:40 — Frame the problem

> I will design an asynchronous AgentRun service that accepts a workflow request, returns a run ID, and tracks status through tool/model steps. I’ll clarify scope, estimate traffic, define APIs and data, draw the async architecture, then deep-dive reliability, security, and observability.

#### 0:40–1:30 — State requirements

> For MVP I support start, get, list, authenticated tool callbacks, cancellation, artifacts, document ingestion, and audit search. I assume multi-tenancy, p95 start under 200 ms, 99.9% availability, durable accepted runs, at-least-once work delivery, and strong tenant isolation. Human approval, streams, and multi-region are phase 2.

#### 1:30–2:10 — Size it

> With 300,000 DAU and 12 runs per DAU, we create 3.6 million runs per day. The total workload is about 632 average and 5,056 peak QPS after status polls, lists, and tool callbacks. Logical growth is about 1.29 TB/day because artifacts dominate. This pushes large payloads to object storage and requires independent API, worker, and storage scaling.

#### 2:10–2:55 — Define contracts and data

> `POST /v1/projects/{id}/runs` uses an idempotency key and returns `202` plus `run_id`. Get and list use object authorization and cursor pagination. Tool callbacks are authenticated and idempotent. Core tables are AgentRun, ToolExecution, Artifact, Feedback, AuditLog, plus Tenant, User, and Project. Indexes follow the top project-run, tenant-audit, and tool-failure queries.

#### 2:55–4:10 — Walk the architecture

> The gateway authenticates and rate-limits. A stateless AgentRun API stores a queued run and an outbox event atomically, then returns. The outbox relay publishes to a queue. Workflow workers update versioned state and call model, retrieval, or tool gateways. Relational storage holds queryable state; object storage holds large inputs and artifacts; a cache serves hot status reads. Tool callbacks persist a validated transition and enqueue continuation. Document workers parse, chunk, embed, and write a vector index separately.

#### 4:10–5:25 — Deep-dive failures and security

> Queue delivery is at least once, so every event and external effect has an idempotency key. Optimistic state versions handle competing workers; leases, deadlines, dead letters, and reconciliation recover stuck work. Callback providers are authenticated with replay protection. Tenant and object authorization is checked on every API, tool credentials are least privilege, and audit records cover state-changing actions.

#### 5:25–6:15 — Observe, trade off, and close

> I trace request, run, event, and tool IDs across the critical path and monitor SLOs, queue age, retries, stuck runs, tool/model errors, cache hit rate, and cost per successful run. The main trade-off is simple at-least-once asynchronous execution plus idempotency versus a much more complex exactly-once claim. The MVP is a single-region durable control plane with stateless horizontal scaling; phase 2 adds approvals, streaming, regional placement, and disaster recovery.

## 12 Common Mistakes in Requirements, Capacity, and APIs

1. Starting with a database or framework before clarifying users and core flows.
2. Mixing MVP and phase-2 features until the design has no clear boundary.
3. Saying “scalable and reliable” without numeric latency, availability, traffic, or retention assumptions.
4. Calculating average QPS but ignoring bursts and peak factor.
5. Counting run rows while ignoring tool events, audit, artifacts, embeddings, and replication overhead.
6. Mixing KB, MB, GB, bytes, and bits without showing units.
7. Claiming a cache hit ratio without explaining keys, freshness, invalidation, or the resulting database load.
8. Making a long workflow synchronous and holding the client connection open.
9. Omitting idempotency from start, callback, cancellation, or other retried writes.
10. Using offset pagination for a large, actively changing run history without discussing drift and cost.
11. Returning inconsistent free-form errors without a stable code and request ID.
12. Trusting tenant IDs, tool callbacks, or state transitions without object-level authorization and validation.

## 10 Interview Q&A

### 1. Why return `202 Accepted` instead of waiting for completion?

Agent workflows can take seconds, minutes, or hours and depend on tools. `202` keeps the API latency bounded and gives the client a stable run ID while durable workers continue.

### 2. How do you avoid creating duplicate runs?

Require an idempotency key, scope it to tenant/caller/project, store it with a request fingerprint, and atomically return the original run for the same request. Reject key reuse with different input.

### 3. Why use both a database and a queue?

The database is the durable queryable source of run state. The queue distributes asynchronous work and absorbs bursts. A transactional outbox connects them without losing accepted work.

### 4. Is exactly-once workflow execution guaranteed?

Across distributed systems, a practical design uses at-least-once delivery with idempotent handlers, effect keys, state versions, and reconciliation. Claiming exactly once without defining the boundary is misleading.

### 5. How do concurrent workers avoid corrupting status?

Use allowed state transitions plus optimistic concurrency on `state_version`. Only one update from an expected version succeeds; the other worker reloads and decides whether its work is already complete or obsolete.

### 6. How do you secure tool callbacks?

Authenticate the provider, verify tenant/run/execution relationships, check expected callback state, validate schema and result references, apply replay/idempotency protection, and audit the outcome.

### 7. Why cursor pagination?

A cursor continues after the last stable sort key, so it scales better and avoids much of the duplication/skipping caused by inserts during offset pagination.

### 8. What would you cache?

Cache short-lived authorized status and recent-list results, keyed by tenant, access scope, object/filter, and version. Do not put large artifacts in the cache, and invalidate or use short TTLs for active runs.

### 9. What happens when a worker dies after an external tool acted?

The tool call uses an effect idempotency key. On recovery, the worker queries or reconciles that effect before retrying. The run checkpoint records the tool execution ID and uncertain outcome.

### 10. What would force the next architecture change?

Regional data residency, much higher write volume, very large audit retention, strict availability, or noisy-neighbor problems may require regional cells, database partitioning, dedicated tenant capacity, event streaming, and stronger disaster recovery.

## Cheat Sheet — My Reusable System Design Skeleton

### 1. Requirements

```text
Actors and top 3 flows
MVP versus phase 2
States and consistency
Latency and availability SLO
Multi-tenant/security/compliance
Retention, cost, integrations, and scale
Out of scope
```

### 2. Capacity

```text
DAU = MAU × active ratio
daily requests = DAU × operations/user/day
average QPS = daily requests / 86,400
peak QPS = average QPS × peak factor
storage/day = objects/day × bytes/object
bandwidth = bytes/day × 8 / 86,400
DB reads after cache = reads × (1 - hit ratio)
```

### 3. Contracts

```text
Versioned REST/gRPC shape
Async acceptance for long work
Authentication and object authorization
Idempotency for state changes
Cursor pagination + filters + deterministic sort
Stable error: code, message, request_id
```

### 4. Data

```text
Entities and ownership
Primary/foreign/tenant keys
State machine and timestamps
Large blobs in object storage
Indexes from top query patterns
Retention, partitioning, and deletion
```

### 5. High-level architecture

```text
Client → gateway → stateless API → durable DB
                           └→ outbox → queue → workers
Workers → model/retrieval/tool gateways
Large data → object storage
Hot reads → cache
All paths → logs, metrics, traces, audit
```

### 6. Deep dives and close

```text
Reliability: idempotency, timeout, retry, outbox, reconciliation, DR
Security: authn/authz, tenant isolation, least privilege, secrets, audit
Observability: SLOs, trace IDs, queues, errors, cost, business outcome
Trade-offs: chosen option, alternative, reason, evolution trigger
Summary: request lifecycle + scale + biggest risk + phase 2
```

### Memory line

> **Requirements → capacity → APIs → data → architecture → deep dives and trade-offs.**
