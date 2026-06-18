**Descriptive notes + ASCII diagram + pseudocode + simple examples + short recap + one Python concept + one Python practice problem.**

---

# Day 1 Prompt — AI Infrastructure and RAG Foundations

```text
Act as a beginner-friendly AI Infrastructure mentor.

Create Day 1 study notes for an AI Infra Engineer role.

Topic:
AI Infrastructure Foundations for GenAI, RAG, and enterprise AI platforms.

Cover these topics:
1. What is AI infrastructure?
2. What is GenAI?
3. What is an LLM?
4. What is an embedding model?
5. What is a vector database?
6. What is Retrieval-Augmented Generation, also called RAG?
7. Why enterprise AI applications need scalable and reliable infrastructure.
8. Difference between:
   - LLM
   - embedding model
   - vector database
   - backend API
   - object storage
   - orchestration layer
9. Basic production AI application architecture.
10. Role of an AI Infrastructure Engineer.
11. How AI/ML engineers, backend engineers, platform architects, and infrastructure engineers work together.
12. Basic distributed systems ideas:
   - compute
   - storage
   - networking
   - latency
   - throughput
   - scalability
   - reliability

Requirements:
- Use simple beginner-friendly language.
- Include descriptive notes.
- Include easy real-world examples.
- Include one ASCII diagram showing a basic enterprise RAG architecture.
- Include pseudocode for this RAG flow:
  user question -> create embedding -> search vector database -> retrieve context -> call LLM -> return answer.
- End with a short "What to remember today" recap.

Python learning:
Teach Python basics:
- variables
- strings
- lists
- dictionaries
- loops
- if/else
- functions

Python practice problem:
Write a Python program that takes a list of server status codes:
[200, 200, 404, 500, 200, 404]
and returns a dictionary showing how many times each status code appears.

For the Python section:
- Explain the concept.
- Show pseudocode.
- Provide a clean Python solution.
- Explain the solution step by step.
```

---

# Day 2 Prompt — Production Python for AI Infrastructure

```text
Act as a beginner-friendly AI Infrastructure mentor.

Create Day 2 study notes for an AI Infra Engineer role.

Topic:
Production-Level Python for AI Infrastructure.

Start with a short revision of Day 1:
- AI infrastructure
- GenAI
- RAG
- vector database
- distributed systems basics

Cover these topics:
1. Why Python is widely used in AI infrastructure.
2. Writing clean Python functions.
3. Python modules and packages.
4. Virtual environments.
5. requirements.txt and dependency management.
6. Type hints.
7. Exception handling.
8. Logging basics.
9. Reading configuration from environment variables.
10. JSON and YAML configuration concepts.
11. API client patterns:
   - timeout
   - retry
   - backoff
   - error handling
12. Sync vs async Python at a beginner level.
13. How Python connects to:
   - embedding APIs
   - vector databases
   - object storage
   - backend services
14. Simple awareness of Go, Java, and C++ in AI infrastructure:
   - where they may be used
   - how Python services interact with services written in other languages.

Requirements:
- Use simple beginner-friendly language.
- Include descriptive notes.
- Include easy examples.
- Include one ASCII diagram showing a Python AI service talking to an embedding API, vector database, and object storage.
- Include pseudocode for a robust API call with timeout, retry, and logging.
- End with a short "What to remember today" recap.

Python learning:
Teach:
- functions
- type hints
- exceptions
- logging

Python practice problem:
Write a Python function called safe_divide(a, b) that returns a / b, but returns "Cannot divide by zero" if b is 0. Add type hints and simple logging.

For the Python section:
- Explain the concept.
- Show pseudocode.
- Provide a clean Python solution.
- Explain the solution step by step.
```

---

# Day 3 Prompt — Docker, Containers, and Microservices

```text
Act as a beginner-friendly AI Infrastructure mentor.

Create Day 3 study notes for an AI Infra Engineer role.

Topic:
Docker, containers, containerized microservices, and registry management.

Start with a short revision of Days 1 and 2:
- RAG architecture
- production Python
- API error handling and logging

Cover these topics:
1. What is a container?
2. What problem Docker solves.
3. Virtual machine vs container.
4. Docker image vs Docker container.
5. Dockerfile basics.
6. Docker build context.
7. Multi-stage Docker builds.
8. Why multi-stage builds are useful in production.
9. Docker Compose basics.
10. Container registry basics:
   - Docker Hub
   - private registry
   - cloud registry
11. Microservices architecture.
12. AI application microservices:
   - API service
   - embedding service
   - vector database
   - ingestion worker
   - inference service
   - monitoring service
13. Docker best practices:
   - small images
   - non-root user
   - no hardcoded secrets
   - health checks
   - pinned dependencies
14. Common Docker issues in AI systems:
   - large images
   - dependency conflicts
   - GPU runtime issues
   - missing environment variables

Requirements:
- Use simple beginner-friendly language.
- Include descriptive notes.
- Include easy examples.
- Include one ASCII diagram showing a containerized AI application with multiple services.
- Include a sample Dockerfile for a Python FastAPI embedding service.
- Include a sample multi-stage Dockerfile.
- Include pseudocode for:
  build -> tag -> push to registry -> deploy.
- End with a short "What to remember today" recap.

Python learning:
Teach:
- file handling
- reading configuration
- dictionaries

Python practice problem:
Write a Python program that reads this configuration dictionary:
{"env": "prod", "replicas": 3, "debug": False}
and prints a deployment summary.

For the Python section:
- Explain the concept.
- Show pseudocode.
- Provide a clean Python solution.
- Explain the solution step by step.
```

---

# Day 4 Prompt — Kubernetes Fundamentals for AI Workloads

```text
Act as a beginner-friendly AI Infrastructure mentor.

Create Day 4 study notes for an AI Infra Engineer role.

Topic:
Kubernetes fundamentals for AI infrastructure and GenAI workloads.

Start with a short revision of Days 1 to 3:
- RAG architecture
- production Python services
- Docker image vs container
- microservices

Cover these topics:
1. What is Kubernetes?
2. Why Kubernetes is used for AI and GenAI platforms.
3. Kubernetes cluster basics:
   - control plane
   - worker nodes
   - kubelet
   - scheduler
   - API server
4. Pod, ReplicaSet, and Deployment.
5. StatefulSet and why it matters for databases like Milvus.
6. DaemonSet basics.
7. Kubernetes Service types:
   - ClusterIP
   - NodePort
   - LoadBalancer
8. Ingress basics.
9. ConfigMap and Secret.
10. Volumes, PersistentVolume, and PersistentVolumeClaim.
11. Namespace.
12. Resource requests and limits.
13. Readiness probe and liveness probe.
14. Horizontal Pod Autoscaler.
15. Kubernetes scheduling basics.
16. Example:
   deploying an embedding API service on Kubernetes.
17. Example:
   why vector databases need persistent storage.

Requirements:
- Use simple beginner-friendly language.
- Include descriptive notes.
- Include easy examples.
- Include one ASCII diagram of a Kubernetes cluster running an AI application.
- Include sample Kubernetes YAML for:
   - Deployment
   - Service
   - ConfigMap
   - PVC
- Include pseudocode explaining how Kubernetes restarts a failed pod.
- Include pseudocode explaining basic autoscaling.
- End with a short "What to remember today" recap.

Python learning:
Teach object-oriented programming basics:
- class
- object
- constructor
- methods
- instance variables

Python practice problem:
Create a Python class called Server with attributes name, cpu, and memory. Add a method called is_high_memory that returns True if memory is greater than 64 GB.

For the Python section:
- Explain the concept.
- Show pseudocode.
- Provide a clean Python solution.
- Explain the solution step by step.
```

---

# Day 5 Prompt — Helm, CI/CD, IaC, and Cloud-Native Deployment

```text
Act as a beginner-friendly AI Infrastructure mentor.

Create Day 5 study notes for an AI Infra Engineer role.

Topic:
Helm charts, CI/CD pipelines, Infrastructure as Code, and cloud-native deployment.

Start with a short revision of Days 2 to 4:
- production Python
- Docker
- Kubernetes Deployment, Service, ConfigMap, Secret, and PVC

Cover these topics:
1. What is Helm?
2. Why Helm is useful for Kubernetes deployments.
3. Helm chart structure:
   - Chart.yaml
   - values.yaml
   - templates/
4. Helm values for different environments:
   - dev
   - test
   - staging
   - production
5. CI/CD basics.
6. Typical CI/CD pipeline for an AI service:
   - code commit
   - unit tests
   - linting
   - security scan
   - Docker build
   - image push
   - Helm deploy
   - smoke test
7. Deployment strategies:
   - rolling update
   - blue-green
   - canary
8. Rollback basics.
9. Secrets management in CI/CD.
10. Infrastructure as Code basics:
   - Terraform
   - Kubernetes manifests
   - Helm values as configuration
11. Cloud-native deployment practices.
12. Managing environment variables safely.
13. Example:
   CI/CD pipeline for an embedding API service.
14. Example:
   CI/CD pipeline for a RAG ingestion worker.

Requirements:
- Use simple beginner-friendly language.
- Include descriptive notes.
- Include easy examples.
- Include one ASCII diagram of a CI/CD pipeline.
- Include sample Helm values.yaml.
- Include a simple Helm Deployment template.
- Include pseudocode for a CI/CD deployment workflow.
- End with a short "What to remember today" recap.

Python learning:
Teach:
- JSON handling
- validation
- clean function design

Python practice problem:
Write a Python function validate_config(config) that checks whether a config dictionary contains:
- env
- replicas
- image

Return True if valid. Otherwise return False and print the missing keys.

For the Python section:
- Explain the concept.
- Show pseudocode.
- Provide a clean Python solution.
- Explain the solution step by step.
```

---

# Day 6 Prompt — Embeddings, LLM APIs, and Batch Pipelines

```text
Act as a beginner-friendly AI Infrastructure mentor.

Create Day 6 study notes for an AI Infra Engineer role.

Topic:
Embeddings, LLM APIs, and production embedding pipelines.

Start with a short revision of Days 3 to 5:
- Docker
- Kubernetes
- Helm
- CI/CD

Cover these topics:
1. What are embeddings?
2. Why text is converted into vectors.
3. Difference between LLM and embedding model.
4. OpenAI embeddings overview.
5. Hugging Face embedding models overview.
6. Cohere embeddings overview.
7. Local embedding model vs API-based embedding model.
8. Embedding pipeline steps:
   - collect documents
   - clean text
   - split into chunks
   - generate embeddings
   - store vectors
   - store metadata
9. Chunking strategies:
   - fixed-size chunking
   - overlapping chunking
   - semantic chunking
10. Batch processing.
11. Rate limits.
12. Retry and exponential backoff.
13. Idempotency in embedding pipelines.
14. Handling failed jobs.
15. Model versioning.
16. Embedding versioning.
17. Cost and latency considerations.
18. Example:
   embedding internal engineering PDFs.

Requirements:
- Use simple beginner-friendly language.
- Include descriptive notes.
- Include easy examples.
- Include one ASCII diagram of an embedding pipeline.
- Include pseudocode for generating embeddings in batches.
- Include pseudocode for retry and exponential backoff.
- Include pseudocode for idempotent embedding generation.
- End with a short "What to remember today" recap.

Python learning:
Teach:
- batching
- list slicing
- retry logic

Python practice problem:
Write a Python function that takes a list of 20 document names and splits them into batches of size 5.

For the Python section:
- Explain the concept.
- Show pseudocode.
- Provide a clean Python solution.
- Explain the solution step by step.
```

---

# Day 7 Prompt — Vector Databases and Milvus

```text
Act as a beginner-friendly AI Infrastructure mentor.

Create Day 7 study notes for an AI Infra Engineer role.

Topic:
Vector databases with focus on Milvus deployment, schema design, and index tuning.

Start with a short revision of Days 4 to 6:
- Kubernetes
- Helm
- CI/CD
- embeddings
- batch pipelines

Cover these topics:
1. What is a vector database?
2. Why normal relational databases are not enough for semantic search.
3. What is vector similarity search?
4. Similarity metrics:
   - cosine similarity
   - dot product
   - Euclidean distance
5. What is Milvus?
6. Milvus beginner architecture:
   - collection
   - partition
   - field
   - entity
   - index
   - query node
   - data node
   - coordinator
7. Milvus production dependencies at a high level:
   - object storage such as MinIO or S3
   - message queue concept
   - metadata store concept
8. Milvus deployment options:
   - standalone
   - distributed
   - Kubernetes deployment
   - Helm deployment
9. Schema design:
   - primary key
   - vector field
   - text field
   - metadata fields
10. Metadata filtering.
11. Index tuning:
   - HNSW
   - IVF-FLAT
12. HNSW vs IVF-FLAT comparison.
13. Trade-off between:
   - recall
   - latency
   - memory
   - cost
14. Top-k search.
15. Backup and restore basics.
16. Monitoring Milvus.
17. Common production issues:
   - slow queries
   - high memory usage
   - wrong index
   - missing metadata
   - poor chunking
   - dimension mismatch

Requirements:
- Use simple beginner-friendly language.
- Include descriptive notes.
- Include easy examples.
- Include one ASCII diagram of Milvus inside a RAG architecture.
- Include one ASCII diagram showing Milvus components at a beginner level.
- Include one ASCII diagram comparing HNSW and IVF-FLAT conceptually.
- Include pseudocode for creating a collection.
- Include pseudocode for inserting vectors.
- Include pseudocode for top-k vector search with metadata filtering.
- End with a short "What to remember today" recap.

Python learning:
Teach:
- sorting
- top-k retrieval
- lists of dictionaries

Python practice problem:
Given a list of documents with scores, return the top 3 documents with the highest scores.

Example:
[
  {"doc": "A", "score": 0.91},
  {"doc": "B", "score": 0.75},
  {"doc": "C", "score": 0.98},
  {"doc": "D", "score": 0.80}
]

For the Python section:
- Explain the concept.
- Show pseudocode.
- Provide a clean Python solution.
- Explain the solution step by step.
```

---

# Day 8 Prompt — Production RAG, Object Storage, and Access Control

```text
Act as a beginner-friendly AI Infrastructure mentor.

Create Day 8 study notes for an AI Infra Engineer role.

Topic:
Production RAG pipelines, object storage integration, metadata, and access control.

Start with a short revision of Days 5 to 7:
- CI/CD
- embeddings
- vector databases
- Milvus schema
- HNSW and IVF-FLAT

Cover these topics:
1. What is a production RAG pipeline?
2. Difference between:
   - ingestion pipeline
   - query pipeline
3. Document ingestion:
   - PDFs
   - Word documents
   - web pages
   - structured data
4. Text extraction and cleaning.
5. Chunking and embedding.
6. Vector storage in Milvus.
7. Object storage:
   - AWS S3
   - MinIO
   - Google Cloud Storage
8. Why object storage is used in AI systems.
9. Storing original documents vs storing extracted chunks.
10. Metadata strategy:
   - document ID
   - source
   - timestamp
   - user access level
   - department
   - domain
   - version
11. Access control basics.
12. Why permission-aware retrieval matters.
13. RAG query flow:
   - receive question
   - authenticate user
   - embed question
   - apply metadata filter
   - retrieve chunks
   - rerank
   - call LLM
   - return grounded answer
14. Common RAG failure cases:
   - hallucination
   - stale documents
   - bad retrieval
   - missing metadata
   - poor chunking
   - no access filtering
15. Production RAG checklist.

Requirements:
- Use simple beginner-friendly language.
- Include descriptive notes.
- Include easy examples.
- Include one ASCII diagram of ingestion and query pipelines.
- Include one ASCII diagram showing object storage plus Milvus.
- Include pseudocode for document upload to object storage.
- Include pseudocode for chunking, embedding, and Milvus insert.
- Include pseudocode for permission-aware RAG retrieval.
- End with a short "What to remember today" recap.

Python learning:
Teach:
- classes
- serialization
- dictionaries
- metadata handling

Python practice problem:
Create a Python class called DocumentChunk with fields:
- chunk_id
- text
- source_file
- metadata

Add a method to_dict() that returns the object as a dictionary.

For the Python section:
- Explain the concept.
- Show pseudocode.
- Provide a clean Python solution.
- Explain the solution step by step.
```

---

# Day 9 Prompt — Hybrid Search, Metadata Filtering, and Vector DB Alternatives

```text
Act as a beginner-friendly AI Infrastructure mentor.

Create Day 9 study notes for an AI Infra Engineer role.

Topic:
Hybrid search, metadata filtering, reranking, index tuning, and vector database alternatives.

Start with a short revision of Days 6 to 8:
- embeddings
- Milvus
- RAG ingestion pipeline
- RAG query pipeline
- object storage
- metadata

Cover these topics:
1. What is keyword search?
2. What is vector search?
3. What is hybrid search?
4. Why hybrid search is useful in enterprise RAG.
5. Metadata filtering:
   - department
   - document type
   - access level
   - date
   - source system
   - project
6. Search ranking basics.
7. Reranking basics.
8. Recall vs precision.
9. Latency vs quality.
10. Index tuning review:
   - recall
   - latency
   - memory
   - throughput
11. Vector database alternatives:
   - Qdrant
   - Pinecone
   - Weaviate
   - PGVector
   - Chroma
12. When to choose Milvus.
13. When to choose Qdrant.
14. When to choose Pinecone.
15. When to choose Weaviate.
16. When to choose PGVector.
17. When to choose Chroma.
18. Production search optimization checklist.
19. Common search problems and fixes.

Requirements:
- Use simple beginner-friendly language.
- Include descriptive notes.
- Include easy examples.
- Include one ASCII diagram of hybrid search.
- Include a comparison table of:
  Milvus, Qdrant, Pinecone, Weaviate, PGVector, and Chroma.
- Include pseudocode for hybrid search:
  keyword results + vector results + metadata filter + reranking.
- Include pseudocode for score normalization.
- End with a short "What to remember today" recap.

Python learning:
Teach:
- filtering
- sorting
- ranking
- score combination

Python practice problem:
Given a list of documents with title, vector_score, keyword_score, and department, filter only documents from department="engineering", calculate:

final_score = 0.7 * vector_score + 0.3 * keyword_score

Then return documents sorted by final_score descending.

For the Python section:
- Explain the concept.
- Show pseudocode.
- Provide a clean Python solution.
- Explain the solution step by step.
```

---

# Day 10 Prompt — LangChain, LlamaIndex, Custom Pipelines, and AI Agents

```text
Act as a beginner-friendly AI Infrastructure mentor.

Create Day 10 study notes for an AI Infra Engineer role.

Topic:
LLM orchestration with LangChain, LlamaIndex, custom pipelines, and multi-agent platforms.

Start with a short revision of Days 7 to 9:
- Milvus
- vector search
- RAG
- hybrid search
- metadata filtering
- reranking

Cover these topics:
1. What is LLM orchestration?
2. Why orchestration frameworks are useful.
3. LangChain overview.
4. LlamaIndex overview.
5. Custom pipeline vs framework-based pipeline.
6. Prompt templates.
7. Chains.
8. Tools.
9. Agents.
10. Multi-agent workflow basics.
11. Agent memory.
12. Tool calling.
13. Retrieval tools.
14. Guardrails.
15. Prompt injection risks.
16. Retry and fallback strategies.
17. Human-in-the-loop review.
18. Production concerns:
   - latency
   - cost
   - security
   - observability
   - tracing
   - retries
   - rate limits
19. Example:
   agent that searches internal documents and calls an equipment-status API.

Requirements:
- Use simple beginner-friendly language.
- Include descriptive notes.
- Include easy examples.
- Include one ASCII diagram of a LangChain or LlamaIndex RAG pipeline.
- Include one ASCII diagram of a simple multi-agent system.
- Include pseudocode for an AI agent that decides whether to search documents or call a tool.
- Include pseudocode for fallback when an LLM API fails.
- End with a short "What to remember today" recap.

Python learning:
Teach:
- decorators
- generators
- basic tracing idea

Python practice problem:
Write a Python decorator called log_call that prints the function name before the function runs. Use it on a function called generate_embedding(text).

For the Python section:
- Explain the concept.
- Show pseudocode.
- Provide a clean Python solution.
- Explain the solution step by step.
```

---

# Day 11 Prompt — GPU Scheduling, Compute, and Inference Optimization

```text
Act as a beginner-friendly AI Infrastructure mentor.

Create Day 11 study notes for an AI Infra Engineer role.

Topic:
Compute, GPU scheduling, resource optimization, and inference acceleration.

Start with a short revision of Days 8 to 10:
- production RAG
- object storage
- hybrid search
- LangChain
- LlamaIndex
- agents

Cover these topics:
1. What is AI inference?
2. Difference between training and inference.
3. CPU vs GPU.
4. Why GPUs are used for LLM and embedding inference.
5. Kubernetes resource requests and limits.
6. GPU scheduling in Kubernetes.
7. Node selectors.
8. Taints and tolerations.
9. GPU node pools.
10. Autoscaling for inference services.
11. Batch inference vs real-time inference.
12. Model serving basics.
13. Inference optimization:
   - batching
   - caching
   - quantization
   - model warmup
   - model loading optimization
   - parallelism
14. Latency vs throughput.
15. Cost optimization.
16. Queue-based inference architecture.
17. Common inference bottlenecks:
   - cold starts
   - GPU underutilization
   - memory limits
   - slow preprocessing
   - network latency
18. Example:
   scaling an embedding model service on Kubernetes.

Requirements:
- Use simple beginner-friendly language.
- Include descriptive notes.
- Include easy examples.
- Include one ASCII diagram of GPU-based inference on Kubernetes.
- Include one ASCII diagram of request batching.
- Include sample Kubernetes YAML showing GPU resource request.
- Include pseudocode for a request batching system.
- Include pseudocode for autoscaling based on queue length or GPU usage.
- End with a short "What to remember today" recap.

Python learning:
Teach:
- concurrency basics
- ThreadPoolExecutor
- parallel processing

Python practice problem:
Write a Python program using concurrent.futures.ThreadPoolExecutor to process a list of text chunks in parallel. Simulate processing by converting each chunk to uppercase.

For the Python section:
- Explain the concept.
- Show pseudocode.
- Provide a clean Python solution.
- Explain the solution step by step.
```

---

# Day 12 Prompt — Observability, Governance, SRE, Dataiku DSS, and Capstone

```text
Act as a beginner-friendly AI Infrastructure mentor.

Create Day 12 study notes for an AI Infra Engineer role.

Topic:
AI observability, LLM evaluation, governance, SRE practices, Dataiku DSS, Oil & Gas context, and final capstone.

Start with a short revision of Days 1 to 11:
- AI infrastructure
- GenAI
- RAG
- production Python
- Docker
- Kubernetes
- Helm
- CI/CD
- IaC
- embeddings
- Milvus
- vector database alternatives
- object storage
- hybrid search
- LangChain
- LlamaIndex
- AI agents
- GPU scheduling
- inference optimization

Cover these topics:
1. What is observability?
2. Difference between logs, metrics, and traces.
3. Why AI observability is different from normal application monitoring.
4. What to monitor in RAG systems:
   - latency
   - retrieval quality
   - hallucination risk
   - token usage
   - cost
   - errors
   - user feedback
5. LLM evaluation basics:
   - relevance
   - faithfulness
   - groundedness
   - answer correctness
6. Governance basics:
   - data privacy
   - access control
   - audit logs
   - model versioning
   - prompt versioning
   - embedding versioning
7. Tracing an LLM request.
8. Monitoring tools overview:
   - Prometheus
   - Grafana
   - OpenTelemetry
   - application logs
9. SRE basics:
   - SLA
   - SLO
   - SLI
   - error budget
   - incident response
   - postmortem
10. Production readiness checklist:
   - security
   - scalability
   - reliability
   - observability
   - cost
   - backup
   - restore
   - disaster recovery
11. Dataiku DSS high-level overview.
12. Where Dataiku DSS fits in enterprise AI and ML workflows.
13. Oil and Gas AI use cases:
   - document search
   - maintenance knowledge assistant
   - well data analysis assistant
   - equipment troubleshooting chatbot
   - safety procedure assistant
14. How to explain AI infrastructure to a non-technical stakeholder.
15. Final capstone:
   Design an enterprise RAG platform using:
   - Kubernetes
   - Docker
   - Helm
   - Milvus
   - embedding service
   - object storage
   - OpenAI or Hugging Face embeddings
   - LLM API
   - LangChain or custom orchestration
   - monitoring
   - CI/CD
   - access control

Requirements:
- Use simple beginner-friendly language.
- Include descriptive notes.
- Include easy examples.
- Include one ASCII diagram showing logs, metrics, and traces in a RAG system.
- Include one large ASCII architecture diagram for the final capstone.
- Include pseudocode for tracing a RAG request from API to vector database to LLM.
- Include pseudocode for calculating average latency, success rate, and error rate.
- Include pseudocode for the complete end-to-end system:
  document upload -> object storage -> chunking -> embeddings -> Milvus insert -> user query -> retrieval -> LLM answer -> monitoring.
- End with a short "What to remember today" recap.

Python learning:
Create a small Python mini-project.

Python practice problem:
Build a small in-memory RAG-style search simulation in Python.

Use:
- a list of document chunks
- fake vector_score
- fake keyword_score
- department metadata
- department filtering
- top 3 retrieval
- simple response generation by combining retrieved chunks

For the Python section:
- Explain the mini-project.
- Show pseudocode.
- Provide a clean Python solution.
- Explain the solution step by step.
```

---
