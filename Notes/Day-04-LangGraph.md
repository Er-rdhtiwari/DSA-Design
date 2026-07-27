# Day 4 — LangGraph

## 1. Core idea in simple words

**LangGraph** is a framework for building stateful AI workflows as a graph. A **graph** is a set of steps and the allowed paths between them.

Instead of hiding the application inside one long prompt or a loose agent loop, the team can draw its behavior:

`start → retrieve → validate → decide → use tool or ask human → respond`

The graph holds explicit **state**, routes to named steps, saves progress, and controls retries and stopping. This is useful when an AI application must be reliable, inspectable, recoverable, and able to pause and resume.

LangGraph does not make an agent safe automatically. It gives engineers a place to design and enforce safety, control, and recovery.

## 2. Foundational concepts

### What problem LangGraph solves

Simple LLM applications are often linear:

`prompt → model → output`

A **chain** can connect several linear components. Real production workflows may also need to:

- choose one of several paths;
- call tools repeatedly;
- validate the result and retry;
- wait hours for human approval;
- resume after a worker restart;
- preserve state across those steps;
- stop when time, cost, or attempt limits are reached;
- recover one failed step without repeating completed effects.

These requirements need an orchestration model, not merely a longer chain.

### LangGraph versus LangChain

- **LangChain** provides application components such as prompts, model calls, retrievers, tools, and simple compositions.
- **LangGraph** organizes components into a stateful control-flow graph with routes, cycles, checkpoints, and pause/resume behavior.

LangChain components can run inside LangGraph nodes. A useful separation is: components do work; the graph decides which work happens next and records its progress.

### Deterministic and agentic workflows

A **deterministic workflow** follows rules written by engineers. For the same validated state, it chooses the same next path. Example: “If the caller lacks `content.review`, reject.”

An **agentic workflow** lets an LLM choose a next step or tool based on the situation. Example: choose whether campaign evidence, regional policy evidence, or a clarification is needed next.

The two can be mixed. Deterministic code should own authorization, limits, approvals, and fixed business rules. The model can handle ambiguous interpretation within those boundaries.

### When LangGraph is a good fit

Use it when the system needs several of these:

- conditional branches or cycles;
- explicit shared state;
- bounded tool-using agent loops;
- checkpoints and durable resume;
- human approval;
- step-level retries and fallbacks;
- streaming progress;
- detailed multi-step traces.

It may not be a good fit for one model call, a short linear request, or a fixed flow that ordinary backend code expresses more simply. A graph adds state schema, checkpoint storage, versioning, tests, and operational work.

## 3. LangGraph building blocks

### State

**State** is the data carried through the workflow. For the campaign example it might contain:

```text
run_id
tenant_id
user_id
permissions
campaign_id
region
question
retrieved_source_ids
decision
tool_attempts
approval_status
error
deadline
```

The state schema defines the name, type, and meaning of each field. It should distinguish immutable request facts from fields that steps may update. Do not place secrets or unlimited chat history in state.

### Nodes

A **node** is one named unit of work. Examples:

- authenticate request;
- retrieve campaign;
- retrieve rights policy;
- call a model;
- validate a structured result;
- create an approval;
- build a response.

Small nodes are easier to retry, test, observe, and reason about. A node should have clear inputs, state updates, side effects, errors, and timeout behavior.

### Edges and control flow

An **edge** connects one node to another. **Control flow** means the rules that decide the order of node execution.

A normal edge always moves to a known next node. A **conditional route** inspects state and selects a path, such as:

```text
if authorization_failed → reject
if evidence_missing → ask_for_review
if evidence_conflicts → human_approval
otherwise → synthesize_answer
```

Routing rules should be explicit and testable. When an LLM proposes a route, deterministic code should validate that the route is allowed.

### Tool execution steps

A tool node executes a bounded capability: search a database, read an API, or create an approval ticket. Separate read tools from write tools. Validate arguments and permissions immediately before execution.

Action tools need:

- idempotency, so a retry does not duplicate an effect;
- a timeout and bounded retry policy;
- audit records;
- a normalized result schema;
- safe handling of partial or uncertain outcomes.

### Checkpointing

A **checkpoint** is a saved snapshot of workflow progress and state. If a process stops after retrieval, it can resume from that checkpoint instead of starting over.

Checkpoint records need a run ID, graph version, state version, completed-step information, tenant-safe access, retention, encryption, and cleanup rules.

### Durable execution

**Durable execution** means progress survives process restarts or long waits. It is more than saving chat history. The system must know which step completed, which effects occurred, and which step is safe to run next.

Exactly-once execution across network systems is difficult. A practical design combines at-least-once delivery with idempotent action keys and records of effects.

### Human-in-the-loop

**Human-in-the-loop** means the workflow pauses for a person to review, edit, approve, or reject. The checkpoint stores the pause. A callback or user action later resumes the same run.

Human review is valuable for high-impact, ambiguous, or legally sensitive decisions. It should not be a blanket fallback for every request; that creates cost and bottlenecks.

### Streaming

**Streaming** sends progress before the entire workflow finishes. The service might emit:

- “retrieval complete”;
- answer tokens as they are generated;
- “waiting for approval”;
- tool or step status.

Streaming improves user experience but creates ordering, reconnect, duplicate-event, authorization, and partial-output concerns. Every event should include run and sequence identifiers, and sensitive internal reasoning should not be streamed.

### Retry and recovery

A **retry** repeats a failed operation. It helps only for transient failures such as a timeout. Invalid input, denied access, or a permanent business error should not be retried.

**Recovery** decides what happens after failure: retry, use a fallback, compensate for an earlier effect, ask a human, return partial read-only information, or stop safely.

Use bounded retries, exponential backoff with jitter, an end-to-end deadline, and a clear terminal error state.

### Guardrails

A **guardrail** is a rule that limits behavior. Examples include allowed tools, input schemas, permission checks, maximum steps, token and cost budgets, content rules, and required approvals.

Guardrails should exist at the actual execution boundary. A prompt saying “do not call unsafe tools” is not an authorization system.

## 4. End-to-end workflow example

Design a workflow called `campaign_content_review`.

### State transitions

1. **`validate_request`**
   - Confirms input schema.
   - Writes normalized campaign ID and region.
   - Invalid input routes to `reject_request`.

2. **`authorize`**
   - Checks tenant and user permissions in deterministic code.
   - Denied access routes to `reject_request`.

3. **`retrieve_evidence`**
   - Runs authorized campaign and policy retrieval, possibly in parallel.
   - Stores source IDs, not unrestricted raw data, in durable state where practical.

4. **`check_evidence`**
   - Validates freshness, required source types, versions, and conflicts.
   - Sufficient evidence routes to `analyze`.
   - Missing evidence routes to `request_human_review`.
   - Temporary retrieval failure routes through a bounded retry policy.

5. **`analyze`**
   - A model interprets the evidence and returns a structured proposed decision.
   - The node stores the proposal and citations.

6. **`validate_decision`**
   - Code validates schema, citation support, allowed decision values, and business rules.
   - A repairable format failure can return once to `analyze`.
   - A policy conflict routes to `request_human_review`.

7. **`request_human_review`**
   - Creates one idempotent approval item.
   - Saves a checkpoint and pauses.

8. **`resume_after_review`**
   - Verifies the callback and reviewer authority.
   - Applies the decision to state and routes to `build_response`.

9. **`build_response`**
   - Creates the user-facing cited answer or safe failure.
   - Marks the run terminal.

### Why explicit workflow design matters

The graph makes important questions visible:

- Which step is allowed to read restricted evidence?
- Which step may change external state?
- What is retried, and how many times?
- What happens when evidence conflicts?
- Where does the workflow wait?
- How does it resume after deployment?
- What is the terminal success, rejection, or failure state?

That visibility is a reliability and governance feature.

## 5. Inter-relation between state, routing, tools, and recovery

These four parts create a control loop:

`state describes now → routing selects next → node/tool changes state → checkpoint records it → recovery handles failure`

### State enables routing

A route can only be correct if state fields have clear meanings. A field such as `approved=true` is unsafe unless it also captures who approved, for what version, at what time, and under which policy.

### Routing bounds autonomy

An agent may propose `search_policy`, `ask_clarification`, or `finish`, but the route validator can reject disallowed or over-budget choices. This creates **controlled autonomy**: the model has freedom inside an engineer-defined state machine.

### Tools create effects

Tool results update state; write tools also change the outside world. Save enough information to tell whether an effect succeeded before retrying. A timeout after sending a request is an uncertain outcome, not proof of failure.

### Checkpoints enable recovery

After a failure, a checkpoint tells the system which successful work can be preserved. Idempotency prevents duplicate approval tickets. A fallback route may return a read-only answer if the write tool is unavailable.

### Planner and executor

In a **planner/executor** design:

- the planner proposes a sequence or next objective;
- the executor runs only allowed tools;
- a validator checks results and limits;
- the graph decides whether to continue, replan, ask a human, or stop.

The plan is a proposal, not authority.

### Agent loops and stopping

An **agent loop** repeats: inspect state, choose tool, execute, observe result, choose again. Every loop needs stopping conditions:

- maximum steps and tool calls;
- time and token budget;
- no-progress or repeated-call detection;
- terminal success criteria;
- an explicit failure or human-review route.

A **tool-using agent** is this kind of loop when the available actions are external tools. The model may select a tool, but the graph and backend still control which tools are visible, validate arguments, authorize execution, and enforce budgets.

A deterministic graph is better when steps are known, compliance needs predictable behavior, latency must be bounded tightly, or actions have high impact. A free-form agent is appropriate only where variable reasoning adds enough value to justify its uncertainty.

## 6. Production-grade challenges

| Challenge | Failure mode | Control |
| --- | --- | --- |
| Unclear state design | Fields conflict or grow without ownership | Typed, versioned, minimal state schema |
| Workflow sprawl | One graph becomes an unreadable application | Small subflows, clear domains, documented routes |
| Infinite loops | Agent repeats tools without progress | Step, time, token, cost, and repetition limits |
| Tool failures | Timeouts, partial effects, bad result shapes | Idempotency, result validation, deadlines, safe retry |
| Hard-to-debug behavior | Route depends on hidden prompts or state | Step traces, route reasons, versioned fixtures |
| Poor recovery | Restart duplicates work or loses progress | Durable checkpoints and recovery tests |
| Cost blowups | Loops multiply model and tool calls | Per-run budgets and usage guards |
| Latency accumulation | Many individually fast steps miss total SLO | End-to-end deadline and critical-path profiling |
| Multi-step observability | Logs cannot reconstruct a run | Correlated run/node/attempt IDs and state-change summaries |
| Human review bottlenecks | Queues grow and decisions arrive too late | Risk-based review, SLAs, workload metrics, escalation |
| Reliability/rollback | New graph version cannot resume old runs | Version-aware routing, migration policy, staged rollout |

Security concerns cross every row: checkpoint access, secret handling, tool credentials, tenant isolation, prompt injection through tool results, and audit retention.

## 7. Optimization strategies

### Strong state and node design

- Make state typed, minimal, versioned, and documented.
- Record source IDs and references instead of duplicating large sensitive payloads.
- Separate immutable identity from mutable workflow fields.
- Give each node one responsibility and an explicit state update contract.
- Keep deterministic rules out of model prompts.

### Better routing and validation

- Define allowed routes as an enum rather than arbitrary text.
- Validate model-proposed routes in code.
- Require evidence and business-rule checks before action.
- Test every branch, terminal state, and forbidden transition.
- Detect no-progress cycles.

### Bounded retries and safe fallbacks

- Retry only classified transient failures.
- Use attempt limits, backoff, jitter, and total deadlines.
- Make action tools idempotent.
- Route permanent or ambiguous failures to a clear terminal or review state.
- Prefer a safe partial or read-only result over an uncontrolled action.

### Selective human review

Use humans for high-risk actions, conflicting evidence, low-confidence policy interpretation, and exceptions. Avoid review for ordinary low-risk requests that deterministic validation can settle. Measure queue time, review rate, overturn rate, and reviewer agreement.

### Better telemetry

For each run, record:

- graph, state-schema, prompt, model, tool, and policy versions;
- node and route sequence with reason codes;
- per-node attempts and latency;
- tokens and cost by model step;
- tool results and effect IDs, with sensitive data protected;
- checkpoint and resume events;
- terminal outcome and human-review outcome.

Monitor p50/p95/p99 duration, completion rate, loop count, failure by node, stuck runs, review backlog, cost per successful run, and quality/evaluation scores.

### Better testing

- Unit-test nodes and route functions.
- Use contract tests for tools.
- Simulate timeouts, duplicate delivery, restart, and partial effects.
- Test pause/resume across graph deployments.
- Run offline evaluations for model decisions and tool choices.
- Replay sanitized production traces against candidate versions.
- Canary new graph versions and retain rollback.

### Cost and latency controls

- Use a model only for ambiguous steps.
- Run independent nodes in parallel.
- Cache safe read results with tenant, permission, and version-aware keys.
- Summarize or reference large state instead of copying it into every prompt.
- Set per-node and per-run budgets.
- Stop early when success or safe failure is already known.

## 8. Easy real-world example

A content manager asks the assistant to review artwork for campaign `CMP-1042`.

The graph:

```text
validate
  → authorize
  → retrieve campaign + rights policy
  → check evidence
      ├─ sufficient → analyze → validate decision → answer
      ├─ missing/conflicting → create review → pause
      │                         → reviewer callback → answer
      └─ temporary failure → bounded retry → fallback or stop
```

This is safer than a free-form agent because:

- access checks cannot be skipped;
- only allowed evidence tools are exposed;
- the review ticket tool can run at most once per idempotency key;
- the graph has a maximum step and cost budget;
- a checkpoint preserves the run during human review;
- every route and effect can be audited.

The model still adds value by interpreting policy wording and selecting relevant evidence. The graph controls when that reasoning is trusted and what it may cause.

## 9. Staff-level interview angle

### A concise interview explanation

> LangGraph is a stateful orchestration layer for AI workflows and agents. I would model work as small nodes connected by explicit deterministic or model-assisted routes over typed state. Checkpoints make progress durable, while bounded retries, idempotent tools, guardrails, and human approval control failures and side effects. I would use it when branching, loops, pause/resume, or recovery justify the operational cost; a short linear request should remain a simple chain or ordinary code.

### How to decide whether orchestration needs it

Ask:

- Does the flow branch or loop?
- Must it survive a restart or long human wait?
- Are there multiple tools or partial external effects?
- Must a failed step resume without repeating earlier work?
- Does audit require a visible state transition history?
- Are per-step retries, fallbacks, and budgets important?

If most answers are no, do not add a graph.

### Durable execution trade-offs

Durability improves recovery and auditability, but adds storage, state migrations, retention, concurrency control, and run-version compatibility. Checkpointing after every tiny step improves recovery resolution but increases storage and write latency. Choose checkpoint boundaries around expensive work and important side effects.

Control also reduces unconstrained flexibility. That is usually a good trade for enterprise actions, but the team should preserve model freedom where interpretation is valuable and risk is bounded.

### Disney-like production fit

Useful workflows include content-rights review, campaign compliance, knowledge-assisted operations, support escalation, and asset approval. These can combine governed retrieval, model interpretation, internal tools, and human decisions while preserving tenant, identity, and audit boundaries.

A Staff AI Engineer should define the state and effect model, graph versioning, SLOs, cost limits, evaluation gates, incident recovery, security controls, and ownership across product, platform, and human operations.

### Fast revision checklist

- State says what is known; nodes do work; edges choose order.
- Conditional routes and loops need explicit limits.
- Components may come from LangChain; LangGraph owns orchestration.
- Checkpointing saves progress; durable execution survives restarts and waits.
- Tool retries require idempotency and uncertain-outcome handling.
- Human review should be risk-based.
- The model may propose; deterministic code authorizes and constrains.
- Use a graph only when workflow complexity earns its operational cost.
