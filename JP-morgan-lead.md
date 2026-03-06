## Day 1 — JD-to-Resume Mapping + Story Bank + Interview Gameplan (Prompt)

```text
You are my interview coach for: “Lead Software Engineer (Python + AI/ML) building an AI-native SDLC Agent Fabric at JPMC”.

Goal for today:
1) Convert the JD into a crystal-clear competency map.
2) Create my behavioral + leadership “story bank”.
3) Create my interview-ready pitch for “Agent Fabric” + my past experience.

Context (JD highlights):
- LLM-driven agents for design, code generation, docs, tests, observability on AWS
- Multi-agent orchestration: LangGraph / AutoGen / A2A SDK / MCP
- Toolchain integrations: Jira, GitHub/Bitbucket, Terraform, monitoring
- Python, FastAPI, Pydantic, RAG, Vector DBs; AWS (EKS, Lambda, S3, Terraform); CI/CD, Docker, Kubernetes
- Leadership + mentoring; (preferred: MLOps, Azure/GCP)

Deliverables (must produce all):
A) JD Decomposition Table:
- Column1: JD requirement
- Column2: What interviewer is testing
- Column3: Evidence I should present (project/metric/decision)
- Column4: Risks/gaps + how I’ll mitigate in interview

B) My 2-minute “Why me for Agent Fabric” pitch:
- Problem → Approach → Architecture → Results → Why I fit → What I’ll build in first 30/60/90 days

C) Story Bank (use STAR format):
- 8 stories total:
  - 2 leadership/mentoring
  - 2 dealing with ambiguity / changing requirements
  - 2 reliability/incident/production bug or outage
  - 1 conflict resolution / stakeholder mgmt
  - 1 cost optimization / performance improvement
For each story include: situation, task, actions, metrics, learnings, and “follow-up questions they might ask”.

D) Interview Loop Plan:
- Based on typical rounds (coding + system design + behavioral), propose how I should allocate practice across the next days.
- Give me a “cheat sheet” of what to say if I don’t know an answer (safe + honest + senior style).

E) Quick Drill:
- Ask me 10 rapid-fire questions (mix: leadership, RAG, agents, AWS, CI/CD), wait for my answers, then grade and improve them.
```

---

## Day 2 — DSA Revision Pack 1 (Arrays/Strings/Hashing/Two Pointers/Sliding Window) (Prompt)

```text
Act as my JPMC coding-round coach. Today is DSA Revision Day 1.

Constraints:
- I may get 2 problems in 60 minutes.
- I must write clean Python with edge cases, explain complexity, and communicate clearly.

Teach + Drill (must include all):
1) Pattern Playbook (short but complete):
- Arrays + prefix/suffix
- Hashing (freq maps, two-sum style)
- Two pointers
- Sliding window (fixed vs variable)
- Sorting + greedy basics
For each pattern: when to use, template pseudocode, common traps.

2) Timed Practice Set (simulate OA):
- Give me 2 problems back-to-back (LeetCode easy/medium mix) with constraints.
- I will answer in chat with code.
- You must review like an interviewer: correctness, time/space, readability, edge cases.

3) “Communication Script”:
- Provide the exact words I should use to start solving:
  - clarifying questions
  - brute force idea
  - optimization idea
  - complexity statement
  - final recap

4) Micro-checklist:
- 10-item checklist I must run before saying “final answer” (nulls, empty arrays, duplicates, overflow, big-O, etc.)

5) Extra: Top 15 tagged-type problems I should practice later (just titles + pattern tag, no solutions).
```

---

## Day 3 — DSA Revision Pack 2 (Stacks/Queues/Linked List/Intervals/Heap + LRU) (Prompt)

```text
You are my interviewer-style coding coach (Python). Today is DSA Revision Day 2.

Focus topics:
- Stack patterns: monotonic stack, valid parentheses, next greater element
- Queue/deque patterns
- Linked list: reverse, cycle, merge, fast/slow pointers
- Intervals: merge, meeting rooms style
- Heap: top-k, streaming median concept
- LRU cache (hashmap + doubly linked list)

Deliverables:
1) “Pattern Cards” for each topic (1 screen each):
- trigger signals (how to recognize)
- core approach
- template code skeleton in Python
- gotchas

2) Timed Mock Round:
- Problem 1: intervals or heap (medium)
- Problem 2: stack or linked list (medium)
I will write code; you review and push for improvements.

3) LRU Mini-Implementation:
- Provide a clean, interview-ready LRU cache implementation in Python (class-based), with explanation of O(1) operations.
- Add 5 test cases (edge-focused).

4) Debugging Drill:
- Give me 5 common bugs in these topics and how to quickly detect them during interview.

5) Behavioral crossover:
- Show how to answer “Why is your solution correct?” in 4–6 crisp bullets (senior engineer style).
```

---

## Day 4 — RAG + Vector DB + Evaluation (Agent Knowledge + Hallucination Control) (Prompt)

```text
You are my GenAI/RAG system interview coach for a Lead role.

Today’s goal:
Build interview-level mastery of RAG design, retrieval quality, grounding, and evaluation—aligned to “RAG-based AI agents with vector DBs”.

Teach in a production mindset (must include all):
1) RAG End-to-End:
- Ingestion pipeline: parsing → chunking → embeddings → index
- Query pipeline: rewrite → retrieve → rerank (concept) → context assembly → generate → citations/grounding

2) Chunking + Embeddings:
- chunk strategies (fixed, heading-based, semantic)
- overlap rationale
- embedding model selection criteria
- metadata filtering (tenant, doc type, time)

3) Vector DB Concepts:
- index types (HNSW/IVF conceptually)
- tradeoffs: latency vs recall vs memory
- hybrid retrieval idea (BM25 + vector) conceptually

4) Hallucination Control:
- prompt grounding patterns
- answer-with-citations behavior
- refusal policy when context is missing
- “don’t know” and retrieval fallback strategies

5) RAG Evaluation & LLMOps:
- offline evaluation: golden set, recall@k, MRR (concept), faithfulness
- online: monitoring drift, query logs, feedback loop
- prompt regression tests and data versioning

6) Mini Design Exercise:
Design: “SDLC Agent Knowledge Base” that answers only from approved engineering docs.
- Provide architecture diagram (ASCII), data flow, schemas for documents/chunks/metadata, and APIs.

7) Interview Q&A:
Ask me 12 questions (mix: concepts + tradeoffs + debugging RAG quality).
Wait for my answers, then correct and improve.
```

---

## Day 5 — Multi-Agent Orchestration + SDLC Agent Fabric Design (LangGraph/AutoGen/A2A/MCP) (Prompt)

```text
You are my Lead-level system designer for “AI-Native SDLC Agent Fabric”.

Today’s goal:
Be able to explain and design a multi-agent platform that orchestrates agents for:
- design review, code generation, docs, test generation, observability
- integrates with Jira/GitHub/Bitbucket/Terraform/monitoring
- deploys on AWS (EKS/Lambda/S3) with CI/CD, security, and reliability.

Deliverables (must include all):
1) Agent Fabric Mental Model:
- agent roles (planner, executor, reviewer, verifier)
- state management, tools, memory (short/long)
- routing, branching, retries, fallbacks, and human-in-the-loop checkpoints

2) Framework Mapping:
Explain how you’d implement the same flow in:
- LangGraph (state graph)
- AutoGen (multi-agent chat)
- A2A/MCP (tool + agent communication concept)
Keep it practical: what code modules you’d create, how messages/state flow, how to test.

3) Core Platform Architecture (system design):
Design “Agent Execution Platform” with:
- API gateway + authn/authz (RBAC, service identities)
- job queue + worker model
- event bus for agent events
- secrets management
- audit logs (prompt + tool calls + outputs)
- data storage for artifacts (S3), metadata DB, vector DB
- observability: metrics, logs, traces, cost tracking

4) Safety & Governance:
- prompt injection defense
- data privacy/PII handling
- tool permissioning (least privilege)
- secure-by-default logging (redaction)
- policy: “only answer from internal KB” + enforcement

5) Integration Flows:
Give sequence diagrams (ASCII) for:
- “Jira ticket → design agent → PR creation → test agent → deploy plan (Terraform) → monitoring checks”
- “PR review agent + policy gates + rollback plan”

6) Interview Drill:
Ask me to explain the architecture in 8 minutes.
Then grill me with 15 follow-up questions (scalability, reliability, security, cost, failure modes).
```

---


[1]: https://leetcode.com/discuss/interview-experience/5438765/JP-Morgan-SE3-Interview-Experience/?utm_source=chatgpt.com "JP Morgan SE3 Interview Experience - Discuss"
[2]: https://www.educative.io/blog/jp-morgan-system-design-interview-questions?utm_source=chatgpt.com "JP Morgan System Design interview questions"
[3]: https://www.glassdoor.co.in/Interview/J-P-Morgan-Machine-Learning-Engineer-Interview-Questions-EI_IE145.0%2C10_KO11%2C36.htm?utm_source=chatgpt.com "J.P. Morgan Machine Learning Engineer Interview Questions"


---

## Day 6 — DSA Pack 3 (Trees/Graphs) + PR Review Drill (Prompt)

```text
You are my JPMC Lead SWE (Python + AI/ML) interview coach.

Today’s focus:
A) Coding round readiness for Trees + Graphs (BFS/DFS/Topo/Union-Find)
B) PR/code review drill (security + correctness + maintainability)
C) Communication style: crisp, senior, production mindset

Part 1 — Pattern Playbook (Trees/Graphs)
1) Trees
- DFS recursion vs iterative stack (when/why)
- BFS level-order using deque
- Binary tree templates: max depth, diameter (concept), path sum (concept)
- Common traps: null children, visited state, recursion depth, mutation bugs

2) Graphs
- Graph representations: adjacency list vs matrix (tradeoffs)
- BFS (shortest path in unweighted) template
- DFS (cycle detection) template
- Topological sort (Kahn’s + DFS) + “when to use”
- Union-Find (DSU) for connectivity + cycle detection (template)
- Shortest path overview: Dijkstra concept (no need to deep code unless asked)

Deliverable: For each pattern, give:
- “signals” to recognize
- template pseudocode
- time/space complexity
- 2 classic pitfalls

Part 2 — Timed Mock (simulate JPMC 60-min coding style)
- Give me 2 problems (medium-ish) back-to-back:
  Problem 1: tree
  Problem 2: graph
I will write Python solutions. Review like interviewer:
- correctness + edge cases
- clean code & naming
- complexity
- ask me to explain approach in 60 seconds

Part 3 — PR Review / Code Review Drill (10 minutes)
Give me a small PR diff (Python service code) that includes 8–12 issues such as:
- hardcoded secrets / credentials
- missing input validation
- bad error handling
- insecure logging (PII)
- poor naming / dead code
- non-idempotent endpoint bug
- concurrency issue (async misuse)
Ask me to review it and list issues + fixes.
Then provide the “ideal reviewer notes” answer.

Part 4 — “How to talk” script
Provide exact lines I should say:
- clarifying questions
- “I’ll start with brute force”
- “here is the optimized approach”
- final recap + complexity

Part 5 — Mini behavioral
Ask me 5 quick questions:
- a time you mentored someone
- a production incident & what you learned
- handling ambiguous requirements
- disagreement with PM/peer
- cost optimization in cloud
Wait for my answers and improve them using STAR.
```

---

## Day 7 — System Design 1: “Agent Execution Platform” (Core) (Prompt)

```text
Act as a JPMC system design interviewer for a Lead Engineer building an AI-native SDLC Agent Fabric.

Design problem (today):
“Design an Agent Execution Platform that runs LLM-driven agents (design/code/docs/tests/observability), supports multi-agent orchestration, integrates tools (Jira/GitHub/Terraform/monitoring), and runs on AWS.”

Rules:
- Must be secure, auditable, reliable, scalable, cost-aware.
- Assume enterprise constraints: RBAC, least privilege, audit logs, data retention, PII redaction.
- Output must be structured like a real system design interview answer.

Deliverables (must include all):

1) Requirements (Functional + Non-Functional)
- Functional: agent run lifecycle, tool calls, artifact storage, human approval gates
- NFRs: latency, throughput, reliability, security, audit/compliance, cost, multi-tenant isolation

2) High-level architecture (ASCII diagram)
Include:
- API Gateway
- AuthN/AuthZ (RBAC/service identity)
- Orchestrator (LangGraph-like state engine concept)
- Job Queue + Workers
- Tool connector layer (Jira/GitHub/Terraform/Observability)
- Data stores: metadata DB, vector DB, object store (S3)
- Secrets store
- Event bus
- Observability pipeline

3) Detailed design
- APIs: start_run, get_status, cancel, approve_step, list_artifacts
- Data model: Run, Step, ToolCall, Artifact, AuditEvent, CostRecord
- State machine: retries, timeouts, fallbacks, “human-in-the-loop” checkpoints
- Idempotency strategy + exactly-once vs at-least-once handling

4) Security + Governance
- prompt injection defense strategy for tool calls
- tool permissioning model (scopes per agent + per run)
- logging redaction policy (prompts may contain secrets/PII)
- audit trails: what is captured, where stored, retention

5) Failure modes & resilience
- LLM timeout, tool failure, partial completion, bad output schema
- retry/backoff strategy
- canary rollout and rollback strategy for agent updates

6) Interview simulation
- Ask me to present the design in 8 minutes.
- Then ask 15 follow-ups (scaling, consistency, cost, security, observability, multi-region, DR).
Wait for my answers and critique like a real interviewer.
```

---

## Day 8 — Python Backend Mastery (FastAPI + Pydantic) + Streaming + Security (Prompt)

```text
You are my Lead Python backend interviewer coach (FastAPI + Pydantic) for an AI agent platform.

Goal:
Be interview-ready on building production APIs for agent runs:
- clean architecture
- validation
- async
- streaming (SSE)
- security
- tests

Deliverables:

1) FastAPI + Pydantic deep revision
Cover with examples:
- request/response models, validators, custom types
- dependency injection
- error handling patterns (HTTPException, custom exception handlers)
- async endpoints + background tasks
- middleware: request IDs, logging, auth, rate limiting concept

2) Streaming responses
Explain and demo:
- SSE streaming for token-by-token output
- what to stream (status updates, partial text, tool events)
- handling disconnects + backpressure
- structured event schema (event_type, run_id, step_id, payload)

3) Security essentials
- Auth: JWT/OAuth2 (concept), service-to-service auth
- RBAC checks per endpoint
- input validation against prompt injection vectors (basic)
- logging redaction strategy (never log secrets)
- secure defaults: timeouts, size limits, rate limits

4) Mini coding exercise (write code)
Ask me to implement:
- POST /runs (start run)
- GET /runs/{id}
- GET /runs/{id}/stream (SSE)
- POST /runs/{id}/approve (human gate)
Provide a clean folder structure suggestion.

5) Testing pack
- pytest unit tests for validators and service layer
- integration test using TestClient
- contract tests for event schema
- load test outline (k6/locust concept)

6) Interview drill
Ask me 12 questions:
- async pitfalls
- pydantic validation costs
- error handling in distributed systems
- streaming + retries
- API versioning and backward compatibility
Wait for my answers and correct them.
```

---

## Day 9 — AWS + Terraform + EKS Deployment Patterns for Agent Fabric (Prompt)

```text
You are my cloud/system interviewer coach for this JD (AWS + Terraform + EKS/Lambda/S3).

Goal today:
Design and explain how I would deploy the Agent Execution Platform on AWS with IaC and production practices.

Deliverables:

1) Deployment architecture (ASCII)
Include:
- EKS for API + workers
- ALB Ingress / load balancing
- S3 for artifacts
- SQS (or Kafka/MSK concept) for job queue
- Secrets Manager / Parameter Store
- CloudWatch + OpenTelemetry collector
- Optional Lambda for lightweight event handlers

2) Terraform plan (modules + state)
- remote state: S3 + DynamoDB locking
- module breakdown: networking, eks, iam/irsa, s3, sqs, observability
- environment strategy: dev/stage/prod, naming, tagging, cost controls
- IAM policy design: least privilege (examples)

3) EKS production basics
- nodegroups vs fargate (tradeoffs)
- autoscaling (HPA/Cluster Autoscaler)
- IRSA for pods
- resource requests/limits, PDBs
- rollout strategy: canary (Argo Rollouts concept) + rollback

4) CI/CD (high level)
- build/push docker images
- deploy helm charts
- promotion strategy + approvals
- secrets handling in pipeline

5) Common failure/debug checklist
- pods crashloop, readiness/liveness
- ALB routing, DNS, certs
- IAM/IRSA permission issues
- queue backlog, worker scaling
- cost spikes

6) Interview drill
Ask me 10 design questions typical for scalable systems (LB, caching, DB, messaging, microservices), and I must answer with AWS-native choices.
Then critique and improve my answers.
(Note: JPMC-style system design often expects scalability + messaging + caching + DB optimization topics.) 
```

---

## Day 10 — Observability + LLMOps (Logging/Versioning/Regression/Evals) + Incident Drill (Prompt)

```text
You are my LLMOps + Observability interview coach for an SDLC Agent Fabric.

Goal:
Be able to explain production-grade monitoring, logging, prompt/version governance, evaluation, and canary/rollback.

Deliverables (must include all):

1) Observability 101 for Agent Systems
- Logs: structured logs, correlation IDs, redaction
- Metrics: latency, throughput, queue depth, error rate, token usage, $ cost
- Traces: OpenTelemetry spans across API → orchestrator → tool calls → vector DB → LLM
- Dashboards: SLOs/SLIs + alert rules

2) Agent/Prompt governance
- versioning: prompts, tools, policies, model version
- configuration management
- change control: canary runs, A/B testing, rollback triggers

3) LLM-specific monitoring (LLMOps)
- prompt & response logging policy (what to store vs mask)
- hallucination signals + guardrail metrics
- tool-call failure tracking
- evaluation harness:
  - golden dataset
  - offline metrics (faithfulness concept, retrieval recall@k concept)
  - regression tests for prompts and tool schemas

4) Reliability strategies
- retries with backoff (LLM + tools)
- circuit breakers
- timeouts + budgets per step
- fallback routes (smaller model / cached answer / human escalation)

5) Incident simulation (postmortem)
Give me a scenario:
“After a prompt update, agent starts creating bad Terraform PRs and costs spike.”
Ask me to:
- detect via metrics
- mitigate (feature flag, rollback)
- debug (logs/traces)
- prevent recurrence (tests/evals)
Then provide the “ideal” senior incident response and a postmortem template.

6) Interview Q&A
Ask me 12 questions:
- how to prove agent output quality in production
- how to avoid leaking secrets in prompt logs
- how to measure cost and enforce budgets
- how to do canary for prompts/tools
Wait for my answers and refine them.
```

---

[1]: https://leetcode.com/discuss/interview-experience/5438765/JP-Morgan-SE3-Interview-Experience/?utm_source=chatgpt.com "JP Morgan SE3 Interview Experience - Discuss"

---
## Day 11 — DSA Pack 4 (Recursion/Backtracking + DP) (Prompt)

```text
You are my JPMC coding-round coach (Python). Today is DSA Revision Day 4.

Goal:
Be comfortable with recursion/backtracking + dynamic programming patterns that often show up in medium problems.

Part 1 — Backtracking Playbook
Cover with simple templates + when to use:
- subsets / permutations / combinations
- “choose / explore / un-choose” pattern
- pruning rules (early stopping)
- handling duplicates (sort + skip pattern)
- time complexity intuition (why it explodes)

Deliver:
- 1 Python backtracking template (generic)
- 5 “common pitfalls” checklist (global state, copying lists, duplicates, recursion depth)

Part 2 — DP Playbook (Interview-ready)
Explain these DP types with 1–2 examples each:
- 1D DP (climbing stairs style)
- 2D DP (grid paths style)
- DP on strings (LCS/edit-distance concept)
- DP optimization (space reduction)
- memoization vs tabulation (when/why)

Deliver:
- 1 memoization template + 1 tabulation template
- how to pick state, transition, base cases (a step-by-step method)

Part 3 — Timed Mock (60 min simulation)
Give me 2 problems back-to-back:
- Problem 1: Backtracking (medium)
- Problem 2: DP (medium)
I will code in Python.
You must review like an interviewer:
- correctness + edge cases
- clarity + naming
- complexity
- ask me to explain approach in 60 seconds

Part 4 — “Explain correctness” script
Give me a short script (4–6 bullets) to justify:
- why recursion enumerates all valid solutions
- why DP state/transition is correct

Part 5 — Rapid Q&A
Ask me 10 quick questions (patterns + complexity + typical traps), wait for answers, then correct.
```

---

## Day 12 — System Design 2: “Jira Ticket → PR → Tests → Terraform Plan” SDLC Agent Workflow (Prompt)

```text
Act as a system design interviewer for an AI-native SDLC Agent Fabric (Lead role).

Design problem:
“Design an end-to-end SDLC automation workflow where a Jira ticket triggers agentic steps to produce:
- design notes
- code changes + PR
- documentation updates
- test generation
- Terraform plan / deployment proposal
- observability checks
All with human approvals, audit logs, and strong security.”

Deliverables (must include all):

1) Requirements
- Functional: ticket intake, context gathering, PR creation, test pipeline, deploy plan, approval gates
- Non-functional: security/compliance, auditability, correctness, rollback, multi-tenant/team isolation, cost controls

2) Workflow as a state machine
Provide:
- states (e.g., Intake → Context → Plan → Implement → Review → Test → Terraform Plan → Approve → Merge → Monitor)
- transitions + failure paths
- retry/backoff rules
- “human-in-the-loop” points and why

3) Integration design
For each tool (Jira, GitHub/Bitbucket, CI/CD, Terraform, Monitoring):
- what APIs/events are used
- auth method (service identity) and permission scope
- rate limits + idempotency approach
- audit events produced

4) PR Quality & Policy Gates
Define automated checks:
- lint + type check + unit tests
- secret scanning
- policy checks (e.g., only allowed Terraform modules)
- approval rules (2-person review, security review on sensitive changes)
Explain how agents interact with these checks.

5) Data model + logging
Define objects:
- TicketContext, Run, Step, ToolCall, Artifact, Approval, PolicyDecision, AuditEvent
Include a redaction strategy for logs (prompts may include secrets/PII).

6) Architecture diagram (ASCII)
Include:
- API layer
- Orchestrator
- Queue/workers
- Connectors
- Data stores (S3/artifacts, metadata DB, vector DB)
- Observability pipeline
- Secrets manager

7) Interview simulation
- Ask me to present the workflow in 8 minutes.
- Then ask 15 follow-ups (security, rollback, failure modes, cost, abuse prevention, scale).
Wait for my answers and critique like a real interviewer.
```

---

## Day 13 — Python Concurrency + Tool Runner Design (Async, Timeouts, Retries, Rate Limits) (Prompt)

```text
You are my Lead Python interviewer coach. Today is about building reliable “tool execution” for agents.

Goal:
Be able to design and implement (in Python) a robust tool runner that calls external systems (Jira/GitHub/Terraform/Monitoring) safely.

Part 1 — Concepts (explain simply but precisely)
- async vs threads vs processes (when to use)
- GIL impact (what it means for CPU vs IO)
- asyncio pitfalls (blocking calls, gather, cancellation)
- timeouts and cancellation correctness
- retry patterns: exponential backoff + jitter + max attempts
- circuit breaker concept
- rate limiting and concurrency limits (semaphores)
- idempotency keys for external calls

Part 2 — Mini implementation task (write code)
Ask me to implement a small Python module with:
- ToolCall dataclass (tool_name, payload, idempotency_key, timeout_s)
- ToolRunner that supports:
  - max_concurrency (semaphore)
  - per-tool rate limit (simple token bucket or leaky bucket concept)
  - retries with backoff
  - structured result (success/failure, error_type, latency_ms)
- A fake tool adapter (simulate GitHub/Jira calls with random failures)

I will write code; you review and improve it.

Part 3 — Observability hooks
- add correlation IDs
- log redaction rules
- metrics to emit (tool_latency, tool_errors, retry_count, queue_depth)

Part 4 — Interview questions (12)
Ask me 12 questions around:
- async cancellation
- avoiding thundering herd retries
- safe logging
- handling partial failures in workflows
- designing for idempotency
Wait for my answers and correct them.

Part 5 — Senior communication
Give me a short “how to explain concurrency design” script (30–60 seconds).
```

---

## Day 14 — LLM Integration + Prompt/Context Engineering for SDLC Agents (Prompt)

```text
You are my GenAI/LLM integration interviewer coach for a Lead role.

Goal:
Master how to build LLM-driven SDLC agents with strong grounding, tool calling, and output quality.

Deliverables (must include all):

1) LLM Integration Patterns
- API-based vs self-hosted (when each is chosen)
- function calling / tool calling (JSON schema, validation)
- structured outputs: Pydantic models + strict parsing
- token budgeting and context window strategy

2) Prompt & Context Engineering (practical)
Teach using SDLC scenarios:
- “Generate PR description + changelog”
- “Create unit tests”
- “Explain Terraform plan risks”
For each:
- system prompt + developer prompt + user prompt pattern
- how to inject policies (“don’t leak secrets”, “only use provided context”)
- anti-hallucination techniques (cite sources, say ‘unknown’ if missing)

3) Guardrails & Safety
- prompt injection examples relevant to tool use
- tool permissioning: allowlist tools + scopes
- output validators: schema validation + policy checks
- fallback strategy: smaller model / retrieval / human approval

4) Evaluation (Rubric + ROI) — keep it interview-ready
Explain:
- what “rubric-based eval” means (scoring criteria)
- how to create a golden dataset for SDLC tasks
- online feedback loop (thumbs up/down, PR acceptance rate)
- ROI calculation examples: time saved, defect reduction, cost per run
Include 2 numeric examples.

5) Hands-on exercise
Ask me to design prompts + schemas for:
- “PR Review Agent” (find issues, propose fixes, assign severity)
- “Test Agent” (generate tests + explain coverage)
You should then critique my prompts and improve them.

6) Interview Q&A
Ask me 15 questions mixing:
- tradeoffs (prompting vs fine-tuning)
- tool calling reliability
- cost/latency control
- preventing unsafe actions
Wait for my answers and refine.
```

---

## Day 15 — Full “Superday” Simulation (Coding + System Design + Behavioral + PR Review) (Prompt)

```text
You are conducting a full JPMC-style interview day for a Lead Python + AI/ML Engineer building an SDLC Agent Fabric.

Rules:
- Keep strict timing.
- Evaluate like a real panel: correctness, clarity, tradeoffs, leadership, security mindset.
- At the end, give a scorecard + top fixes.

Round 1 (60 min) — Coding
- Give me 2 problems:
  - Problem A: arrays/strings or graphs (medium)
  - Problem B: DP or trees (medium)
I will code in Python.
You must:
- interrupt like interviewer if I go off-track
- push for edge cases
- ask for complexity
- ask for quick tests

Round 2 (45–60 min) — System Design
Design: “Agent Execution Platform + Jira→PR workflow”
I will present:
- requirements
- architecture
- data model
- security/audit
You must ask 12 follow-ups:
- scale, reliability, idempotency, DR
- prompt injection + tool permissioning
- cost control and observability
- rollout strategy for prompts/tools

Round 3 (30 min) — PR Review
Give me a PR diff with:
- FastAPI endpoint + Pydantic model changes
- logging and auth middleware
- a bug + a security issue + a performance issue
I will review it.
Then provide ideal review comments.

Round 4 (30 min) — Behavioral / Leadership
Ask me 10 questions:
- mentoring/junior guidance
- incident handling + postmortem culture
- handling ambiguity with PM/stakeholders
- disagree and commit
- delivering under deadlines without cutting corners
After my answers, rewrite my best 3 answers into “final interview-ready” versions.

Final output:
- Scorecard (Coding / Design / PR Review / Behavioral)
- Top 10 improvements (actionable)
- 7-day targeted practice plan based on my weaknesses
```

---

## Day 16 — Security, Governance & Threat Modeling for SDLC Agents (Prompt)

```text
You are my security-first interview coach for a Lead Python + AI Agent platform role (JPMC context).

Today’s goal:
Be able to design and defend a secure, compliant “SDLC Agent Fabric” that uses tools (Jira/GitHub/Terraform/monitoring) and LLMs—without leaking data or executing unsafe actions.

Deliverables (must include all):

1) Threat Model (STRIDE style, practical)
- List assets: source code, secrets, Jira tickets, PRs, Terraform state, logs, embeddings, artifacts (S3), model prompts/responses
- List trust boundaries: API gateway, orchestrator, tool connectors, workers, vector DB, external SaaS APIs
- Identify threats + mitigations for each:
  - prompt injection → tool misuse
  - data exfiltration (logs, prompts, artifacts)
  - privilege escalation (over-broad IAM, tool scopes)
  - supply chain risks (dependencies, container images)
  - impersonation (service identities, tokens)
  - replay attacks / duplicate requests
  - model poisoning / retrieval poisoning

2) AuthN/AuthZ Design
- Human auth: SSO/OIDC (concept)
- Service-to-service auth: mTLS/JWT (concept)
- RBAC model: roles (dev, lead, reviewer, ops, security)
- Fine-grained tool permissions:
  - per-agent tool allowlist
  - per-run scope
  - policy gates before high-risk tools (Terraform apply, repo write)

3) Secrets & Data Handling
- Where secrets live (Secrets Manager/Parameter Store)
- Rotation, access patterns (IRSA), least privilege
- Data classification: public/internal/confidential/regulated
- Logging policy: what to store, what to redact, retention rules
- “Never log”: tokens, keys, raw customer data, credentials

4) Guardrails for Tool Calling
- Input validation: schema + allowlists
- Output validation: strict Pydantic parse + policy checks
- Human-in-the-loop checkpoints for destructive actions
- Dry-run-only mode for Terraform + approvals

5) Security Controls Checklist (interview-ready)
- Network: VPC, private subnets, egress control, security groups
- K8s: pod security, network policies, image scanning
- Audit: immutable audit log, traceability across steps
- Compliance: retention, access reviews, incident response

6) Scenario Drill (answer like a senior)
Scenario: “Agent was tricked by a Jira comment to exfiltrate a secret via PR description.”
Ask me to respond with:
- detection signals (logs/alerts)
- immediate containment steps
- root cause analysis steps
- long-term fixes (policy, tests, tool scopes)
Then provide the ideal answer and a short postmortem template.

7) Interview Q&A (15)
Ask me 15 questions focused on:
- prompt injection defenses
- least privilege for tools/IAM
- safe logging and PII
- secure SDLC + supply chain
Wait for my answers and improve them.
```

---

## Day 17 — CI/CD + GitOps + Terraform Policy Gates for Agent-Generated Code (Prompt)

```text
You are my DevOps/MLOps interview coach for building and shipping an SDLC Agent platform.

Today’s goal:
Explain a production-grade CI/CD strategy where agents create PRs, tests run, Terraform plans are validated, and releases are safe (canary + rollback).

Deliverables (must include all):

1) End-to-End Pipeline Design (ASCII)
From: “Jira → agent run → PR created”
To: “merge → deploy → monitor”
Include stages:
- pre-commit checks (lint, type check)
- unit/integration tests
- secret scanning
- SAST/dependency scanning
- container build + SBOM
- Terraform fmt/validate/plan
- policy-as-code gate (OPA/Conftest concept)
- manual approval for high-risk changes
- deploy (canary) + rollback conditions

2) Branching + Environment Strategy
- dev/stage/prod promotion
- versioning (service version + prompt/tool version)
- feature flags for agent behaviors
- artifact repository strategy (Docker images, Helm charts)

3) Terraform Governance
- module allowlist
- remote state handling
- plan review workflow (human + automated checks)
- drift detection
- “no apply by default” rule for agents
- break-glass procedure (how to safely do emergencies)

4) Testing Strategy for Agent Changes
- prompt regression tests (golden inputs → expected outputs)
- schema contract tests for tool calls
- end-to-end workflow tests (mock Jira/GitHub/Terraform)
- canary runs for prompt/tool updates

5) Observability in CI/CD
- build metrics (duration, failure rate)
- deploy metrics (success rate, rollback rate)
- quality gates (PR acceptance, defects)

6) Exercise
Ask me to propose:
- a Jenkins/GitHub Actions style pipeline (high-level YAML steps)
- a policy gate rule example (pseudo OPA)
Then critique and provide improved “ideal” versions.

7) Interview Q&A (12)
Ask me 12 CI/CD questions focused on:
- safe automation, approvals
- secrets in pipelines
- canary + rollback
- GitOps vs push-based deploy
Wait for my answers and refine.
```

---

## Day 18 — Performance, Latency & Cost Optimization (LLM Inference + RAG + Scaling) (Prompt)

```text
You are my performance/cost interview coach for an LLM-driven multi-agent platform.

Today’s goal:
Be able to optimize latency/throughput/cost for:
- agent orchestration
- LLM inference
- retrieval (vector DB)
- tool calls
…and explain tradeoffs clearly.

Deliverables (must include all):

1) Latency Breakdown (where time goes)
- API overhead
- orchestration decisions
- retrieval + reranking (concept)
- tool calls (Jira/GitHub/Terraform)
- LLM generation (tokens)
Create a simple “latency budget” table and how to measure each part.

2) Inference Optimization Concepts (practical)
- batching: when it helps, when it hurts
- caching: prompt cache + response cache (key design + invalidation)
- streaming: SSE vs WebSocket; why streaming improves perceived latency
- context trimming + token budgeting
- model routing: small vs large model based on task
- fallback strategies when model is slow/unavailable
- quantization concept (4-bit/8-bit) and tradeoffs (quality vs speed)

3) RAG Performance Optimization
- choosing K (top-k), chunk size tradeoffs
- metadata filtering to reduce search space
- hybrid retrieval concept
- indexing choices (HNSW/IVF conceptually)
- warm caches and embedding reuse

4) Platform Scaling Strategy
- queue-based workers + autoscaling (queue depth, CPU, latency)
- backpressure + rate limits per tenant
- concurrency limits per tool / per agent
- circuit breakers for flaky tools
- cost budgets per run (max tool calls, max tokens)

5) Cost Model (interview-ready)
Create an example cost calculation:
- tokens per run × cost/token + infra + vector DB ops
Show how to enforce:
- per-tenant budgets
- alerts on anomalies
- “kill switch” for runaway agent loops

6) Exercise
Give me a scenario:
“Traffic spikes 10×; queue backlog grows; LLM cost doubles.”
Ask me to propose:
- immediate mitigations
- long-term fixes
- which metrics prove success
Then provide the ideal answer.

7) Interview Q&A (15)
Ask me 15 questions around:
- throughput vs latency tradeoffs
- caching correctness
- rate limiting and fairness
- scaling EKS workers
Wait for my answers and refine.
```

---

## Day 19 — Evaluation, Rubrics, Data Pipelines & MLOps for Agent Quality (Prompt)

```text
You are my LLMOps/MLOps interview coach for an SDLC agent platform.

Today’s goal:
Be able to prove “agent output quality” with evaluation pipelines, monitoring, and continuous improvement—without overfitting or leaking sensitive data.

Deliverables (must include all):

1) Define “Quality” for SDLC Agents
Create a rubric for each agent:
- Code Gen Agent: correctness, compile/test pass rate, security issues, style
- PR Review Agent: precision of findings, severity correctness, false positives
- Test Agent: coverage gain, flaky tests, relevance
- Terraform Risk Agent: correctness of risk flags, policy compliance
For each rubric: define 5–8 scoring criteria with 0–2 or 0–5 scale.

2) Offline Evaluation Pipeline
- build a “golden set” from past Jira tickets/PRs (with sanitization)
- dataset versioning (DVC-like concept), splits
- evaluation runner that:
  - runs agent prompts/tools in mocked mode
  - scores outputs using rubric
  - tracks regressions per prompt/tool/model version

3) Online Monitoring & Feedback Loop
- capture signals:
  - PR acceptance rate
  - time-to-merge
  - number of review comments reopened
  - incident rate linked to agent-generated changes
  - user feedback (thumbs up/down)
- detect drift and anomalies
- human review sampling strategy

4) CI/CD for Prompts/Tools (LLMOps)
- prompt versioning and rollout
- canary runs + A/B
- rollback triggers based on eval metrics
- governance: approvals and audit trails

5) Data Privacy & Compliance
- PII removal/redaction strategy
- safe storage of prompts/responses (what to store vs mask)
- retention policy + access controls

6) Exercise
Ask me to:
- design a minimal “Eval Harness” architecture (ASCII)
- propose 10 golden test cases for “PR Review Agent”
Then critique and provide an improved version.

7) Interview Q&A (12)
Ask me 12 questions on:
- rubric-based eval
- offline vs online metrics
- preventing gaming/overfitting
- safe logging and privacy
Wait for my answers and refine.
```

---

## Day 20 — Final Revision: Role Pitch, 30/60/90 Plan, and Top Interview Questions (Prompt)

```text
You are my final interview coach for JPMC Lead Software Engineer (Python + AI Agent Fabric).

Today’s goal:
Polish everything into interview-ready answers and strategy.

Deliverables (must include all):

1) My “Role Pitch” (2 minutes)
Write a final pitch tailored to:
- AI-native SDLC agent fabric
- multi-agent orchestration (LangGraph/AutoGen/A2A/MCP)
- integrations (Jira/GitHub/Terraform/Monitoring)
- AWS deployment (EKS/Lambda/S3/Terraform)
Make it: Problem → My approach → Results → Why me → What I’ll do first.

2) 30/60/90 Day Plan
Provide a concrete plan:
- first 30: discovery, baseline metrics, guardrails, MVP workflow
- 60: reliability + observability, eval harness, policy gates
- 90: scale, multi-tenant, cost controls, broader tool integrations
Include measurable KPIs.

3) “Design Story” One-Pager
Summarize my best system design narrative:
- architecture diagram (ASCII)
- data model highlights
- security model
- failure modes
- cost + observability
This should be something I can rehearse in 6–8 minutes.

4) Top 25 Interview Questions (with strong answer outlines)
Split into:
- Coding (5): patterns and how I’d approach
- System Design (10): scaling, multi-tenant, DR, security, queues, caching
- GenAI/Agents (7): tool calling, RAG, evals, prompt injection, governance
- Leadership (3): mentoring, incidents, stakeholder mgmt
For each question: provide a bullet outline of an excellent senior answer.

5) Mock Behavioral “Story Polish”
Pick my best 5 STAR stories and rewrite them:
- crisp, metric-driven
- leadership emphasis
- includes conflict handling and tradeoffs
Also provide 5 “follow-up traps” and best responses.

6) Final Checklist (Interview Day)
- what to do before interview
- how to manage time in coding round
- how to structure system design answer
- questions to ask interviewer (team, scope, success metrics, risks)

7) Mini Mock (fast)
Ask me:
- 1 coding question (medium)
- 1 system design question (10 minutes)
- 3 behavioral questions
Wait for my responses, then grade and provide final improvements.
```

---

Below is an **industry-grade Day 21 “POC Codex Prompt”** you can copy-paste into Codex / any code-gen LLM.

This PoC uses the real Hugging Face dataset **`pacovaldez/stackoverflow-questions`** (fields: `title`, `body`, `label`). ([Hugging Face][1])

```text
You are a Senior AI Engineer building a production-style PoC aligned to this JD:
“Lead Software Engineer (Python + AI/ML) building an AI-Native SDLC Agent Fabric using multi-agent orchestration (LangGraph/AutoGen concepts), MCP-style tool contracts, RAG + vector DB, FastAPI/Pydantic, observability, CI/CD discipline.”

# 🚀 PoC Name
“Ticket2PR Agent Fabric (Mini)”

# 🎯 Objective (what the PoC must do)
Build a small but realistic “SDLC agent fabric” service that:
1) Ingests a REAL Hugging Face dataset into a vector index for retrieval (RAG):
   - dataset: pacovaldez/stackoverflow-questions
   - fields: title (string), body (string), label (int)
2) Exposes a FastAPI API where a user submits a “ticket” (bug/how-to request).
3) Runs a LangGraph-based multi-agent workflow to produce SDLC artifacts:
   - Triage Agent: classify ticket type + severity + risk
   - Retrieval Agent: retrieve top-k similar StackOverflow questions (RAG)
   - Solution Agent: propose fix/answer grounded in retrieved contexts (no hallucination)
   - Test Plan Agent: generate a concrete test plan (and optional pytest snippets)
   - PR Draft Agent: generate PR title/description + checklist + rollout/rollback notes
   - Policy/Verifier Agent: validate JSON outputs, enforce rules, and mark “NEED_HUMAN_APPROVAL” if risky
4) Implements “MCP-inspired” tool contracts:
   - Define tools with JSON schema (name, description, input_schema, output_schema)
   - Provide a ToolRunner that can call local tools safely (timeouts, retries, redaction)
   - Tools to implement (local, no external credentials needed):
     - search_kb(query) -> retrieves chunks from vector store
     - create_pr_draft(ticket, solution, tests) -> returns PR markdown
     - run_policy_checks(artifact) -> returns pass/fail + reasons
     - (optional) run_unit_tests() -> simulated tool that returns a dummy report
5) Provides observability:
   - structured logs with request_id/run_id/step_id
   - basic metrics endpoints (/metrics in Prometheus text format OR simple JSON)
   - tracing-friendly structure (OpenTelemetry optional but nice)
6) Includes an evaluation harness:
   - small golden set (10–20 tickets) stored in repo
   - rubric scoring (helpfulness, grounding, structure, policy compliance)
   - script to run eval and produce a JSON report
7) Must be runnable end-to-end locally with no code edits.

# ✅ Hard Requirements (Do NOT skip)
- Python 3.11+
- FastAPI + Pydantic v2
- LangGraph used for orchestration (real code)
- RAG vector store:
  - Default: FAISS (local) OR Chroma (local) — choose ONE and implement well
  - Optional: Qdrant via docker-compose (bonus)
- Use Hugging Face `datasets` library to load the dataset.
- Ingestion must support sampling (e.g., first N rows) to keep PoC fast.
- All outputs from agents must be structured JSON validated by Pydantic models.
- Add safety rules:
  - “Answer must cite retrieved snippets (at least 2) OR say NOT_ENOUGH_CONTEXT”
  - “Never output secrets”
  - “If ticket indicates destructive actions, mark NEED_HUMAN_APPROVAL”
- Provide clean repo structure, docs, runbook, and tests.

# 📦 Repo Structure (must generate exactly this or better)
ticket2pr-agent-fabric/
  README.md
  pyproject.toml
  .env.example
  Makefile
  docker-compose.yml               # optional but recommended (qdrant)
  Dockerfile                       # multi-stage build
  docs/
    architecture.md
    runbook.md
    threat_model.md
    api.md
    eval.md
  src/
    app/
      main.py                       # FastAPI entrypoint
      api/
        routes.py
        schemas.py                  # Pydantic request/response models
      core/
        config.py                   # env config, typed
        logging.py                  # structured logging + redaction
        ids.py                      # request_id/run_id helpers
      rag/
        ingest.py                   # HF dataset -> documents -> embeddings -> vector store
        store.py                    # vector store wrapper
        retriever.py
      agents/
        graph.py                    # LangGraph StateGraph definition
        state.py                    # State model (Pydantic)
        prompts.py                  # prompts in one place
        nodes/
          triage.py
          retrieve.py
          solve.py
          test_plan.py
          pr_draft.py
          verify.py
      tools/
        registry.py                 # MCP-style tool defs (schemas)
        runner.py                   # timeouts, retries, concurrency limits
        local_tools.py              # actual implementations
      eval/
        golden_set.jsonl
        rubric.py
        run_eval.py
  tests/
    test_api.py
    test_rag.py
    test_policy.py
    test_graph.py

# 🔧 Configuration (env vars)
Provide .env.example with:
- APP_ENV=local
- LOG_LEVEL=INFO
- HF_DATASET=pacovaldez/stackoverflow-questions
- HF_SPLIT=train
- HF_SAMPLE_SIZE=2000
- VECTOR_STORE=faiss
- EMBEDDINGS_PROVIDER=openai|local
- OPENAI_API_KEY=... (optional)
- LOCAL_EMBEDDINGS_MODEL=sentence-transformers/all-MiniLM-L6-v2 (or similar)
- LLM_PROVIDER=openai|ollama
- OLLAMA_BASE_URL=http://localhost:11434
- OLLAMA_MODEL=llama3
- TOP_K=5

# 🧠 Model strategy (must implement fallback)
- If OPENAI_API_KEY is set and LLM_PROVIDER=openai, use OpenAI chat model.
- Else use Ollama chat model (local).
- For embeddings: prefer local sentence-transformers by default to avoid paid APIs.
- Keep code provider-agnostic via small adapters.

# 🧩 API Contract (must implement)
1) POST /v1/runs
Request:
{
  "ticket_id": "TCK-123",
  "title": "FastAPI request hangs intermittently",
  "description": "Requests time out under load; suspect async issue...",
  "constraints": {"must_not": ["restart database"], "env":"dev"},
  "risk_level": "low|medium|high"   # optional input
}
Response (immediate):
{
  "run_id": "...",
  "status": "queued|running|completed|needs_approval|failed"
}

2) GET /v1/runs/{run_id}
Returns status + artifacts:
{
  "run_id": "...",
  "status": "...",
  "artifacts": {
     "triage": {...},
     "retrieval": {"citations":[...], "snippets":[...]},
     "solution": {...},
     "test_plan": {...},
     "pr_draft_md": "..."
  },
  "policy": {"approved": false, "reasons":[...]}
}

3) GET /healthz

(Optional bonus) GET /metrics

# 🧬 LangGraph Workflow (must implement)
State includes:
- ticket (id/title/description/constraints)
- triage_result
- retrieved_contexts (top-k docs + metadata)
- solution
- test_plan
- pr_draft
- policy_result
- status + errors
Nodes:
- triage_node -> retrieve_node -> solve_node -> test_plan_node -> pr_draft_node -> verify_node
Edges:
- verify_node can route to “NEEDS_APPROVAL” if policy fails or risk high.
Add retry behavior for retrieve/solve (bounded).

# 📚 RAG Ingestion details (must implement)
- Load dataset with datasets.load_dataset(HF_DATASET, split=HF_SPLIT)
- Sample HF_SAMPLE_SIZE rows deterministically (seed=42)
- Build Document text as:
  “TITLE: {title}\nBODY: {body}”
- Add metadata:
  { "source":"stackoverflow", "label": label }
- Chunking: simple (e.g., 800–1200 chars + overlap 100) and explain in docs
- Persist vector index locally under ./data/index/ (create folder)
- Provide a CLI:
  python -m app.rag.ingest

# 🛡️ Policy / Verifier rules (must implement)
- Must cite at least 2 retrieved snippets in solution (by id) OR output NOT_ENOUGH_CONTEXT
- If solution suggests destructive actions (delete data, disable auth, apply terraform), set NEED_HUMAN_APPROVAL=true
- Output must be valid JSON matching Pydantic models; otherwise repair once then fail.

# 🧪 Testing + Quality Gates
- Use pytest
- Add ruff + mypy configs in pyproject
- Provide pre-commit suggestions in README (optional)
- Ensure tests cover:
  - ingestion creates index
  - retrieval returns results
  - graph runs end-to-end on a sample ticket
  - API contract
  - policy gating path

# 📈 Evaluation Harness (must implement)
- golden_set.jsonl contains tickets + expected rubric notes (not exact answers)
- rubric.py scores:
  - Grounding (0–2)
  - Structure (0–2)
  - Safety/Policy compliance (0–2)
  - Practicality (0–2)
- run_eval.py runs N tickets, stores eval_report.json with per-case scores + totals

# 📝 Documentation (must produce)
README.md must include:
- what it does (1 paragraph)
- architecture diagram (ASCII)
- quickstart (local) with exact commands
- docker run instructions
- sample curl requests + sample outputs
docs/architecture.md:
- data flow diagram
- LangGraph state machine explanation
docs/runbook.md:
- troubleshooting (index missing, model not reachable, slow retrieval)
- log fields and where to look
docs/threat_model.md:
- prompt injection, data leakage, least privilege tool scope (even for local tools)
docs/api.md:
- endpoint schemas
docs/eval.md:
- how rubric works + how to interpret report

# 🏁 Run commands (must work)
Provide Makefile targets:
- make setup
- make ingest
- make run
- make test
- make eval
All commands must be copy-paste runnable.

# ⚠️ Constraints
- Keep the PoC small, but do not skip “production touches”:
  structure, typing, validation, logging, tests, docs, runbook, minimal Dockerfile.
- No placeholders like “TODO implement”.
- If any external dependency is optional (qdrant/ollama), provide clear fallback path.

# ✅ Output Format (how you must respond)
1) First: show the final repo tree
2) Then: provide each file with its full content in fenced code blocks
3) Ensure nothing is missing; everything must run.
```


[1]: https://huggingface.co/datasets/pacovaldez/stackoverflow-questions "pacovaldez/stackoverflow-questions · Datasets at Hugging Face"

