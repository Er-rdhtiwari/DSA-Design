## Day 1 — Vanilla RAG

```text
Act as a patient Staff AI Engineer mentor. Teach me Day 1 of my Disney-focused study plan in very simple language. I am not confident in this topic yet, so start from the foundation and build step by step. Define every new term before using it. Use easy backend examples and practical intuition.

Today’s topic: Vanilla RAG end to end.

My goal:
Help me deeply understand Vanilla RAG from first principles, then move into production-grade challenges, trade-offs, and optimization strategies. Keep the Disney Staff AI Engineer role as the central focus, so explain how this knowledge helps build reliable, scalable AI-powered backend systems.

Please cover all important topics and subtopics in a logical learning order:

A. Foundational knowledge I need first
- What problem RAG solves
- Why LLMs alone are not enough for many real business systems
- Difference between pretraining knowledge, prompting, fine-tuning, and retrieval
- Basic concepts: documents, chunks, embeddings, vector search, retrieval, reranking, grounding, hallucination, context window
- Difference between keyword search, semantic search, and hybrid search
- Why recall and precision matter in retrieval systems

B. Vanilla RAG architecture step by step
- Data ingestion flow
- Document parsing basics
- Cleaning and normalization
- Chunking basics
- Chunk size and overlap trade-offs
- Embedding generation
- Vector indexing basics
- Metadata storage basics
- Retrieval flow
- Top-k retrieval
- Reranking basics
- Context assembly
- Prompt construction for RAG
- Answer generation
- Citation-aware answering
- Feedback loop basics

C. How each stage connects to the next
- How chunking affects embeddings
- How embeddings affect retrieval quality
- How retrieval quality affects final answer quality
- How context size affects cost, latency, and answer quality
- How poor ingestion can break the full pipeline

D. Production-grade challenges
- Bad chunking choices
- Missing metadata
- Stale data
- Duplicate documents
- Poor parsing quality
- Low recall
- Low precision
- Wrong top-k
- Context pollution
- Hallucinated answers even when retrieval exists
- Slow retrieval
- High token cost
- Multi-tenant isolation concerns
- Security and privacy concerns
- Monitoring blind spots
- Evaluation blind spots

E. Optimization strategies
- Better chunking strategies
- Metadata filtering
- Hybrid search
- Query rewriting
- Reranking
- Context compression
- Better prompt construction
- Better top-k selection
- Retrieval caching
- Embedding model selection trade-offs
- Index tuning basics
- Freshness strategies
- Cost vs quality vs latency trade-offs
- When vanilla RAG is enough and when advanced RAG is needed

F. Staff-level understanding
- How to explain RAG in a system design interview
- How to discuss failure modes and trade-offs
- What a Staff AI Engineer should own in a production RAG system
- How RAG fits into AI-powered ad platforms or enterprise AI products

Output format:
1. Core idea in simple words
2. Foundational concepts
3. End-to-end Vanilla RAG flow
4. Inter-relation between all stages
5. Production-grade challenges
6. Optimization strategies
7. Easy real-world example
8. Staff-level interview angle


Important style instructions:
- Use simple language
- Use clear section headers
- Use easy examples
- Do not skip basics
- Do not assume prior knowledge
- Make the notes detailed but easy to revise later
```

## Day 2 — LlamaIndex

```text
Act as a patient Staff AI Engineer mentor. Teach me Day 2 of my Disney-focused study plan in very simple language. I am not confident in this topic yet, so begin from the foundations and then go deeper. Define every new term clearly and use practical examples.

Today’s topic: LlamaIndex end to end.

My goal:
Help me understand LlamaIndex from first principles, especially how it helps build data-aware AI applications, RAG pipelines, and workflows in production systems. Keep the Disney Staff AI Engineer role as the central focus.

Please cover all important topics and subtopics in a logical learning order:

A. Foundational knowledge I need first
- What LlamaIndex is
- What problem LlamaIndex solves
- How LlamaIndex differs from plain Vanilla RAG
- How LlamaIndex differs from LangChain at a practical level
- Core mental model: data ingestion, indexing, retrieval, query engine, workflows, agents
- When LlamaIndex is a good fit and when it is not

B. Data ingestion foundations
- Documents, nodes, chunks, metadata
- Loaders and connectors at a conceptual level
- Parsing and cleaning basics
- Structured vs unstructured data
- Document pipelines
- Why ingestion quality matters

C. Embeddings and indexing
- How LlamaIndex uses embeddings
- Index types at a high level
- Vector indexes in practical terms
- Metadata-aware indexing
- Index update and refresh thinking
- Cost and performance considerations

D. Retrieval and query flow
- Retriever basics
- Query engine basics
- Similarity search
- Metadata filtering
- Hybrid retrieval concepts
- Reranking basics
- Response synthesis
- Citation-aware answering
- How retrieval quality affects answer quality

E. Search and optimization
- Chunk size trade-offs
- Chunk overlap
- Better metadata design
- Query rewriting concepts
- Hybrid search basics
- Retrieval tuning
- Top-k tuning
- Context quality optimization
- Latency and cost optimization

F. Workflows and agents in LlamaIndex
- High-level workflow concepts
- Agent concepts inside LlamaIndex
- Document-centric workflows
- When to use workflows vs simple retrieval
- When to use agents vs deterministic logic

G. Production-grade challenges
- Parsing quality issues
- Inconsistent metadata
- Retrieval drift
- Freshness issues
- Slow queries
- High token cost
- Large document collections
- Multi-tenant isolation
- Access control concerns
- Evaluation gaps
- Observability gaps
- Deployment and scaling concerns

H. Optimization strategies
- Better ingestion design
- Better metadata design
- Better indexing strategy
- Better filtering strategy
- Better retriever setup
- Better synthesis strategy
- Better evaluation approach
- Better caching approach
- When to combine LlamaIndex with other tools

I. Staff-level understanding
- How to explain LlamaIndex in a system design interview
- How to choose LlamaIndex vs building directly
- How to use LlamaIndex in production AI backend systems
- How it supports Disney-like document, knowledge, and workflow-heavy use cases

Output format:
1. Core idea in simple words
2. Foundational concepts
3. LlamaIndex building blocks
4. End-to-end flow
5. Inter-relation between ingestion, embeddings, retrieval, and response
6. Production-grade challenges
7. Optimization strategies
8. Easy real-world example
9. Staff-level interview angle


Important style instructions:
- Use very simple language
- Use clear comparisons where helpful
- Explain the “why” behind each component
- Keep examples practical and backend-focused
```

## Day 3 — LangChain

```text
Act as a patient Staff AI Engineer mentor. Teach me Day 3 of my Disney-focused study plan in very simple language. I am not confident in this topic yet, so please start from foundational ideas and then build toward production use.

Today’s topic: LangChain end to end.

My goal:
Help me understand LangChain as a framework for building LLM-powered applications, especially where it fits in production AI systems and how it helps with integrations, prompting, tools, retrieval, and application assembly. Keep the Disney Staff AI Engineer role as the central focus.

Please cover all important topics and subtopics in a logical learning order:

A. Foundational knowledge I need first
- What LangChain is
- What problem LangChain solves
- How LangChain differs from writing everything manually
- How LangChain differs from LlamaIndex in practical terms
- How LangChain relates to LangGraph
- When LangChain is useful and when it may be unnecessary

B. Core building blocks
- Models
- Prompts
- Output parsers
- Retrievers
- Tools
- Chains
- Memory/state at a high level
- Callbacks/observability concepts
- Provider integrations
- Why component composition matters

C. Prompting and structured generation
- Prompt templates
- Few-shot prompting
- Structured output
- Schema-guided generation
- Output parsing
- Reliability considerations for structured generation

D. Retrieval and tool integration
- How LangChain supports retrievers
- How it can participate in RAG pipelines
- Tool calling and external integrations
- Database/search/API tools at a conceptual level
- Why tool calling is useful in business workflows

E. Production-grade challenges
- Framework abstraction confusion
- Hidden complexity
- Poor prompt design
- Tool misuse
- Unclear state handling
- Debugging difficulty
- Provider coupling
- Versioning issues
- Cost/latency concerns
- Reliability concerns
- Evaluation gaps
- Observability gaps

F. Optimization strategies
- Keep chains simple
- Use clear interfaces
- Structured outputs where needed
- Reduce unnecessary abstraction
- Choose the right components
- Improve prompts and validation
- Improve tool boundaries
- Improve observability
- Improve testing and evaluation
- Know when to move from LangChain to LangGraph

G. Staff-level understanding
- How LangChain fits in a production AI platform
- How to decide whether to use LangChain or not
- How to explain LangChain in interviews
- How LangChain helps build reusable AI application patterns for Disney-like systems

Output format:
1. Core idea in simple words
2. Foundational concepts
3. LangChain building blocks
4. End-to-end example flow
5. Inter-relation between prompts, tools, retrieval, and outputs
6. Production-grade challenges
7. Optimization strategies
8. Easy real-world example
9. Staff-level interview angle


Important style instructions:
- Keep the explanation simple but structured
- Use practical examples instead of abstract theory
- Clearly show where LangChain helps and where it can hurt
```

## Day 4 — LangGraph

```text
Act as a patient Staff AI Engineer mentor. Teach me Day 4 of my Disney-focused study plan in very simple language. I am not confident in this topic yet, so please start from the foundation and then build toward production architecture.

Today’s topic: LangGraph end to end.

My goal:
Help me understand LangGraph as a framework for stateful, controllable, production-grade AI workflows and agents. Keep the Disney Staff AI Engineer role as the central focus.

Please cover all important topics and subtopics in a logical learning order:

A. Foundational knowledge I need first
- What LangGraph is
- What problem LangGraph solves
- Why simple chains are not enough for many real AI systems
- How LangGraph differs from LangChain at a practical level
- Deterministic workflow vs agentic workflow
- When LangGraph is a good fit and when it is not

B. Core concepts
- State
- Nodes
- Edges
- Control flow
- Conditional routing
- Tool execution steps
- Checkpointing basics
- Durable execution
- Human-in-the-loop
- Streaming concepts
- Retry and recovery thinking

C. Workflow design
- How to model a multi-step AI workflow
- State transitions
- Branching and routing
- Validation steps
- Retry logic
- Approval steps
- Fallback logic
- Guardrails
- Why explicit workflow design matters

D. Agents with LangGraph
- Agent loops in simple language
- Tool-using agents
- Planner/executor mental model
- Controlled autonomy
- When an agent should be constrained
- When a deterministic graph is better than a free-form agent

E. Production-grade challenges
- Unclear state design
- Workflow sprawl
- Infinite loops or poor stopping conditions
- Tool failures
- Hard-to-debug behavior
- Poor recovery logic
- Cost blowups
- Latency accumulation
- Multi-step observability issues
- Human review bottlenecks
- Reliability and rollback concerns

F. Optimization strategies
- Strong state schema
- Small clear nodes
- Explicit validation
- Better routing rules
- Bounded retries
- Human review only where needed
- Better telemetry
- Better testing strategy
- Better fallback behavior
- Better cost/latency controls

G. Staff-level understanding
- How to explain LangGraph in a system design interview
- How to decide when orchestration needs LangGraph
- How LangGraph fits Disney-like production AI systems
- How to discuss durable execution, control, and reliability trade-offs

Output format:
1. Core idea in simple words
2. Foundational concepts
3. LangGraph building blocks
4. End-to-end workflow example
5. Inter-relation between state, routing, tools, and recovery
6. Production-grade challenges
7. Optimization strategies
8. Easy real-world example
9. Staff-level interview angle


Important style instructions:
- Use easy terms
- Prefer workflow examples over theory
- Keep the note practical and production-focused
```

## Day 5 — MCP

```text
Act as a patient Staff AI Engineer mentor. Teach me Day 5 of my Disney-focused study plan in very simple language. I am not confident in this topic yet, so begin from the foundation and move step by step.

Today’s topic: MCP (Model Context Protocol) end to end.

My goal:
Help me understand MCP from first principles, especially how it standardizes tool and data connectivity for AI applications, and how it fits into production-grade AI systems. Keep the Disney Staff AI Engineer role as the central focus.

Please cover all important topics and subtopics in a logical learning order:

A. Foundational knowledge I need first
- What MCP is
- What problem MCP solves
- Why custom one-off tool integrations do not scale
- How MCP differs from normal function calling or ad hoc tool wrappers
- MCP mental model in simple words

B. MCP architecture
- Host
- Client
- Server
- Tools
- Data/resources
- Prompts/workflows if relevant
- Stateful session concept
- Why client-host-server separation matters
- JSON-RPC idea at a high level, only in simple language

C. MCP in practical AI systems
- Connecting AI applications to external tools
- Connecting to data sources
- Connecting to internal enterprise systems
- Read-only vs action-taking integrations
- Why standardization matters in multi-tool environments
- How MCP can reduce integration sprawl

D. Security and governance foundations
- Why MCP introduces new security concerns
- Authentication and authorization concepts
- Least privilege
- Tool scoping
- Approval flows
- Auditability
- Prompt injection risks through external systems
- Data leakage risks
- Safe action boundaries

E. Production-grade challenges
- Too many tools
- Tool discovery confusion
- Bad server design
- Weak permissions
- Latency across remote tools
- Reliability issues
- Tool result inconsistency
- Observability gaps
- Governance issues
- Versioning and compatibility concerns
- Operational ownership concerns

F. Optimization strategies
- Strong interface design
- Clear tool boundaries
- Good permission boundaries
- Narrow tool scope
- Better caching where appropriate
- Good observability
- Good retry and timeout policy
- Safe fallback behavior
- Better server quality
- Better governance model

G. Staff-level understanding
- How to explain MCP in interviews
- When MCP is worth adopting
- How MCP fits with agent/tool ecosystems
- How MCP can help Disney-like enterprise AI platforms integrate safely with external and internal systems

Output format:
1. Core idea in simple words
2. Foundational concepts
3. MCP architecture explained simply
4. End-to-end practical flow
5. Inter-relation between host, client, server, tools, and governance
6. Production-grade challenges
7. Optimization strategies
8. Easy real-world example
9. Staff-level interview angle


Important style instructions:
- Keep protocol discussion simple
- Focus on practical understanding, not spec-heavy detail
- Always connect concepts back to real production systems
```

## Day 6 — Interrelationship of RAG, LlamaIndex, LangChain, LangGraph, and MCP

```text
Act as a patient Staff AI Engineer mentor. Teach me Day 6 of my Disney-focused study plan in very simple language. I am not confident in how all these topics connect, so I want a full synthesis from foundation to production architecture.

Today’s topic: The complete interrelationship between Vanilla RAG, LlamaIndex, LangChain, LangGraph, and MCP.

My goal:
Help me understand how these topics relate to each other, where they overlap, where they differ, when to use which one, and how they fit together in a production-grade AI backend system. Keep the Disney Staff AI Engineer role as the central focus.

Please cover all important topics and subtopics in a logical learning order:

A. Foundational mental model
- What is a retrieval pattern
- What is a framework
- What is an orchestration runtime
- What is a protocol
- Why people confuse these categories
- Simple category map:
  - Vanilla RAG as a design pattern
  - LlamaIndex as a data/retrieval/workflow-oriented framework
  - LangChain as an LLM application framework and integration layer
  - LangGraph as a stateful orchestration/runtime layer
  - MCP as a tool/data connectivity protocol

B. Compare each one clearly
- What problem each solves
- What each is best at
- What each is not mainly meant for
- Where they overlap
- Where they complement each other
- Common misconceptions

C. How they connect in a real system
- Vanilla RAG as the retrieval backbone
- LlamaIndex for ingestion/index/query workflows over enterprise data
- LangChain for application assembly, prompts, tools, and integrations
- LangGraph for stateful multi-step workflows and agents
- MCP for standardized external tool/data connectivity
- Where model providers, vector DBs, and APIs sit around them

D. End-to-end production example
- User request enters API
- Routing/orchestration decision
- Retrieval path
- Tool path
- Graph/workflow path
- External tool/data access through MCP if relevant
- Response synthesis
- Logging, evaluation, fallback, and governance
- Explain the full request lifecycle in simple terms

E. Production-grade challenges across the full stack
- Too much framework complexity
- Wrong tool choice
- Poor boundaries between layers
- Debugging difficulty
- Security and governance risks
- High latency and high cost
- Weak observability
- Weak evaluation
- Provider lock-in
- Operational ownership confusion

F. Optimization strategies across the full stack
- Clear separation of concerns
- Good interfaces between layers
- Use simple RAG when enough
- Use LlamaIndex where data pipelines matter
- Use LangChain where app composition matters
- Use LangGraph where workflow control matters
- Use MCP where standardized connectivity matters
- Keep observability, evaluation, security, and cost controls across all layers

G. Staff-level understanding
- How to explain the full stack in a system design interview
- How to choose the right combination for a problem
- How to justify trade-offs
- How to answer “Why this framework and not that one?”
- How this full picture maps to Disney-like AI platform work

Output format:
1. Core integrated summary
2. Foundational category map
3. Clear comparison table in plain English
4. Inter-relation between all five topics
5. One end-to-end production architecture example
6. Production-grade challenges across the full stack
7. Optimization strategies across the full stack
8. Staff-level interview angle


Important style instructions:
- Use very simple language
- Make overlaps and differences crystal clear
- Use one consistent end-to-end example throughout
- Focus on practical architecture, not marketing language
```
* ([disneycareers.com][1])
* ([LangChain Docs][2])


[1]: https://www.disneycareers.com/en/job/bengaluru/staff-ai-engineer/391/91426017952?utm_source=chatgpt.com "Staff AI Engineer at DISNEY"
[2]: https://docs.langchain.com/oss/python/langgraph/overview?utm_source=chatgpt.com "LangGraph overview - Docs by LangChain"
---

##  **Day 7

```text
Act as a patient Staff AI Engineer mentor. Help me revise Day 7 of my Disney-focused study plan in very simple language. I am now in revision mode, so do not teach topics in isolation. Instead, help me revise the full learning journey from Day 1 to Day 6 as one connected production AI system. I am not fully confident yet, so start from foundational mental models, then connect everything step by step. Define every important term in simple words before using it. Use one consistent easy backend example throughout.

Today’s revision topic:
Complete revision of Vanilla RAG, LlamaIndex, LangChain, LangGraph, MCP, and their full interrelationship.

My goal:
Help me revise all important topics and subtopics from Day 1 to Day 6 in a way that makes the differences, overlaps, and practical connections crystal clear. Keep the Disney Staff AI Engineer role as the central focus, so explain everything as if I am preparing to design and operate production-grade AI backend systems.

Please cover all important topics and subtopics in a logical revision order:

A. Foundational category map first
- What is a design pattern
- What is a framework
- What is an orchestration runtime
- What is a protocol
- Why these categories are often confused
- Category map:
  - Vanilla RAG as a retrieval design pattern
  - LlamaIndex as a data and retrieval oriented framework
  - LangChain as an LLM application framework and integration layer
  - LangGraph as a stateful orchestration/runtime layer
  - MCP as a standard protocol for tool and data connectivity

B. Revise Vanilla RAG end to end
- What problem RAG solves
- Why plain LLM knowledge is often not enough
- Documents, chunks, embeddings, vector search, retrieval, reranking, grounding
- Keyword vs semantic vs hybrid retrieval
- Chunking, overlap, metadata, top-k, context assembly
- Prompt construction for RAG
- Citation-aware answering
- Retrieval quality vs answer quality
- Production challenges in RAG
- Optimization strategies in RAG

C. Revise LlamaIndex end to end
- What LlamaIndex is
- How it differs from plain RAG
- Data ingestion, parsing, nodes, metadata, indexing
- Embeddings and retrieval in LlamaIndex
- Filtering, query engine, response synthesis
- Search optimization ideas
- Workflow and agent concepts in LlamaIndex
- Production challenges in LlamaIndex
- Optimization strategies in LlamaIndex
- When LlamaIndex is a good fit

D. Revise LangChain end to end
- What LangChain is
- What problem it solves
- Core building blocks: models, prompts, output parsers, retrievers, tools, chains, integrations
- Prompt templates and structured output
- Retrieval and tool integration
- How LangChain helps assemble AI applications
- Production-grade challenges in LangChain
- Optimization strategies in LangChain
- When LangChain is useful and when it may be unnecessary

E. Revise LangGraph end to end
- What LangGraph is
- Why it is needed beyond simple chains
- State, nodes, edges, routing, control flow
- Deterministic workflow vs agentic workflow
- Checkpointing, retries, durable execution, human-in-the-loop
- Tool steps and validation steps
- Workflow design principles
- Production-grade challenges in LangGraph
- Optimization strategies in LangGraph
- When LangGraph is the right choice

F. Revise MCP end to end
- What MCP is
- What problem MCP solves
- Why one-off tool integrations do not scale well
- Host, client, server, tools, resources/data
- Stateful session mental model
- How MCP differs from simple function calling
- How MCP supports external tool and data connectivity
- Security and governance basics
- Production-grade challenges in MCP
- Optimization strategies in MCP
- When MCP is worth adopting

G. Full interrelationship across all five
- How Vanilla RAG connects to LlamaIndex
- How LlamaIndex connects to LangChain
- How LangChain connects to LangGraph
- How LangGraph can use tools and why MCP can help standardize tool/data access
- Where embeddings, vector DBs, APIs, model providers, and external systems fit around them
- Where they overlap
- Where they differ
- What each one is mainly for
- What each one is not mainly for
- Common misconceptions across all five topics

H. One complete end-to-end production mental model
Use one consistent simple example and explain:
- User request enters backend API
- Application decides whether it needs retrieval, tools, or workflow orchestration
- Retrieval path using RAG concepts
- LlamaIndex role if data ingestion/query workflows are involved
- LangChain role if application assembly, prompts, retrievers, or tools are involved
- LangGraph role if multi-step stateful workflow or agent control is needed
- MCP role if external tools or enterprise systems need standardized connectivity
- Response generation
- Logging, evaluation, fallback, security, governance, and monitoring around the full flow

I. Production-grade challenges across the whole stack
- Wrong tool/framework choice
- Over-engineering
- Weak boundaries between layers
- Retrieval quality issues
- Workflow complexity
- Tool failure handling
- Security and governance risks
- Weak observability
- Weak evaluation
- High latency
- High cost
- Provider lock-in
- Operational ownership confusion

J. Optimization strategies across the whole stack
- Clear separation of concerns
- Use the simplest layer that solves the problem
- Better retrieval quality controls
- Better workflow control
- Better tool boundaries
- Better observability
- Better evaluation
- Better security and governance
- Better cost and latency controls
- Better fallback strategies
- Better framework selection strategy

K. Staff-level interview understanding
- How to explain all 5 topics clearly in an interview
- How to answer: “When would you use RAG vs LlamaIndex vs LangChain vs LangGraph vs MCP?”
- How to justify trade-offs
- How to explain the architecture in simple but strong language
- How this full picture maps to Disney-like production AI systems

Output format:
1. Core integrated summary
2. Foundational category map
3. Topic-by-topic revision for Day 1 to Day 6
4. Inter-relation between all five topics
5. One complete end-to-end production example
6. Production-grade challenges across the full stack
7. Optimization strategies across the full stack
8. Common misconceptions to avoid
9. Staff-level interview angle


Important style instructions:
- Use very simple language
- Do not skip foundations
- Make differences and overlaps crystal clear
- Use one consistent example throughout
- Keep the explanation practical, production-focused, and easy to revise later
```

## Day 8 — System Design Method + Requirements + Capacity + APIs + Data Model (HLD core + LLD basics)

```text
You are my System Design + LLD interview coach for a Lead Software Engineer (Python + AI/ML, agent platforms).

Goal today:
Build my “interview muscle memory” for: requirements → capacity → APIs → data model → high-level architecture.
Also set LLD basics so I can deep dive a component when asked.

A) System Design Interview Framework (must teach clearly)
1) The 6-phase flow:
- Clarify requirements (functional + NFR)
- Capacity estimation (QPS, storage, bandwidth)
- API contracts (REST/gRPC shape, idempotency, pagination)
- Data model (entities + keys + indexes basics)
- High-level architecture (services + data + async)
- Deep dives + trade-offs + summary (reliability/security/obs)

2) Provide a reusable checklist of clarifying questions (15–20)
- Include NFR prompts: latency SLO, availability, cost, compliance/audit, multi-tenant, scaling, integration constraints.

B) Capacity Estimation (must do with examples)
- Teach step-by-step formulas: DAU/MAU, avg QPS, peak QPS, payload sizes, storage growth/day, cache hit assumptions.
- Give 2 mini scenarios and solve:
  1) “AgentRun API” traffic sizing
  2) “Document ingestion” sizing (PDF → chunks → embeddings)

C) API Design (must include common interview expectations)
- REST endpoints, filtering, pagination, versioning
- Idempotency keys (where needed)
- Error model: standard error response with code/message/request_id

D) Data Model Starter (HLD-level)
- Entities for Agent Platform: User, Tenant, Project, AgentRun, ToolExecution, Artifact, Feedback, AuditLog
- Show keys + indexes for top queries:
  - last 20 AgentRuns for project
  - audit trail by tenant/time
  - tool failures by type/status

E) LLD Basics (short but essential today)
- Explain: responsibility, cohesion/coupling, interfaces
- Give me a simple LLD template:
  - classes, responsibilities, interfaces, sequence flow, edge cases, tests

F) Case Study (today’s practice system)
“Design an AgentRun service that starts an agent workflow and tracks status.”

I must produce (deliverables):
1) Functional + NFR list (MVP + phase-2)
2) Capacity table (avg/peak QPS, storage/day, bandwidth)
3) 6–8 APIs (start_run, get_status, list_runs, tool_callback, ingest_doc, search_audit)
4) Data model outline + 5 indexes
5) A 5–7 minute “interview script” for my design approach

Include:
- 12 common mistakes (requirements/capacity/APIs)
- 10 interview Q&A
- Cheat sheet: “my reusable system design skeleton”
```
