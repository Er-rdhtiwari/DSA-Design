# 15-Day Disney AI Core (Backend AI Lead) Prep Plan

### (Daily Copy-Paste Ready Super Prompts)

## Day 1 — JD Deconstruction + Your Fit Narrative (STAR Library)

```text
You are my Staff/Principal Backend + AI Platform interview coach.

Goal: Convert this Disney AI Core Engineering JD into a preparation map and my personal “fit narrative”.

Context: I am Lead Backend Engineer at IBM. Strong in Golang + Python, microservices, distributed systems, CI/CD, reliability. Preparing for Disney Ad Platforms AI Core Engineering role focused on reusable AI platform components, agent orchestration (LangGraph/LangChain), model integration services, and platform engineering rigor.

Tasks:
1) Extract and list the top 15 responsibilities/expectations from the JD.
2) Convert them into a competency matrix grouped under:
   A) System Design & Architecture (service boundaries, multi-tenancy, scalability)
   B) AI Platform & Agent Orchestration (LangGraph/LangChain patterns)
   C) Model Integration Layer (LLM gateway, routing, fallbacks, cost controls)
   D) Reliability/Observability/Operations (SLOs, tracing, runbooks)
   E) Engineering Excellence (testing, CI/CD, code quality, reviews)
   F) Leadership & Cross-Region Collaboration (Bangalore ↔ US, influence, mentoring)
3) For each competency, provide:
   - What “excellent” looks like in interview answers
   - Common weak answers / red flags
   - Evidence I should prepare (projects, metrics, incidents, PRs)
4) Build my “Story Bank”:
   - 6 STAR stories: architecture, scale incident, reliability improvement, team mentoring, cross-team conflict, delivery under ambiguity
   - For each story include: situation, task, actions (with technical depth), measurable results, what I learned.
5) Provide a one-page “Interview Cheat Sheet”:
   - My 60-second intro
   - My 2-minute “Why Disney + Why AI Core”
   - 8 bullets that map IBM work to JD keywords
Deliverables: competency matrix + story bank + cheat sheet + what to revise tomorrow.
```

---

## Day 2 — AI Platform Architecture Fundamentals (Control Plane vs Data Plane)

```text
Teach me AI Platform architecture as if I must design Disney “AI Core” used by multiple Ad Platform teams.

Explain in depth:
1) Definitions with examples:
   - Control plane vs data plane for AI platform
   - Orchestration vs execution vs model gateway
   - Agent runtime vs workflow definition vs tool registry
2) Reference Architecture:
   - Core building blocks: workflow registry, run service, step executor, tool service, model gateway, policy engine, audit store, evaluation pipeline, observability pipeline
   - How teams consume it (SDK, APIs, templates)
3) API & Contract Design:
   - Required endpoints (workflow CRUD, run start/cancel, run status, step status, logs, tool invocation, model completion)
   - Versioning strategy (workflow versions, API versions, compatibility)
4) Non-functional requirements:
   - Multi-tenancy isolation
   - Latency targets and cost targets
   - Reliability and failover
   - Security & governance hooks
5) Provide:
   - ASCII architecture diagram (services + data stores + event bus)
   - Minimal “platform contract” spec (OpenAPI-like) for 5 endpoints
   - List of top 10 design tradeoffs + how to justify decisions in interviews
6) End with:
   - 10 interview questions with strong sample answers
   - A quick self-test checklist (if I can answer these, I’m ready)
```

---

## Day 3 — System Design Deep Dive: Agent Orchestration Service (LangGraph-like)

```text
Act as my system design interviewer for “Agent Orchestration Service” (workflow-based, LangGraph-like).

Design requirements:
- Teams define workflows (graph of steps)
- Steps can call LLMs and tools
- Supports retries, backoff, timeouts, cancellation
- Supports human-in-the-loop step (optional)
- Multi-tenant, versioned workflows
- Durable execution with idempotency
- Works in Kubernetes, scales horizontally
- Observability: logs/metrics/traces per run + per step
- Security: authN/authZ, secrets, audit logs

Deliver:
1) Requirements (functional + non-functional) and assumptions
2) High-level architecture and components
3) Detailed execution model:
   - How workflow is stored
   - How runs are created
   - How steps are scheduled
   - How state is persisted
   - How retries/cancellation happen
4) Data model:
   - Tables for workflow_def, workflow_version, run, step_run, tool_call, model_call, audit_log
   - Indexing strategy for querying “latest runs”, “stuck runs”, “tenant usage”
5) Reliability:
   - Idempotency key strategy
   - At-least-once processing handling
   - Deduplication + retry semantics
   - Failure modes and mitigations (worker crash, tool timeout, model provider outage, DB slowdown)
6) Scaling:
   - Worker pools, backpressure, rate limits per tenant
   - Queue vs direct execution patterns
7) Security + governance hooks:
   - PII redaction points
   - Policy enforcement points
   - Audit trails
8) Observability:
   - Metrics list, log schema, trace spans
   - SLO proposal + alert examples
9) Final: 10 “push-back” interviewer follow-ups and best responses.
Include at least 1 ASCII diagram and 1 sequence diagram for “Start Run”.
```

---

## Day 4 — Model Integration Layer: LLM Gateway + Routing + Policy

```text
Teach and design a “Model Integration Layer / LLM Gateway” for enterprise production.

Cover:
1) Provider abstraction:
   - Unified interface (chat, embeddings, tool-calls)
   - Adapters for providers (OpenAI/Bedrock/etc.) with request/response normalization
2) Routing & selection:
   - Model registry + capabilities (context window, cost, latency, regions)
   - Routing rules based on tenant, use-case, latency/cost constraints
   - Fallback strategy (provider outage, rate limit, timeouts)
   - Canary/A-B testing toggles
3) Reliability engineering:
   - Timeouts, retries with jitter, circuit breaker, bulkheads
   - Rate limits: global and tenant-level
   - Request hedging concept (optional)
4) Cost & performance controls:
   - Token budgeting and enforcement
   - Prompt caching (semantic vs exact)
   - Response caching with TTL and invalidation
   - Batching (where appropriate)
5) Governance & security:
   - PII redaction, secret handling
   - Prompt injection defenses and allowlisted tools
   - Audit logging requirements
6) Deliverables:
   - An API spec for /chat and /embeddings with fields for tenant, purpose, idempotency, trace_id
   - Python pseudo-code for gateway + one provider adapter + router + fallback logic
   - A list of 12 interview talking points + tradeoffs
```

---

## Day 5 — Multi-Agent Patterns + Tooling Architecture

```text
Teach multi-agent orchestration and tool calling as used in real production AI platforms.

Explain with examples and decision rules:
1) Patterns:
   - ReAct (tool-use loop)
   - Planner–Executor
   - Supervisor–Worker
   - Router (intent-based)
   - Critic/Reflection (lightweight, cost-aware)
2) Choosing patterns:
   - When to keep single-agent
   - When multi-agent is worth it
   - How to limit runaway costs and loops
3) Tooling system design:
   - Tool registry, tool schemas (JSON schema), validation
   - Permissions: tool allowlists per tenant / per workflow
   - Tool execution: timeouts, sandboxing, retries
   - Tool result caching and idempotency
4) Threats & pitfalls:
   - Prompt injection and tool hijacking
   - Infinite loops and “agent drift”
   - Non-determinism hurting debugging
5) Deliverables:
   - A “tool calling contract” design
   - A checklist of safeguards
   - 12 interview questions + strong sample answers
   - A short demo workflow example (planner→tool→summarize) in pseudo-code.
```

---

## Day 6 — Hands-on Build #1: AI Workflow Runner (FastAPI) — Full Skeleton

```text
Create a production-style mini-project: “AI Workflow Runner” (Python + FastAPI).

I want a clean repo that I can show in interview discussions.

Requirements:
A) Core Features
1) Define workflows (in code to start, but designed for DB later)
2) Start workflow run: POST /runs
3) Query run status: GET /runs/{id}
4) Cancel run: POST /runs/{id}/cancel
5) Track step-level execution statuses

B) Execution Engine
1) Async execution using a background worker pattern (asyncio task group OR queue+workers)
2) Concurrency limits (global and per-tenant)
3) Timeouts and cancellation propagation
4) Retries with jitter per step
5) Idempotency key support on run start

C) Production Readiness
1) Structured logging (json logs with run_id, step_id, tenant_id, trace_id)
2) Metrics placeholders (latency, error counts, token/cost placeholders)
3) Config management (env vars)
4) Clean architecture (service layer + repository layer)
5) Unit tests with pytest (minimum 6 tests)

Deliver:
- Repo structure (folders/files)
- All code for minimal runnable version
- How to run locally (commands)
- Explain design choices and what to improve if this was real production.
```

---

## Day 7 — Upgrade Build: Persistence + State Machine + Idempotency + DLQ

```text
Upgrade the AI Workflow Runner project to be more “enterprise platform”.

Add:
1) Persistence using SQLite + SQLAlchemy (or a simple DB layer)
2) Explicit state machine:
   - Run: CREATED → RUNNING → SUCCEEDED/FAILED/CANCELED
   - Step: PENDING → RUNNING → SUCCEEDED/FAILED/SKIPPED
3) Idempotency:
   - Support idempotency key on POST /runs
   - Ensure duplicate calls return same run_id
4) Retry policy:
   - per-step max attempts
   - exponential backoff + jitter
   - record attempts
5) Dead-letter handling:
   - if a step fails after retries, mark run failed and store failure reason
   - create a DLQ table/flag for failed runs to investigate

Deliver:
- Updated schema/migrations
- Updated API behavior docs
- Minimum 8 tests including idempotency + cancellation + retry edge cases
- A short section: “How I’d scale this on Kubernetes”
```

---

## Day 8 — Observability Mastery (Logs, Metrics, Tracing, SLOs, Runbooks)

```text
Teach observability for AI orchestration and model gateway systems, like an SRE + platform engineer.

Cover:
1) Structured logging:
   - What fields to include (run_id, step_id, tenant_id, workflow_version, model, tool, latency_ms, error_type, cost_estimate)
   - Example JSON log lines for: run started, step started, tool call, model call, retry, run finished
2) Metrics:
   - Golden signals: latency/error/saturation
   - AI platform extras: token usage, cost per tenant, cache hit rate, model fallback rate, tool timeout rate
   - Example metric names and labels
3) Tracing:
   - Span naming conventions (run span, step span, tool span, model span)
   - Propagation of trace_id across services
4) SLOs + alerts:
   - Propose 3 SLOs and alert rules
   - “What wakes someone up at 2am?”
5) Debugging playbooks:
   - Stuck runs
   - High latency
   - Provider rate limiting
   - Cost spikes
6) Deliver:
   - Dashboard layout outline
   - Runbook outline template
   - 10 interview questions & answers
```

---

## Day 9 — Testing Strategy (AI Platform-Grade)

```text
Create a complete testing strategy for:
- Agent orchestration service
- Model gateway
- Tool execution system

Cover:
1) Unit tests: what to mock, what to assert
2) Integration tests: DB + queue + service interactions
3) Contract tests: provider adapter contracts (request/response normalization)
4) Determinism strategy for LLM tests:
   - golden responses, snapshot tests, fixtures
   - failure simulation (timeouts, 429, 500)
5) Load tests:
   - scenarios, metrics to capture, capacity planning inputs
6) CI/CD gates:
   - lint, type checks, security scanning, test coverage thresholds

Deliver:
- A test plan checklist
- Example pytest tests for workflow execution and model gateway routing
- A “testing pitfalls” section (flaky tests, nondeterminism, over-mocking)
```

---

## Day 10 — Security + Governance for Enterprise AI (Differentiator)

```text
Teach me security & governance design for enterprise AI platform services.

Cover deeply:
1) AuthN/AuthZ:
   - JWT/OAuth, service-to-service auth
   - RBAC and tenant isolation
   - Permissions for tools and workflows
2) Secrets management:
   - tool credentials
   - model provider keys
   - rotation patterns
3) Prompt injection defense:
   - input validation
   - tool allowlisting
   - content filtering
   - “never trust tool output blindly”
4) Privacy:
   - PII detection/redaction points
   - data retention
   - audit logging
   - access controls for logs
5) Compliance-friendly design:
   - audit trails, change management for workflow defs
   - approvals for high-risk tools

Deliver:
- A security checklist I can speak in interview
- 8 real incident scenarios + mitigations
- Where to enforce policy in architecture (control plane points)
- A minimal threat model (STRIDE-style summary)
```

---

## Day 11 — Scalability Engineering: Queues, Workers, Backpressure, Rate Limits

```text
Teach scalability patterns needed for an orchestration engine and model gateway.

Cover:
1) Execution patterns:
   - synchronous vs async
   - queue + worker pool
   - scheduling strategies
2) Backpressure:
   - bounded queues
   - concurrency limits
   - admission control
3) Rate limiting:
   - per-tenant and global
   - token budgets and QPS budgets
4) Delivery semantics:
   - at-least-once processing
   - idempotency and dedup
   - exactly-once illusion patterns
5) Long-running steps:
   - heartbeats
   - leases
   - resuming after crash
6) Deliver:
   - ASCII architecture diagram for scalable execution
   - A “tradeoff table” (Kafka vs SQS, Redis queue vs Celery, asyncio vs workers)
   - 10 interview questions with strong answers
```

---

## Day 12 — Leadership + Cross-Region Execution Playbook (Bangalore ↔ US)

```text
Coach me for the leadership + collaboration side of the role.

Tasks:
1) Provide a playbook for working with US tech leadership:
   - design alignment, RFCs, decision logs (ADRs)
   - review rituals and escalation paths
2) Give me templates:
   - Design doc template (system design)
   - RFC template (proposal + tradeoffs)
   - ADR template (decision record)
   - Weekly status update template (metrics + risks + asks)
3) Mentoring and raising engineering standards:
   - code review checklist
   - system design review checklist
   - CI/CD quality gates proposal
4) Behavioral interview:
   - Ask 12 behavioral questions
   - Provide strong sample answers tailored to a Lead Backend at IBM moving to AI Core
5) Deliver:
   - A “leadership talking points” cheat sheet
   - 5 conflict scenarios and how to respond
```

---

## Day 13 — Hands-on Build #2: Model Gateway Prototype (with Fallback + Cost Control)

```text
Build a minimal but interview-ready “Model Gateway” service in Python.

Requirements:
1) FastAPI endpoint POST /chat
2) Provider abstraction interface (ChatProvider)
3) Two mock providers simulating:
   - latency variance
   - failures (429, timeout, 500)
4) Router:
   - choose provider/model based on tenant + policy
   - fallback on failure
5) Cost control:
   - token budget enforcement (estimate tokens)
   - reject or downgrade when budget exceeded
6) Caching:
   - simple cache for identical prompt (in-memory ok)
7) Observability:
   - structured logs + metric placeholders
8) Tests:
   - minimum 8 tests: routing, fallback, timeout, budget, caching

Deliver:
- Repo layout
- Full code + run commands
- Explain design tradeoffs and how to evolve for real providers.
```

---

## Day 14 — Evaluation + A/B Testing + Quality Metrics (Platform Differentiator)

```text
Extend the Model Gateway to support evaluation and experimentation.

Add:
1) A/B routing:
   - 90/10 split configurable
   - stable hashing on tenant/user id
2) Eval logging:
   - store prompt, response, model, latency, token usage, cost estimate
   - store “quality score placeholder”
3) Offline evaluation:
   - dataset format (jsonl)
   - script to run batch eval using mock “judge”
   - summary report: latency percentiles, error rates, cost, win-rate

Deliver:
- Updated code
- Example dataset file
- A sample evaluation report output
- Interview talking points: how to justify A/B, how to talk about eval rigor without overclaiming.
```

---

## Day 15 — Full Interview Simulation (Behavioral + System + Coding + Debrief)

```text
Run a full interview simulation for Disney AI Core Engineering (Lead Backend + AI platform).

Structure:
A) Behavioral (10–15 min)
- Ask me 6 questions one-by-one and wait for my answer each time.
- After each answer: critique + improved version + what signal it shows.

B) System Design (30–40 min)
Topic: Agent Orchestration Service
- Start by asking clarifying questions.
- Force tradeoffs: latency vs cost, sync vs async, multi-tenancy, versioning, governance.
- Push on failure modes, idempotency, observability, and scaling.
- At the end: score my design, list gaps, give a model answer outline.

C) Coding (30–40 min)
Problem: Implement a concurrency-limited workflow executor in Python with:
- max concurrency
- per-task timeout
- cancellation
- retries with jitter
- returns structured results
Provide constraints and edge cases.
Evaluate my solution for correctness, clarity, and production safety.

D) Debrief
- Scorecard (architecture, backend fundamentals, AI platform knowledge, leadership)
- 1-week targeted revision plan
Start now with the first behavioral question only and wait.
```

---
