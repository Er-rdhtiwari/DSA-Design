## Day 1 to Day 5 (Copy-paste prompts)

### Day 1 — Baseline + JD mapping (Arrays/Hashing + Fault-tolerant design + FastAPI contract)

```text
You are my JPMorgan Lead Software Engineer (Python + AI/ML) interview coach.
JD focus: AI-native SDLC agent fabric, multi-agent orchestration (LangGraph/A2A/MCP), RAG + vector DB, Python/FastAPI/Pydantic, AWS (EKS/Lambda/S3/Terraform), CI/CD, observability, tool integrations (Jira/Git/Terraform).

Rules for today:
- Be strict and interview-like. Ask clarifying questions where needed.
- For DSA: do NOT reveal solution immediately. Let me attempt first.
- For HLD/LLD: produce clear checklists + diagram + API contracts + failure modes.
- Output must be structured exactly in these sections:
  (A) DSA Round
  (B) System Design (HLD) Round
  (C) Low-Level Design (LLD) Round
  (D) Code Review Mini-Round (10 mins)
  (E) Behavioral (STAR)
  (F) Recap + Homework

(A) DSA Round (Arrays/Hashing)
1) Give me 2 problems:
   - Q1 easy (hashmap/set)
   - Q2 medium (hashmap + prefix/suffix or frequency)
2) For each: provide constraints + 2 sample tests.
3) Timebox: 25 minutes per medium.
4) After my attempt, provide:
   - optimal approach + complexity
   - edge cases checklist
   - “pattern recognition” triggers (how to spot hashing)
   - common mistakes in Python (mutability, default dict, off-by-one)
   - 5 extra testcases to validate.

(B) System Design (HLD) Round — “Agent Gateway” (multi-tenant)
Design an “AI Agent Gateway” that routes requests to agents (docgen/testgen/codegen/observability) and supports:
- multi-tenant isolation, RBAC, audit logs
- tool calling (Jira/Git/Terraform) via connectors
- RAG (vector DB) for grounding in internal docs
- streaming responses, rate limits, budgets (tokens/cost)
- deployments on AWS (EKS; optionally Lambda for async tasks)
Deliverables:
1) Requirements: functional + NFR (latency p95, availability, compliance)
2) High-level architecture diagram (ASCII)
3) Core services & responsibilities (Gateway, Orchestrator, RAG service, Tool Connectors, Observability)
4) Data stores: which DB for what (relational vs KV vs vector)
5) APIs: at least 6 endpoints (run, status, cancel, feedback, ingest, health)
6) Failure modes + mitigations: retries/backoff, circuit breaker, timeouts, idempotency, DLQ
7) Security: authn/authz, secrets, prompt logging redaction/PII, least privilege
8) Scaling & cost: caching, batching, autoscaling, quotas, tenant throttling
9) Observability: traces/metrics/log schema (correlation_id)
10) “MVP → Production” plan in phases.

(C) Low-Level Design (LLD) Round — FastAPI + Pydantic contracts
Create:
- Pydantic models: AgentRunRequest, AgentRunResponse, ToolCall, ToolResult, ErrorModel
- Streaming option: SSE (server-sent events) payload model
- Validation rules: tenant_id required, max_input_size, allowed_agent_types enum
- Correlation IDs: middleware approach
- Retry policy object + timeout config
Provide:
1) class/interface design (AgentRunner, Orchestrator, ToolAdapter)
2) code skeletons (FastAPI router + dependency injection)
3) structured error handling strategy (HTTP codes + error codes)
4) unit test plan (pytest): validation, timeouts, idempotency, tool failures.

(D) Code Review Mini-Round (10 mins)
Give me a short snippet (20–40 lines) that contains:
- at least 4 issues (hardcoded secret, missing timeouts, bad logging, missing validation).
Ask me to point them out; then show the ideal review comments.

(E) Behavioral (STAR)
Ask me 4 lead-level questions:
- mentoring, conflict, ownership, incident/postmortem.
After my answers, refine them into crisp 60–90 sec STAR responses.

(F) Recap + Homework
- 1-page checklist to revise tomorrow
- 2 LC problems as homework mapped to today’s patterns
- 5 “JPMC-style follow-ups” I should practice for this system.
```

### Day 2 — Sliding Window + RAG system (vector DB + grounding) + schema LLD

```text
You are my JPMorgan Lead Python + AI/ML interview coach (same JD).
Follow the same strict structure and rules as Day 1.

(A) DSA Round (Sliding Window / Two Pointers)
1) Give:
   - Q1: classic sliding window (easy/medium)
   - Q2: harder window with constraints (distinct count / min window / at most K)
2) I attempt first. Afterward, give:
   - brute → optimal progression
   - invariant explanation (what stays true in the window)
   - complexity + edge cases
   - common pitfalls (shrinking logic, counters)
   - 6 testcases including extremes.

(B) HLD — “RAG Knowledge Service” for SDLC agents
Design a RAG service that answers ONLY from approved corp docs and supports:
- ingestion pipeline: load → chunk → embed → index
- hybrid retrieval (keyword + vector) + rerank (conceptual)
- metadata filters: tenant_id, repo, docType, timestamp
- strict grounding + citation support
- handling updates: re-index, versioning, tombstones, dedup
Deliverables:
1) Data flow: ingestion vs query flow (ASCII)
2) Chunking strategy choices (heading-based vs fixed) + overlap rationale
3) Vector DB choice tradeoffs (latency, filtering, scaling)
4) Query pipeline steps: rewrite → retrieve → rerank → assemble → generate
5) Guardrails: “answer unknown if not found”, hallucination control
6) Evaluation: retrieval metrics (Recall@K), answer quality rubric, regression tests
7) Ops: monitoring (retrieval latency, hit rate, chunk count), cost controls.

(C) LLD — schemas + interfaces
Provide:
- Pydantic models for DocumentMeta, Chunk, EmbeddingRecord, RetrievalRequest/Response
- Vector schema: id, embedding, text, metadata fields, tenant partitioning
- Interfaces: Chunker, Embedder, IndexWriter, Retriever, Reranker
- Pseudocode for retrieve() + context assembly (ordering, truncation)
- Test strategy: golden queries + drift detection.

(D) Code Review Mini-Round
Short snippet showing a buggy retrieval (wrong filters, leaking tenant data).
I identify issues; you provide corrected version.

(E) Behavioral
Ask 3 questions on “data privacy + compliance” and “handling ambiguity in requirements.”

(F) Recap + Homework
- 1-page RAG cheat sheet (pipeline + knobs)
- 2 DSA problems (sliding window)
- 5 follow-up design questions (scale, compliance, freshness).
```

### Day 3 — Stack/Queue + Multi-agent orchestration (LangGraph/A2A) + state machine LLD

```text
Act as my JPMorgan Lead AI-native SDLC interview coach (same JD).
Keep it strict, structured, and interactive.

(A) DSA Round (Stack/Queue)
1) Give:
   - Q1: monotonic stack OR parentheses validation (easy)
   - Q2: medium (next greater element / decode string / sliding window max)
2) After my attempt: optimal solution + stack invariant + pitfalls + tests.

(B) HLD — “Multi-Agent Orchestrator”
Design orchestrator for planner → executor → verifier agents with:
- shared typed state, branching, loops, retries
- tool calling policy and approvals (human-in-loop)
- timeouts, cancellation, partial results
- guardrails: max steps, budget limit, safe fallbacks
- execution modes: sync vs async (queue-based)
Deliverables:
1) Orchestration patterns comparison: single-agent vs planner-executor vs graph
2) State design: what goes into state (inputs, retrieved context, tool outputs, scores)
3) Reliability: retry/backoff, idempotency, DLQ, “stuck workflow” detection
4) Security: tool permissions per tenant/user role
5) Observability: per-step trace + step metrics + error taxonomy.

(C) LLD — State machine / LangGraph-like graph
Provide:
- Pydantic State model (AgentState) and node output models
- Node interface: run(state) -> state delta
- Retry policy wrapper + timeout wrapper
- Example nodes: PlanNode, RetrieveNode, ToolNode, VerifyNode, FinalizeNode
- Minimal code skeleton (not full project) showing how nodes connect + branching.

(D) Code Review Mini-Round
Snippet with bad retry loop / missing timeouts / non-idempotent tool call.
I review; you show ideal fix.

(E) Behavioral
Ask: “Tell me about a time you designed a framework/platform used by others.”

(F) Recap + Homework
- Orchestrator checklist + failure modes list
- 2 DSA problems on stack/queue
- 5 “what-if” questions (agent misbehaves, tool fails, budget exceeded).
```

### Day 4 — Trees + Tool connectors (Jira/Git/Terraform) + Adapter pattern LLD

```text
You are my JPMorgan Lead Engineer interview coach (same JD).
Be strict and cover all subtopics; interactive for DSA.

(A) DSA Round (Trees)
1) Give:
   - Q1: traversal/level-order (easy)
   - Q2: medium (LCA / serialize-deserialize / path sum variant)
2) After my attempt: recursion vs iterative tradeoffs, complexity, edge cases (nulls, skewed), tests.

(B) HLD — “Tool Connector Layer”
Design connector service to integrate agents with Jira + GitHub/Bitbucket + Terraform:
- auth: OAuth/token, service accounts, least privilege
- secret management: AWS Secrets Manager/SSM
- audit logs: who called what tool and why
- rate limits + backpressure
- sandbox mode vs production mode for Terraform actions
- PR workflow: create branch, commit, open PR, request reviewers
Deliverables:
1) Component diagram + data flow
2) Tool abstraction model (tool registry, capabilities, permissions)
3) Failure handling: retries, idempotency, partial commits rollback plan
4) Security controls: allowlist actions, approval gates, policy-as-code
5) Observability: tool call latency, error rates, per-tool dashboard metrics.

(C) LLD — Adapter + Policy
Provide:
- Interfaces: ToolAdapter, ToolRequest, ToolResponse
- Concrete adapters: JiraAdapter, GitAdapter, TerraformAdapter
- Policy engine: checks user role + action type + resource scope
- Example FastAPI endpoints: /tools/execute, /tools/capabilities
- Unit tests: mocking external APIs, contract tests, replay tests.

(D) Code Review Mini-Round
Snippet with insecure webhook verification or hardcoded tokens—review and fix.

(E) Behavioral
Ask: “How do you mentor juniors and enforce engineering standards without slowing delivery?”

(F) Recap + Homework
- Tool integration checklist (auth, rate limit, audit, safety)
- 2 tree problems as homework
- 5 follow-up questions on compliance + approvals.
```

### Day 5 — Graphs + Event-driven SDLC workflow + Idempotency/Retry LLD

```text
Act as my JPMorgan Lead Engineer interview coach (same JD).
Strict interview format.

(A) DSA Round (Graphs BFS/DFS)
1) Give:
   - Q1: BFS/DFS basic (islands / connected components)
   - Q2: medium (topological sort / shortest path in unweighted / clone graph)
2) After my attempt: visited rules, recursion depth pitfalls, complexity, 6 testcases.

(B) HLD — “Event-driven SDLC Workflow”
Design SDLC automation workflow:
TicketCreated → DesignDocGenerated → PRCreated → TestsGenerated → CITriggered → DeployCanary → Observe → Rollback/Promote.
Use event-driven approach conceptually (EventBridge/SQS/Step Functions).
Deliverables:
1) Events list (name, schema, producer/consumer)
2) Exactly-once-ish handling: idempotency keys + dedupe store
3) Workflow state storage: relational vs KV
4) Retry + DLQ strategy; poison message handling
5) Concurrency control: avoid double PR creation
6) Backpressure: queue depth autoscaling signals
7) Security: event signing, tenant isolation, audit
8) MVP → Prod plan + runbook outline.

(C) LLD — Idempotency + Retry library
Provide:
- Python idempotency decorator/middleware concept
- Data model for IdempotencyRecord (key, status, response hash, expiry)
- Retry/backoff policy (jitter), circuit breaker outline
- FastAPI integration skeleton + unit test plan.

(D) Code Review Mini-Round
Review a message consumer with duplicate-processing bug.

(E) Behavioral
Ask: “Tell me about an incident you owned end-to-end and what you changed afterward.”

(F) Recap + Homework
- Graph cheat sheet
- 2 graph problems
- 10 rapid-fire questions on reliability patterns.
```

---

## Day 6 to Day 10 (Copy-paste prompts)

### Day 6 — Heaps/TopK + LLM inference performance (batch/cache/stream) + SSE LLD

```text
You are my JPMorgan Lead AI/ML + Python interview coach (same JD).
Focus today on performance + cost + latency—like a production system.

(A) DSA Round (Heap/TopK)
1) Q1: easy heap/top-k
2) Q2: medium involving heap + frequency/streaming
After my attempt: complexity, memory, edge cases, tests, and alternatives (sort vs heap vs quickselect).

(B) HLD — “Inference & Serving Layer”
Design an LLM serving layer that supports:
- streaming responses (SSE/WebSocket)
- batching (dynamic batching), concurrency limits
- caching: prompt cache + response cache (cache keys, TTL, invalidation)
- rate limits per tenant/user; token/cost budgets
- model routing (small model vs big model) and fallbacks
- autoscaling signals; p95 latency SLO
- safe timeouts; partial responses; cancellation
Deliverables:
1) Architecture + request lifecycle
2) Performance knobs (batch size, max tokens, streaming chunk size)
3) Cost controls: quotas, budgets, sampling logs, selective tracing
4) Failure handling: upstream LLM errors, retries policy, circuit breaker
5) Observability: latency breakdown (queueing vs inference vs network), token usage metrics.

(C) LLD — Streaming endpoint + cache
Provide:
- FastAPI SSE endpoint skeleton with async generator
- Response event types: token, tool_call, tool_result, final, error
- Cache key design: tenant + agent + prompt hash + tool config + prompt version
- Unit tests: streaming, cancellation, cache hit/miss, timeout.

(D) Mini PR Review
Snippet with no timeout or blocking call inside async—fix it.

(E) Behavioral
Ask 3 questions on “how you optimize costs and justify tradeoffs.”

(F) Recap + Homework
- 1-page inference optimization checklist
- 2 heap problems homework
- 5 follow-up design questions (scale to 10x, multi-region, compliance).
```

### Day 7 — Greedy/Intervals + CI/CD + Canary/Rollback + config/prompt versioning LLD

```text
Act as my JPMorgan Lead Engineer interview coach (same JD).

(A) DSA (Intervals/Greedy)
1) Q1: merge intervals or meeting rooms
2) Q2: medium greedy scheduling
After: proof intuition, pitfalls, complexity, tests.

(B) HLD — “CI/CD for Agent Services”
Design CI/CD pipeline for:
- Python services (FastAPI) + infra (Terraform) + Helm
- automated tests: unit, integration, contract, security scans
- canary deployment and rollback
- versioning: prompts, tools, agent graphs, RAG index versions
- environment strategy: dev/stage/prod, feature flags
Deliverables:
1) Pipeline stages diagram
2) Release strategy: blue/green vs canary; when to choose what
3) Rollback plan including DB/schema migrations strategy
4) Policy gates: approvals for Terraform apply and prod releases
5) Observability gates: SLO-based promotion (error rate, p95, token cost).

(C) LLD — Versioned configuration
Provide:
- Data models: PromptVersion, AgentGraphVersion, ToolConfigVersion
- Safe rollout mechanism: feature flag + percentage routing per tenant
- Example “config resolution” function: (tenant, agent, env) -> effective config
- Test plan: regression test suite for prompts and tools.

(D) Mini Code Review
Snippet showing “prompt changes shipped without tests”—review and fix.

(E) Behavioral
Ask: “How do you ensure quality and speed in a fast-moving platform team?”

(F) Recap + Homework
- CI/CD + rollout cheat sheet
- 2 interval/greedy problems homework
- 8 follow-up questions on release safety.
```

### Day 8 — DP basics + Observability/Monitoring (LLM + agents) + logging schema LLD

```text
You are my JPMorgan Lead Engineer interview coach (same JD).
Today emphasis: monitoring after deployment + “what do you look for once live?”

(A) DSA (DP Basics)
1) Q1: DP easy (climbing stairs / house robber style)
2) Q2: DP medium (subset/partition/knapsack-ish)
After: brute -> memo -> tabulation, state definition, transitions, tests, complexity.

(B) HLD — “Observability for Agent Fabric”
Design monitoring for:
- agent workflows (per-step tracing)
- tool calls (latency/error)
- RAG retrieval (hit rate, recall proxies)
- model usage (tokens/cost), hallucination/grounding checks
- privacy: PII redaction, sampling, retention policy
Deliverables:
1) What to log vs never log (privacy)
2) Metrics catalog (golden signals + AI-specific signals)
3) Tracing approach (correlation_id, trace_id propagation)
4) Dashboards: 5 core dashboards + alert rules
5) Incident runbook outline + postmortem template.

(C) LLD — Logging + tracing schema
Provide:
- JSON log schema: timestamp, tenant_id, workflow_id, step_id, model, tokens, latency_ms, outcome, error_code
- Middleware code skeleton: correlation id injection, structured logger
- Redaction approach: regex + allowlist fields
- Unit tests: redaction correctness + log completeness.

(D) Mini Review
Bad logging snippet with PII leakage—fix it.

(E) Behavioral
Ask: “How do you handle incidents and communicate with stakeholders?”

(F) Recap + Homework
- 1-page observability checklist
- 2 DP problems homework
- 10 rapid-fire monitoring questions.
```

### Day 9 — Mixed DSA (timed) + End-to-end “AI-native SDLC” HLD + service boundaries LLD

```text
Act as my JPMorgan Lead Engineer interview coach (same JD).
Today is end-to-end integration day.

(A) DSA Timed Round
- Give me 1 medium from any past pattern, timed 35 mins.
- After my attempt: optimization, edge cases, tests, and “how to explain in interview”.

(B) HLD — Full “AI-native SDLC Agent Fabric”
Design complete system:
Jira issue → plan → retrieve context → generate design doc → create PR → generate tests → run CI → canary deploy → monitor → rollback/promote.
Must include:
- multi-tenant RBAC and audit trails
- tool permissions + approvals
- RAG knowledge boundaries (answer only from approved datasets)
- budgets/cost controls
- reliability: retries/DLQ/idempotency/circuit breakers
- compliance: logging policies, retention, data residency (conceptual)
Deliverables:
1) Architecture diagram + sequence diagram (ASCII)
2) Service boundaries + responsibilities + APIs between services
3) Data model overview (tables/entities and keys)
4) Key tradeoffs: monolith vs microservices; sync vs async; DB choice
5) “MVP → Production” roadmap in 3 phases.

(C) LLD — Service interfaces
Provide:
- API contracts between Gateway, Orchestrator, RAG, Tools, Observability
- Error taxonomy and retryability matrix (which errors retry)
- Contract testing plan.

(D) Mini Review
Review a “service boundary mistake” example (leaky abstraction).

(E) Behavioral
Ask: “How do you influence cross-functional stakeholders and set technical direction?”

(F) Recap + Homework
- 1-page final architecture checklist
- 2 mixed DSA homework problems
- 10 follow-up design questions.
```

### Day 10 — Mock 1 (coding + system design + LLD + code review) with scorecard

```text
Day 10 = Full Mock Interview 1 for JPMorgan Lead Python + AI/ML role (same JD).
Be strict, timed, and score me.

Round 1: Code Review (10 mins)
- Give a PR snippet with at least: hardcoded secret, missing timeout, poor logging, no validation.
- I identify issues; you provide ideal review comments.

Round 2: Coding (45 mins)
- Give 1 LeetCode-medium style problem.
- Enforce: clarify requirements, propose approach, write code, test, analyze complexity.
- After: provide reference solution + grading rubric (communication, correctness, complexity, tests).

Round 3: System Design (60 mins)
Question: “Design a large-scale fault-tolerant system and explain how you take MVP → production.”
Then steer it toward my JD: agent fabric / tool integrations / AWS / observability.
Push on:
- failures, retries, rate limits
- data stores, tenancy, RBAC
- CI/CD, canary, rollback
- monitoring/alerts and runbook
After: scorecard + 5 prioritized improvements.

Round 4: LLD (25 mins)
Design FastAPI /agent/run with:
- streaming (SSE), retries, timeouts, idempotency, structured logs, error model.
Provide skeleton + tests outline.

Final Output:
- Overall score (0–10)
- Strengths
- Weaknesses
- Next 3 days micro-plan.
```

---

## Day 11 to Day 15 (Copy-paste prompts)

### Day 11 — Revision day (DSA patterns + HLD templates + LLD patterns)

```text
You are my interview coach (same JD).
Today is revision + consolidation. Output must be crisp but complete.

(A) DSA Pattern Revision
Create a revision pack:
1) For each pattern: hashing, sliding window, stack, tree, graph, heap, DP
2) Give:
   - “When to use” triggers
   - 1 canonical problem example
   - 3 common mistakes
   - 5-line template/pseudocode.

(B) HLD Template Drill
Give me a universal system design template for JPM:
- requirements (functional + NFR)
- capacity planning quick math
- architecture + data flow
- data stores + schemas (high level)
- reliability + security + observability
- cost + rollout plan
Then give 3 short design drills (10 mins each) and expected checklist.

(C) LLD Pattern Drill (Python/FastAPI)
Provide reusable patterns:
- Pydantic validation patterns
- dependency injection
- async + concurrency safety
- retries/timeouts/circuit breaker
- idempotency keys
- structured errors
- test strategy (unit/integration/contract)
End with 1-page cheat sheet.
```

### Day 12 — Mock 2 (resiliency heavy + behavioral)

```text
Full Mock Interview 2 (same JD). Focus: resiliency, fault tolerance, productionization.

Round 1: System Design (70 mins)
Question: “Improve an existing monolith to handle 50x traffic and make it fault tolerant.”
You must:
- ask clarifying Qs
- propose target architecture
- discuss rollout strategy (strangler pattern), canary, rollback
- address data migrations, caching, queues
- add monitoring, SLOs, incident response
Then connect it to JD by adding: “integrate an AI agent service into this system safely.”

Round 2: Coding (40 mins)
1 medium problem (timed). Evaluate communication and tests.

Round 3: Behavioral (20 mins)
Ask 6 lead-level questions:
- conflict resolution
- stakeholder management
- mentoring
- ownership
- handling pressure/incidents
- making tradeoffs

End with scorecard + top weaknesses + targeted drills for Day 13.
```

### Day 13 — Mock 3 (Agent + RAG + tool integrations)

```text
Mock Interview 3 (same JD). Focus: agent orchestration + RAG + toolchain integrations.

Round 1: System Design (70 mins)
Design “AI-native SDLC assistant”:
- multi-agent orchestrator (LangGraph/A2A style)
- RAG service (vector DB, metadata filters, strict grounding)
- tool connectors: Jira + Git + Terraform
- approvals + RBAC + audit trails
- deployment on AWS (EKS; optional Step Functions/SQS)
- observability: traces, metrics, logs, redaction
Push me on failure modes: tool failures, hallucination, tenant leakage, retries, budgets.

Round 2: LLD (35 mins)
Implement design for:
- ToolAdapter interface + 2 concrete adapters
- Orchestrator state model + node interface
- /agent/run endpoint with SSE
Include test plan (mock tools, contract tests).

Round 3: Short Coding (20 mins)
1 short problem (stack/graph) to test speed.

End with:
- architecture ASCII diagram
- 10 follow-up questions + ideal answers outline
- final improvement list.
```

### Day 14 — Rapid revision + “Answer in 2 minutes” practice + STAR polishing

```text
Day 14 = Rapid Revision + Communication polishing.

(A) DSA Rapid-fire
Give 12 quick checks:
- 6 conceptual (choose pattern, complexity, edge cases)
- 6 mini coding snippets (fix bug / fill missing logic)
Include Python pitfalls (mutable defaults, recursion depth, integer overflow not in python but indexing, perf).

(B) HLD “2-minute pitch”
Give me 5 prompts where I must explain a design in 2 minutes:
- agent gateway
- RAG service
- tool connector safety
- inference optimization
- observability strategy
After each, critique my clarity + missing points.

(C) Behavioral STAR
Help craft 8 STAR stories mapped to JD:
- building platform/framework
- integrating tools/APIs
- CI/CD improvements
- incident handling
- mentoring/leadership
- security/compliance decision
- performance optimization
- ambiguous requirements
Output them as 60–90 sec scripts.

(D) Final checklist
Provide 1-page “day-before-interview checklist”.
```

### Day 15 — Final full loop simulation + 1-page cheat sheets

```text
Day 15 = Final full simulation (same JD). Treat this like the real on-site/superday.

Round 0: PR Review (10 mins)
Find security/reliability/style issues and propose fixes.

Round 1: Coding (45 mins)
1 LeetCode-medium style question; strict on edge cases and tests.

Round 2: System Design (75 mins)
Choose one and interview me hard:
Option A: “AI-native SDLC agent fabric (multi-agent + RAG + toolchain + AWS).”
Option B: “Fault tolerant system + MVP→prod + scale 50x, then integrate an AI service safely.”
Push on:
- tenancy/RBAC
- audit/compliance/logging redaction
- reliability patterns
- rollout and rollback
- SLOs and incident response
- cost controls

Round 3: LLD (35 mins)
Design FastAPI service:
- /agent/run SSE streaming
- retries/timeouts/circuit breaker
- idempotency
- structured logs + correlation IDs
- test plan

Final Deliverables:
1) scorecard (coding/design/LLD/behavioral)
2) top 10 “must-remember” bullets
3) 1-page cheat sheet for DSA patterns
4) 1-page cheat sheet for system design template
5) 1-page cheat sheet for LLD/FastAPI reliability patterns.
```

---

[1]: https://leetcode.com/discuss/post/7359766/jpmorgan-chase-sde-3-java-full-stack-dev-rxak/?utm_source=chatgpt.com "JPMorgan Chase SDE-3 Java Full stack developer ..."
