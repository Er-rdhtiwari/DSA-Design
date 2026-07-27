# Day 1 — Vanilla RAG

## 1. Core idea in simple words

**RAG** means **Retrieval-Augmented Generation**. It is a design pattern in which an application first finds relevant business information and then gives that information to a large language model, or **LLM**, so the model can answer.

Think of it as an open-book exam:

1. The user asks a question.
2. The system searches trusted documents for useful passages.
3. The LLM reads those passages.
4. The LLM writes an answer based on them and points to its sources.

RAG solves a practical problem: an LLM may not know private, recent, tenant-specific, or frequently changing information. A Disney-like company may have current campaign rules, internal content policies, and partner agreements that were never part of the model’s training. RAG can supply those facts at request time without retraining the model.

“Vanilla” RAG is the simplest useful version: ingest documents, split them into chunks, create embeddings, store them in a vector index, retrieve the best chunks, place them in a prompt, and ask the model to answer.

## 2. Foundational concepts

### Why an LLM alone is not enough

An **LLM** is a model trained to predict and generate language. Its built-in knowledge has four important limits:

- **Knowledge cutoff:** it does not automatically know facts created after training.
- **Private-data gap:** it has not seen most internal company data.
- **No guaranteed evidence:** it can produce a fluent answer without a reliable source.
- **Tenant and permission needs:** business answers must respect the current user’s access, not simply use everything the model may know.

An LLM can also **hallucinate**, meaning it can state unsupported or incorrect information as if it were true. RAG reduces this risk by providing evidence, but does not eliminate it. The model can still ignore, misread, or combine evidence incorrectly.

### Four different ways to influence a model

| Method | Simple meaning | Best used for | Important limit |
| --- | --- | --- | --- |
| **Pretraining knowledge** | Knowledge learned during the model’s original large-scale training | General language and broad facts | Usually fixed, not private, and may be stale |
| **Prompting** | Instructions and text sent with the current request | Telling the model what task and format to follow | The prompt can only use information placed inside it |
| **Fine-tuning** | Additional training that changes model behavior | Stable style, format, or repeated behavior | Usually a poor database for frequently changing facts |
| **Retrieval** | Searching an external knowledge source at request time | Fresh, private, attributable facts | Quality depends on ingestion and search |

These methods complement one another. For example, a fine-tuned model can follow a company answer style, while retrieval supplies current policy facts and a prompt tells it to cite only those facts.

### The basic RAG vocabulary

- A **document** is a source item such as a PDF, web page, policy, campaign brief, or database record.
- **Parsing** converts a document’s original format into usable text and structure.
- A **chunk** is a smaller passage cut from a document. Searching passages is usually more precise than searching an entire long PDF.
- **Metadata** is descriptive information stored beside a chunk, such as `tenant_id`, title, source URL, policy region, version, access group, and update time.
- An **embedding** is a list of numbers that represents the meaning of text. Texts with related meanings tend to have embeddings that are close together.
- A **vector index** is a data structure optimized for finding nearby embeddings quickly.
- **Vector search** compares the query embedding with stored chunk embeddings to find semantically similar chunks.
- **Retrieval** is the full act of selecting evidence for a request. It may use vector search, keyword search, filters, or a combination.
- **Top-k** means returning the `k` highest-ranked search results. For example, top-5 returns five chunks.
- **Reranking** means taking an initial candidate set and using a more accurate scoring method to reorder it.
- **Grounding** means tying an answer to supplied evidence instead of relying only on the model’s memory.
- A **context window** is the maximum amount of input and output text a model can handle in one request.
- **Context assembly** is the process of selecting, ordering, labeling, and fitting retrieved chunks into that window.
- A **citation** identifies the source that supports a claim.

### Keyword, semantic, and hybrid search

**Keyword search** looks for matching words or lexical variations. It is strong for exact names, IDs, codes, and rare phrases. A search for `CMP-1042` should favor exact matching.

**Semantic search** compares embeddings, so it can match similar meaning even when the words differ. “Who can approve a regional campaign?” may match a passage saying “market leads authorize local promotions.”

**Hybrid search** combines keyword and semantic results. It is often safer in production because enterprise questions contain both exact identifiers and natural-language intent.

### Recall and precision

**Recall** asks: “Of all useful chunks that exist, how many did retrieval find?”

`recall = relevant chunks retrieved / all relevant chunks available`

**Precision** asks: “Of all chunks retrieved, how many were actually useful?”

`precision = relevant chunks retrieved / all chunks retrieved`

Low recall means the answer may miss required facts. Low precision means irrelevant chunks pollute the prompt. Increasing top-k may improve recall but often reduces precision, costs more tokens, and increases latency. A production system measures both instead of assuming that “more context” is better.

## 3. End-to-end Vanilla RAG flow

RAG has two paths:

- The **offline ingestion path** prepares searchable knowledge.
- The **online query path** answers a user request.

### Offline ingestion path

#### Step 1: Receive and identify data

The ingestion service accepts a document and records its source, owner, tenant, version, security class, and update time. It should assign stable IDs so a later update can replace the correct version.

#### Step 2: Parse the document

A parser extracts text, headings, tables, page numbers, and other useful structure from formats such as PDF or HTML. Parsing is not merely “read every character.” Headers, footers, navigation text, repeated disclaimers, and scanned images can produce noise. A scanned PDF may require optical character recognition.

#### Step 3: Clean and normalize

**Cleaning** removes content that should not be searched, such as repeated page headers. **Normalization** makes equivalent forms consistent, such as whitespace or date formats. The pipeline should preserve meaningful structure and source locations; aggressive cleaning can destroy table relationships or section boundaries.

#### Step 4: Split text into chunks

Chunking turns long text into retrieval units. Common approaches include:

- fixed token or character windows;
- paragraph- or heading-aware chunks;
- structure-aware chunks for tables, FAQs, or code;
- small child chunks for search with larger parent sections for context.

**Chunk size** creates a trade-off:

- Very small chunks are focused but may lose the meaning around a sentence.
- Very large chunks keep context but may contain several unrelated topics and cost more tokens.

**Overlap** repeats some boundary text in adjacent chunks so an idea split across a boundary can still be found. Too little overlap can break an idea; too much creates duplicates, raises storage, and may crowd the final prompt with repeated text.

There is no universal size. Measure it against real questions and document types.

#### Step 5: Generate embeddings

An embedding model converts each searchable chunk into a vector. The ingestion and query paths must use compatible embedding logic. Record the embedding model and version because changing the model can require re-embedding the collection.

Model selection balances:

- domain and language quality;
- vector dimensions and storage;
- inference cost and latency;
- privacy and deployment constraints;
- long-text support.

#### Step 6: Build the vector index

The system places chunk vectors in a vector index so nearest-neighbor lookup is fast. An exact comparison against every vector becomes expensive at scale, so many indexes use approximate search: much faster, with a small chance of missing a neighbor.

Basic tuning choices trade memory, build time, query speed, and recall. Index settings must therefore be validated on the actual collection and traffic pattern.

#### Step 7: Store text and metadata

Each vector must connect back to:

- the chunk text;
- document and chunk IDs;
- title and source location;
- tenant and access-control fields;
- version, validity, and timestamps;
- document type, region, language, or business tags.

Metadata is part of correctness. Without it, the system may retrieve the right words from the wrong tenant, an expired policy, or a region the user cannot access.

### Online query path

#### Step 8: Accept and protect the request

The backend authenticates the user, determines tenant and access scope, validates the question, and creates a request ID for tracing. Access rules should become mandatory retrieval filters, not optional prompt instructions.

#### Step 9: Prepare the query

The simplest system embeds the original question. A more tuned system may normalize it or rewrite conversational wording into a self-contained search query. Rewriting should preserve identifiers and intent.

#### Step 10: Retrieve top-k candidates

The retriever performs semantic, keyword, or hybrid search and applies metadata and permission filters. It returns top-k candidate chunks with scores and source information.

`k` is a tunable value, not a fixed truth. Too small can omit evidence; too large can add noise and cost.

#### Step 11: Rerank

A fast first-stage search may retrieve, for example, 30 candidates. A slower but more accurate reranker can read the question and each candidate together, then retain the best 5. This often improves precision without searching every stored chunk with the expensive model.

#### Step 12: Assemble context

The context builder:

- removes exact or near duplicates;
- enforces token and source budgets;
- preserves useful neighboring text;
- orders passages clearly;
- labels each passage with a source ID;
- avoids mixing conflicting versions without explanation.

The context should contain enough evidence to answer, not every passage that looks vaguely related.

#### Step 13: Construct the RAG prompt

A good prompt separates:

- **instruction:** answer using the supplied sources;
- **user question:** the original request;
- **evidence:** clearly delimited and source-labeled passages;
- **behavior when evidence is weak:** say that the information is unavailable or ask for clarification;
- **output contract:** answer structure and citation format.

Retrieved text is untrusted data. The prompt should say that instructions found inside documents must not override system rules.

#### Step 14: Generate the answer

The LLM combines the question and evidence into a useful response. Sampling settings can be conservative for factual business answers. If an output schema is required, validate it after generation rather than trusting the model blindly.

#### Step 15: Produce citation-aware output

The model should attach source IDs to claims. The backend should verify that every cited ID was actually provided and translate it into a safe title, page, or link. Citation presence alone does not prove support, so evaluation must also check whether the cited passage entails the claim.

#### Step 16: Capture feedback and telemetry

The system records safe operational signals such as:

- request and trace IDs;
- retrieval and reranking latency;
- candidate IDs and scores;
- selected context size;
- model, prompt, index, and embedding versions;
- input/output token counts and cost;
- citation and refusal behavior;
- explicit user feedback.

The feedback loop uses evaluated failures to improve parsing, chunking, retrieval, prompts, or source content. Raw user feedback should be reviewed before becoming training or evaluation data.

## 4. Inter-relation between all stages

The final answer is the end of a dependency chain:

`source → parse → clean → chunk → embed → index → retrieve → rerank → assemble → prompt → generate → cite → evaluate`

### Chunking affects embeddings

An embedding summarizes the chunk it receives. If a chunk contains three unrelated policy sections, its vector becomes a blurred summary. If it contains a sentence without its subject or heading, the vector may be precise but meaningless. Structure-aware chunking gives the embedding a coherent unit.

### Embeddings affect retrieval

An embedding model decides which meanings appear close. A model weak in company vocabulary, languages, or short identifiers may miss correct chunks. The query and corpus must use the same compatible embedding space.

### Retrieval affects answer quality

The generator cannot reliably use evidence it never receives. Missing evidence creates an upper bound on factual answer quality. Irrelevant or conflicting evidence makes reasoning harder and can cause confident errors.

It is useful to diagnose answers in layers:

1. Did the correct source exist and parse correctly?
2. Was a useful chunk created?
3. Did retrieval find it?
4. Did reranking keep it?
5. Did context assembly include it?
6. Did the model use and cite it correctly?

This separates a retrieval failure from a generation failure.

### Context size affects cost, latency, and quality

More context consumes more input tokens, increases model latency and cost, and can distract the model. Too little context loses evidence. Optimize for the smallest sufficient context, measured with real questions.

### Poor ingestion can break everything downstream

If a PDF table is flattened incorrectly, no embedding model or prompt can recover the lost row relationships. If stale and duplicate versions are indexed, retrieval may return both. Production quality begins with document ownership, parsing tests, versioning, and freshness—not only model choice.

## 5. Production-grade challenges

| Challenge | What can go wrong | What to observe or protect |
| --- | --- | --- |
| Bad chunking | Ideas are split or unrelated ideas are mixed | Retrieval quality by chunk strategy and document type |
| Missing metadata | Wrong tenant, region, version, or policy can appear | Required metadata validation and filter tests |
| Stale data | Expired information answers current questions | Source freshness lag, validity windows, deletion/update success |
| Duplicate documents | Repeated evidence crowds out other facts | Content hashes, canonical IDs, near-duplicate rate |
| Poor parsing | Tables, headings, or scanned text become corrupt | Parse success plus sampled semantic quality checks |
| Low recall | Required evidence never reaches the model | Labeled-query recall@k and “no evidence” cases |
| Low precision | Irrelevant passages pollute context | precision@k, reranker lift, context-usefulness grading |
| Wrong top-k | Too few misses evidence; too many add noise | Quality, tokens, and latency across candidate values |
| Context pollution | Duplicated, conflicting, or malicious text distracts the model | Deduplication, version policy, injection scans |
| Hallucination after retrieval | The model ignores evidence or invents a bridge between facts | Groundedness, citation entailment, calibrated refusal |
| Slow retrieval | Index, filters, or remote calls miss latency targets | Per-stage p50/p95/p99 latency and timeout rate |
| High token cost | Excess context and verbose answers raise spending | Tokens and cost per request, tenant, and use case |
| Weak tenant isolation | One customer sees another’s data | Server-side tenant filters, authorization tests, separate indexes where risk requires |
| Security/privacy gaps | Sensitive content leaks into prompts, logs, or providers | Data classification, encryption, redaction, retention, provider policy |
| Monitoring blind spots | The service is “up” while answers are bad | System metrics plus retrieval and answer-quality signals |
| Evaluation blind spots | A few demos hide broad failure modes | Versioned offline sets, online feedback, slice and regression analysis |

Reliability also requires bounded timeouts, retries with jitter where safe, circuit breakers for dependencies, graceful “evidence unavailable” responses, and a rollback path for prompt, index, embedding, or model changes.

## 6. Optimization strategies

### Improve evidence quality first

- Use heading-, paragraph-, or structure-aware chunking and evaluate per document type.
- Add small-to-large retrieval: search small focused chunks, then return a larger parent section when helpful.
- Validate metadata on ingestion and enforce tenant, access, validity, language, and region filters.
- Deduplicate by stable IDs and content hashes.
- Combine keyword and vector search when questions mix exact terms and meaning.
- Rewrite vague follow-up questions into standalone search queries while preserving names and IDs.
- Retrieve a wider cheap candidate set and rerank it with a more accurate model.
- Compress context by removing repeated or non-answering sentences, while keeping source links.

### Tune the online path

- Choose top-k through evaluation rather than habit; it may vary by question class.
- Use prompts that clearly delimit evidence, require citations, handle missing evidence, and resist instructions inside retrieved text.
- Cache retrieval only when the cache key includes query, tenant, permissions, filters, and index version. Short time-to-live values reduce stale results.
- Parallelize independent keyword and vector searches, then merge results.
- Set per-stage latency budgets and fall back safely if reranking or a secondary search times out.

### Tune models and indexes

- Select embedding models using domain recall, language support, cost, latency, dimensions, and privacy requirements.
- Tune vector-index search depth for the required speed/recall balance.
- Batch embeddings during ingestion and rate-limit background work so it does not harm online traffic.
- Version embeddings and indexes. Build and evaluate a new index before switching traffic.

### Keep data fresh

- Prefer event-driven updates when a source changes.
- Run periodic reconciliation to catch missed events.
- Use source version, `updated_at`, and validity fields.
- Propagate deletions, including cached results.
- Measure freshness lag from source update to searchable update.

### Balance quality, cost, and latency

Changing one part moves the others:

- Larger candidate sets can raise recall but increase reranking latency.
- More final context may add evidence but raises tokens and may lower focus.
- A larger model may reason better but costs more and responds more slowly.

Define targets first, such as answer-quality threshold, p95 latency, and cost per successful answer. Optimize against all three, not a single metric.

### When vanilla RAG is enough

Use vanilla RAG when requests are mostly one-step questions, one retrieval pass is sufficient, data formats are manageable, and simple filters plus reranking reach quality targets.

Consider advanced RAG when questions require decomposition, multiple sources or hops, tables or graphs, iterative retrieval, tool use, personalized authorization logic, or stateful workflows. Add complexity only after evaluation identifies a concrete vanilla-RAG failure.

## 7. Easy real-world example

Imagine an internal assistant for content and campaign teams.

**Question:** “Can campaign `CMP-1042` use this character artwork in an India partner promotion, and which policy supports the answer?”

The offline path:

1. Ingest approved campaign briefs, regional brand policies, and rights documents.
2. Parse headings, tables, pages, and campaign IDs.
3. Remove repeated footers but retain policy version and page information.
4. Chunk by section so artwork rules stay with their exceptions.
5. Embed each chunk and index it with `tenant_id`, `region`, `campaign_id`, `status`, access group, and validity dates.

The online path:

1. Authenticate the employee and derive allowed content groups.
2. Use hybrid search: the exact campaign ID benefits from keywords; the permission question benefits from semantic search.
3. Filter to the employee’s tenant, India region, current versions, and authorized sources.
4. Retrieve candidates, rerank them, remove duplicates, and select a small evidence set.
5. Ask the LLM to answer only from that evidence and cite each important statement.
6. If the rights document is missing or conflicting, return “I cannot confirm this from the approved sources” and route the issue to the content-rights owner.
7. Log stage latency, versions, citations, and feedback without placing restricted text in unsafe logs.

This example shows why RAG is more than a vector database: identity, versions, parsing, filters, citations, fallbacks, and monitoring are all part of the answer’s correctness.

## 8. Staff-level interview angle

### A concise interview explanation

> RAG is a retrieval design pattern that grounds an LLM in current, authorized evidence. I would separate offline ingestion from the online query path. Ingestion parses, versions, chunks, embeds, and indexes documents with access metadata. The query path authenticates the caller, performs filtered hybrid retrieval, reranks and assembles a small evidence set, then asks the model for a cited answer. I would measure retrieval recall and precision separately from grounded answer quality, and design for freshness, tenant isolation, latency, cost, and safe failure.

### How to discuss failures and trade-offs

Do not jump directly to a bigger model. Walk the chain:

- Is the source present, current, and authorized?
- Did parsing and chunking preserve the answer?
- Did retrieval find it and reranking retain it?
- Was context sufficient but not noisy?
- Did the model follow the evidence and cite it?

Then explain trade-offs with measurable choices: top-k versus precision and tokens, approximate-index speed versus recall, richer context versus latency, shared-index efficiency versus isolation risk, and cache speed versus freshness.

### What a Staff AI Engineer should own

A Staff AI Engineer should define the system’s contracts and quality bar, not only implement prompts. Ownership includes:

- architecture and clear service boundaries;
- source onboarding, data quality, lineage, freshness, and deletion;
- identity, authorization, tenant isolation, privacy, and threat modeling;
- retrieval and generation evaluation datasets and release gates;
- SLOs, capacity, cost budgets, telemetry, incident response, and rollback;
- versioning across parsers, chunkers, embeddings, indexes, prompts, and models;
- alignment among data owners, platform teams, security, legal, and product;
- a roadmap that adds advanced RAG only when measured failures justify it.

### Fit in ad platforms and enterprise AI products

In an AI-powered ad platform, RAG can ground recommendations in campaign constraints, inventory rules, audience policies, approved assets, and current performance definitions. In an enterprise product, it can answer over internal policies or operational knowledge.

The critical production principle is the same: retrieve only evidence the current caller may use, preserve its version and lineage, generate an answer that admits uncertainty, and make the full decision path observable and evaluable.

### Fast revision checklist

- RAG = retrieve trusted evidence, then generate.
- Ingestion quality sets the ceiling.
- Metadata and authorization are correctness features.
- Recall finds enough evidence; precision keeps noise out.
- Top-k, context, cost, latency, and quality are linked.
- Citations help, but must actually support claims.
- Evaluate retrieval and generation separately.
- Start with vanilla RAG; add complexity for measured reasons.
