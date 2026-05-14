# 14-Day IBM Cloud + BSS + Service Onboarding Add-on Plan

Use this after your 100-day plan:

```text
Days 101–114: IBM Cloud + BSS + Service Onboarding specialization
```

Common instruction for all 14 days:

```text
Use only public IBM Cloud concepts and public documentation-level explanations.
Do not assume or reveal IBM-internal confidential implementation details.
Where internal BSS behavior is unknown, explain the concept generically and mark it as a high-level platform pattern.
Make every explanation interview-ready, beginner-friendly, and architecture-focused.
```

---

## Day 101 — IBM Cloud Fundamentals, Account Model, IAM, Resource Groups

```text
Act as a senior IBM Cloud platform mentor preparing me for IBM Cloud backend, BSS, service onboarding, and cloud data services roles.

Today is Day 101 of my IBM Cloud add-on plan.

Topic:
IBM Cloud fundamentals, account model, IAM, resource groups, service IDs, API keys, trusted access, and resource lifecycle.

Cover in detail:
1. What IBM Cloud is.
2. IBM Cloud account model.
3. Regions, zones, and resource locations.
4. Resource groups.
5. IAM users, access groups, roles, and policies.
6. Service IDs and API keys.
7. Trusted profiles / trusted access concept at a high level.
8. Resource lifecycle: create, update, bind, access, delete.
9. IBM Cloud CLI basics.
10. How these concepts matter for backend/cloud service development.

Also cover:
- Account vs resource group vs service instance.
- Platform access vs service access.
- Human identity vs service identity.
- Least privilege IAM design.
- Common mistakes with API keys and over-permissioned access.
- How to explain IBM Cloud IAM in interviews.

Mandatory output format:
- 5-line beginner summary
- Descriptive notes in simple language
- ASCII diagram: user/account → IAM → resource group → service instance
- Pseudocode for accessing a cloud resource using service identity
- Conceptual IBM Cloud CLI command flow
- AWS comparison table: AWS account/IAM/resource model vs IBM Cloud account/IAM/resource groups
- Common mistakes
- Debugging checklist
- 10 interview questions with strong answers
- Hands-on task: map one backend service into IBM Cloud account, resource group, IAM, service ID, and API key model
```

---

## Day 102 — IBM Cloud VPC, Networking, Subnets, Security Groups, Load Balancers

```text
Act as a senior IBM Cloud networking mentor.

Today is Day 102.

Topic:
IBM Cloud VPC networking fundamentals for backend and cloud platform engineers.

Cover in detail:
1. What IBM Cloud VPC is.
2. VPC vs classic infrastructure at a high level.
3. Regions and zones in VPC design.
4. Subnets.
5. Public and private networking.
6. Security groups.
7. Network ACLs.
8. Floating IPs.
9. Load balancers.
10. Routing basics.

Also cover:
- Public endpoint vs private endpoint.
- Inbound vs outbound traffic.
- Backend service communication inside VPC.
- Connecting app tier, database tier, and worker tier.
- Common connectivity failure cases.
- How VPC design affects security and cost.
- How to debug “service not reachable” issues.

Mandatory output format:
- 5-line beginner summary
- Descriptive notes
- ASCII diagram: internet → load balancer → subnet → VSI/service → database
- Request flow explanation
- Failure cases: wrong security group, missing route, no public IP, DNS issue
- Debugging checklist
- AWS comparison: VPC, subnet, security group, NACL, load balancer
- 10 interview questions with strong answers
- Hands-on task: design VPC networking for a Go notification service, private database, and worker component
```

---

## Day 103 — VSI Deep Dive: Virtual Server Instances on IBM Cloud

```text
Act as a senior IBM Cloud infrastructure mentor.

Today is Day 103.

Topic:
IBM Cloud Virtual Server Instances for VPC in depth.

Cover in detail:
1. What VSI means.
2. VSI lifecycle: create, start, stop, reboot, delete.
3. VSI profiles: CPU, memory, storage thinking.
4. Images and custom images.
5. Boot volume and block storage basics.
6. SSH keys and secure access.
7. Cloud-init.
8. Floating IP.
9. Security groups for VSI.
10. When to use VSI instead of Kubernetes, OpenShift, Code Engine, or serverless.

Also cover:
- VSI for benchmark automation workers.
- VSI for stateful or low-level infrastructure tasks.
- VSI vs containerized app deployment.
- Operational responsibility when using VSI.
- Patching, access control, logging, and monitoring.
- Cost and capacity considerations.
- Common VSI debugging scenarios.

Mandatory output format:
- 5-line beginner summary
- Descriptive notes
- ASCII diagram: VPC → subnet → VSI → volume → security group
- Pseudocode for provisioning and using a VSI
- Conceptual IBM Cloud CLI flow
- Terraform-style resource design idea
- Common mistakes
- Debugging checklist
- AWS comparison: EC2 vs IBM Cloud VSI
- 10 interview questions with strong answers
- Hands-on task: design a VSI-based deployment for a benchmark automation worker
```

---

## Day 104 — IBM Cloud Kubernetes Service and Red Hat OpenShift on IBM Cloud

```text
Act as a senior IBM Cloud Kubernetes and OpenShift mentor.

Today is Day 104.

Topic:
IBM Cloud Kubernetes Service and Red Hat OpenShift on IBM Cloud.

Cover in detail:
1. IBM Cloud Kubernetes Service overview.
2. Red Hat OpenShift on IBM Cloud overview.
3. Kubernetes vs OpenShift.
4. Cluster, worker node, namespace, pod, deployment, service.
5. Ingress in Kubernetes.
6. Routes in OpenShift.
7. ConfigMap and Secret.
8. Container Registry integration.
9. Cluster access and IAM/RBAC at a high level.
10. When to choose IKS vs OpenShift.

Also cover:
- How this maps to my Plan 1 Kubernetes/Tekton learning.
- Deploying a Go backend service.
- Deploying a Python/FastAPI service.
- Handling environment configuration.
- Readiness/liveness probes.
- Scaling with replicas/HPA.
- Debugging failed pods and image pull issues.

Mandatory output format:
- 5-line beginner summary
- Descriptive notes
- ASCII diagram: container registry → cluster → deployment → service → ingress/route
- Kubernetes YAML concept
- OpenShift route concept
- Debugging checklist
- AWS comparison: EKS vs IBM Cloud Kubernetes Service vs Red Hat OpenShift on IBM Cloud
- 10 interview questions with strong answers
- Hands-on task: map my Go notification microservice to IKS/OpenShift deployment
```

---

## Day 105 — IBM Cloud Code Engine, Serverless Containers, Jobs, and Functions

```text
Act as a senior IBM Cloud serverless mentor.

Today is Day 105.

Topic:
IBM Cloud Code Engine for applications, containers, jobs, and event-driven workloads.

Cover in detail:
1. What IBM Cloud Code Engine is.
2. Apps vs jobs vs functions.
3. When to use Code Engine instead of VSI.
4. When to use Code Engine instead of Kubernetes/OpenShift.
5. Deploying containerized backend APIs.
6. Running batch jobs.
7. Running scheduled jobs conceptually.
8. Environment variables and secrets.
9. Scaling behavior at a high level.
10. Cost and operations trade-offs.

Also cover:
- Example: usage aggregation job.
- Example: log-processing worker.
- Example: lightweight API backend.
- Failure handling for jobs.
- Observability for Code Engine apps/jobs.
- Security concerns.
- Limits and trade-offs.

Mandatory output format:
- 5-line beginner summary
- Descriptive notes
- ASCII diagram: source/container → Code Engine app/job → IBM Cloud service
- Pseudocode for a job execution flow
- Conceptual deployment flow
- Common mistakes
- Debugging checklist
- AWS comparison: Lambda, App Runner, Fargate vs IBM Cloud Code Engine
- 10 interview questions with strong answers
- Hands-on task: design a Code Engine job for daily usage-meter aggregation
```

---

## Day 106 — IBM Cloud Data Services: Databases, Object Storage, Event Streams

```text
Act as a senior IBM Cloud data services mentor.

Today is Day 106.

Topic:
IBM Cloud data services for backend, BSS, service onboarding, and usage-metering systems.

Cover in detail:
1. IBM Cloud Databases overview.
2. PostgreSQL on IBM Cloud.
3. Db2 basics.
4. Cloudant basics.
5. IBM Cloud Object Storage.
6. IBM Event Streams.
7. Choosing SQL vs NoSQL vs object storage.
8. Kafka-compatible event streaming with Event Streams.
9. Data retention and audit logs.
10. Data model for service onboarding, usage events, and billing records.

Also cover:
- Metadata database design.
- Service instance database design.
- Usage event storage.
- Object Storage for logs/reports/exports.
- Event Streams for async usage ingestion.
- Reliability and replay thinking.
- Data security and encryption basics.

Mandatory output format:
- 5-line beginner summary
- Descriptive notes
- ASCII diagram: API → database → Object Storage → Event Streams → worker
- Data model sketch
- Event flow for usage ingestion
- Failure cases and retry strategy
- AWS comparison: RDS/DynamoDB/S3/MSK vs IBM Cloud Databases/Cloudant/Object Storage/Event Streams
- 10 interview questions with strong answers
- Hands-on task: design storage for service metadata, usage records, invoices, audit logs, and report exports
```

---

## Day 107 — IBM Cloud Toolchains, Continuous Delivery, Tekton Pipelines

```text
Act as a senior IBM Cloud DevOps, toolchain, and delivery pipeline mentor.

Today is Day 107.

Topic:
IBM Cloud Toolchains, Continuous Delivery, Tekton pipelines, and production deployment flow.

Cover in detail:
1. What IBM Cloud Toolchains are.
2. Common tool integrations: source repo, issue tracking, secrets, pipeline, deployment tools.
3. IBM Cloud Continuous Delivery overview.
4. Delivery Pipeline stages.
5. Tekton pipeline basics.
6. Build, test, scan, package, deploy flow.
7. Public workers vs private workers.
8. Deploying to Kubernetes/OpenShift.
9. Environment promotion: dev, stage, prod.
10. Rollback strategy.

Also cover:
- Quality gates.
- Image scanning concept.
- Secrets in pipeline.
- Pipeline environment properties.
- Evidence collection at a high level.
- Deployment strategies.
- How this maps to my Plan 1 Tekton learning.
- Common pipeline failures.

Mandatory output format:
- 5-line beginner summary
- Descriptive notes
- ASCII diagram: repo → toolchain → pipeline → build → test → scan → deploy → monitor
- Pipeline pseudocode
- YAML-style Tekton pipeline example conceptually
- Common mistakes
- Debugging checklist
- AWS comparison: CodePipeline/CodeBuild/CodeDeploy vs IBM Cloud Toolchains/Delivery Pipeline/Tekton
- 10 interview questions with strong answers
- Hands-on task: design one IBM Cloud pipeline for a Go backend service deployed to OpenShift or IKS
```

IBM Cloud Continuous Delivery supports Tekton pipelines, and IBM docs describe public/private workers for pipeline jobs, including private workers for jobs that need access to internal or on-prem resources. ([IBM Cloud][2])

---

## Day 108 — IBM Cloud Billing, Usage Reports, Billing Units, BSS Fundamentals

```text
Act as a senior IBM Cloud BSS and billing-platform mentor.

Today is Day 108.

Topic:
IBM Cloud billing, usage, billing units, invoices, cost tracking, and BSS fundamentals.

Cover in detail:
1. What BSS means in cloud platforms.
2. Billing vs metering vs rating vs invoicing.
3. Account-level billing.
4. Enterprise billing units.
5. Usage reports.
6. Invoices.
7. Cost allocation.
8. Subscription vs pay-as-you-go thinking.
9. Billing data flow.
10. Common billing failure cases.

Also cover:
- Customer account → billing unit relationship at a high level.
- Usage quantity vs billed amount.
- Rating and pricing concept.
- Credits, commitments, and discounts at a high level.
- Cost visibility.
- Billing reconciliation.
- Why billing correctness matters.
- How backend services generate usage records that later become customer charges.

Mandatory output format:
- 5-line beginner summary
- Descriptive notes
- ASCII diagram: resource usage → metering → rating → billing → invoice
- Pseudocode for usage-to-billing flow
- Example usage record schema
- Example invoice line item concept
- Common mistakes
- Debugging checklist
- AWS comparison: AWS Billing/Cost Explorer/Marketplace metering vs IBM Cloud billing/usage model
- 10 interview questions with strong answers
- Hands-on task: design billing flow for a usage-based GenAI API service
```

IBM Cloud docs describe usage reports and invoices through the billing and usage console, and IBM’s glossary defines a billing unit as a top-level enterprise billing entity that manages contracts, invoices, orders, and payments. ([IBM Cloud][3])

---

## Day 109 — IBM Cloud Usage Metering and Usage-Based Pricing

```text
Act as a senior usage metering and billing engineer.

Today is Day 109.

Topic:
IBM Cloud usage metering and usage-based pricing for cloud services.

Cover in detail:
1. What usage metering is.
2. Why usage records must be accurate.
3. Metering dimensions: requests, API calls, GB-hours, tokens, storage, compute-hours.
4. Usage event collection.
5. Usage aggregation.
6. Idempotency in metering.
7. Duplicate usage-event prevention.
8. Late-arriving usage.
9. Backfill and correction.
10. Auditability.

Also cover:
- Metering source of truth.
- Metering windows.
- Hourly/daily/monthly aggregation concept.
- Usage submission failure handling.
- Retry without double charging.
- Usage reconciliation.
- Usage-based pricing plan thinking.
- How metering connects to billing and customer trust.

Mandatory output format:
- 5-line beginner summary
- Descriptive notes
- ASCII diagram: service instance → usage collector → aggregator → usage metering API → billing
- Usage event schema
- Metering aggregate schema
- Pseudocode for idempotent usage submission
- Failure scenarios: duplicate event, delayed event, missing metric, wrong unit, retry storm
- Debugging checklist
- 10 interview questions with strong answers
- Hands-on task: design a metering system for a RAG/LLM service charging by tokens, storage, and API calls
```

IBM’s public overview says usage metering lets service providers submit metrics collected for resource instances, and the usage metering API docs are specifically for submitting usage metrics. ([IBM Cloud][4])

---

## Day 110 — IBM Cloud Partner Center, Catalog, Pricing Plans, Service Onboarding

```text
Act as a senior IBM Cloud service onboarding mentor.

Today is Day 110.

Topic:
IBM Cloud Partner Center, catalog entry, product metadata, pricing plans, and service onboarding workflow.

Cover in detail:
1. What IBM Cloud Partner Center is.
2. What service onboarding means.
3. IBM Cloud catalog entry.
4. Product metadata.
5. Programmatic name vs display name.
6. Product details, support details, documentation, logo, URLs.
7. Pricing plans.
8. Free, BYOL, and usage-based plan concepts.
9. Approval and validation workflow.
10. Publishing to IBM Cloud catalog.

Also cover:
- Public catalog vs private/internal visibility conceptually.
- Product support model.
- Service documentation readiness.
- SLAs/SLOs at a high level.
- Support escalation readiness.
- Pricing plan mistakes.
- Metadata mistakes.
- Catalog lifecycle: draft, validate, publish, update, retire.

Mandatory output format:
- 5-line beginner summary
- Descriptive notes
- ASCII diagram: provider → Partner Center → catalog → customer creates instance
- Checklist for service onboarding
- Example product metadata schema
- Example pricing plan schema
- Common mistakes
- Debugging checklist
- AWS comparison: AWS Marketplace/service listing vs IBM Cloud Partner Center/catalog
- 10 interview questions with strong answers
- Hands-on task: create a mock catalog onboarding plan for a notification service
```

IBM’s public service-onboarding docs explain that Partner Center is used to define product metadata and catalog information, and that Resource Controller calls the service broker to validate service type, product, plans, and region availability during create requests. ([IBM Cloud][1])

---

## Day 111 — Service Broker, Resource Controller, Provisioning, Binding, Deprovisioning

```text
Act as a senior IBM Cloud platform service engineer.

Today is Day 111.

Topic:
Service broker architecture, Resource Controller integration, provisioning lifecycle, binding, update, and deprovisioning.

Cover in detail:
1. What a service broker is.
2. Open Service Broker API concept.
3. IBM Cloud Resource Controller concept.
4. Provision service instance flow.
5. Get service instance flow.
6. Update service instance or plan flow.
7. Bind and unbind flow.
8. Deprovision flow.
9. Broker authentication and security.
10. How broker lifecycle connects to metering and billing.

Also cover:
- Service instance state machine.
- Async provisioning.
- Partial provisioning failure.
- Retry and idempotency.
- Orphan cleanup.
- Plan validation.
- Region validation.
- Entitlement validation at a high level.
- Audit logging.
- Operational runbook for broker failures.

Mandatory output format:
- 5-line beginner summary
- Descriptive notes
- ASCII diagram: IBM Cloud catalog/resource controller → service broker → provider backend
- Provisioning lifecycle sequence diagram
- Pseudocode for provision, bind, update, and deprovision handlers
- Example service instance state machine
- Failure handling: partial provision, retry, rollback, orphan cleanup
- Debugging checklist
- 10 interview questions with strong answers
- Hands-on task: design a minimal service broker for a managed notification service
```

IBM’s service broker docs state that the IBM Cloud platform interacts with service brokers to create and manage service instances and service bindings. ([IBM Cloud][5])

---

## Day 112 — IBM Cloud Security: IAM, Secrets Manager, Key Protect, Audit

```text
Act as a senior IBM Cloud security mentor.

Today is Day 112.

Topic:
IBM Cloud security controls for backend, BSS, service onboarding, and metering systems.

Cover in detail:
1. IAM roles and policies.
2. Access groups.
3. Service IDs and API keys.
4. Trusted profiles / trusted access conceptually.
5. IBM Cloud Secrets Manager.
6. IBM Key Protect.
7. Encryption at rest and in transit.
8. Activity tracking and audit events.
9. Least privilege.
10. PII-safe and billing-safe logging.

Also cover:
- Secure service broker design.
- Secure metering submission.
- API key rotation.
- Secret lifecycle management.
- Key lifecycle management.
- Separation of duties.
- Audit trails for provisioning and billing actions.
- Threat model for service onboarding.
- Threat model for metering/billing.
- Common security anti-patterns.

Mandatory output format:
- 5-line beginner summary
- Descriptive notes
- ASCII security boundary diagram
- Threat model for service onboarding and metering
- Pseudocode for secure API-key/secret usage
- Common mistakes
- Debugging checklist
- AWS comparison: IAM/KMS/Secrets Manager/CloudTrail vs IBM IAM/Key Protect/Secrets Manager/activity tracking
- 10 interview questions with strong answers
- Hands-on task: create a security checklist for billing and usage metering service
```

IBM’s security documentation describes Secrets Manager as a service for storing and managing API keys, credentials, certificates, and other sensitive information, while Key Protect activity tracking events can be monitored through IBM Cloud Logs. ([IBM Cloud][6])

---

## Day 113 — IBM Cloud Observability, Logs, Monitoring, Activity Tracker, SLOs

```text
Act as a senior IBM Cloud SRE and production-readiness mentor.

Today is Day 113.

Topic:
Observability and production operations for IBM Cloud services, service brokers, metering pipelines, and billing-related systems.

Cover in detail:
1. Logs.
2. Metrics.
3. Traces.
4. Audit events.
5. Activity tracking.
6. IBM Cloud Logs.
7. IBM Cloud Monitoring.
8. SLI, SLO, SLA, and error budget.
9. Alert design.
10. Incident response.

Also cover:
- Observability for service broker APIs.
- Observability for metering collectors.
- Observability for billing reconciliation jobs.
- Important metrics: provision latency, provision failure rate, usage submission success rate, duplicate usage count, billing reconciliation mismatch count.
- Alert examples.
- Runbook examples.
- Postmortem structure.
- Customer-impact communication.
- Debugging production incidents.

Mandatory output format:
- 5-line beginner summary
- Descriptive notes
- ASCII observability diagram: app → logs/metrics/traces/audit → alert → runbook
- Example metrics for service broker and metering pipeline
- Example alerts
- Runbook template
- Common production issues
- Debugging checklist
- 10 interview questions with strong answers
- Hands-on task: design monitoring for service broker, metering collector, billing reconciliation job, and customer-facing API
```

IBM Cloud docs for multiple services show observability integrations with IBM Cloud Logs and IBM Cloud Monitoring, and security/observability reference architecture material includes services such as Key Protect, Secrets Manager, Activity Tracker Event Routing, Event Notifications, and log retention through Object Storage. ([IBM Cloud][7])

---

## Day 114 — Final IBM Cloud System Design Mock: Service Onboarding + Metering + Billing Platform

```text
Act as a strict IBM Cloud backend/platform interviewer.

Today is Day 114.

Conduct a full IBM Cloud system design and interview revision.

Design:
A usage-based IBM Cloud service that can be onboarded through Partner Center, shown in the IBM Cloud catalog, provisioned through a service broker, deployed on IBM Cloud infrastructure, metered accurately, billed correctly, secured properly, and operated reliably.

Cover in detail:
1. Requirement clarification.
2. Functional requirements.
3. Non-functional requirements.
4. IBM Cloud account and IAM model.
5. Resource group design.
6. Partner Center onboarding.
7. Catalog metadata.
8. Pricing plans.
9. Service broker lifecycle.
10. Resource Controller interaction.
11. Deployment option: VSI vs Kubernetes/OpenShift vs Code Engine.
12. Data model.
13. Usage metering.
14. Billing and BSS flow.
15. Billing reconciliation.
16. Toolchain and pipeline.
17. Security and secrets.
18. Observability and audit.
19. Failure handling.
20. Cost and capacity.
21. Trade-offs.
22. Interview explanation.
23. Weak-area checklist.
24. Final revision priorities.
25. Final 7-day follow-up plan.

Mandatory output:
- 5-line summary
- Full system design answer
- IBM Cloud architecture ASCII diagram
- Provisioning sequence diagram
- Metering and billing sequence diagram
- CI/CD pipeline diagram
- Pseudocode for provision, bind, usage submission, billing reconciliation, and deprovision
- Example schemas:
  - service instance
  - binding
  - usage event
  - metering aggregate
  - invoice line item
  - audit event
- Table: component → responsibility → failure mode → mitigation
- Table: IBM Cloud service → role → AWS equivalent
- Table: design decision → trade-off → alternative
- 25 IBM Cloud interview questions with strong answers
- 10 billing/metering interview questions with strong answers
- 10 service onboarding interview questions with strong answers
- Final 7-day IBM Cloud revision checklist
```

---

# Final coverage check

This revised 14-day plan now covers:

```text
IBM Cloud fundamentals
IAM, resource groups, service IDs, API keys
VPC, networking, subnets, security groups
VSI
Kubernetes and OpenShift
Code Engine
Databases, Object Storage, Event Streams
Toolchains, Continuous Delivery, Tekton pipelines
Billing, usage reports, billing units, BSS concepts
Usage metering and usage-based pricing
Partner Center and catalog onboarding
Service broker and Resource Controller lifecycle
Security, Secrets Manager, Key Protect, audit
Observability, monitoring, logs, SLOs
Final IBM Cloud system design mock
```

Yes — this is now a **complete IBM Cloud add-on layer** for your 100-day plan.

[1]: https://cloud.ibm.com/docs/sell?topic=sell-how-it-works&utm_source=chatgpt.com "How third-party services use the IBM Cloud platform"
[2]: https://cloud.ibm.com/docs/ContinuousDelivery?topic=ContinuousDelivery-tekton-pipelines&utm_source=chatgpt.com "Working with Tekton pipelines"
[3]: https://cloud.ibm.com/docs/account?topic=account-overview-billing&utm_source=chatgpt.com "Video - How can I manage billing and usage in IBM Cloud?"
[4]: https://cloud.ibm.com/docs/overview?topic=overview-whatis-platform&utm_source=chatgpt.com "What is the IBM Cloud platform?"
[5]: https://cloud.ibm.com/docs/sell?topic=sell-broker-dev-host&utm_source=chatgpt.com "Developing, hosting, and testing your service brokers"
[6]: https://cloud.ibm.com/docs/security-hub?locale=ja&topic=security-hub-core-security-services-pattern&utm_source=chatgpt.com "Cloud foundation for security and observability"
[7]: https://cloud.ibm.com/docs/databases-for-mongodb-gen2?topic=databases-for-mongodb-gen2-console-overview&utm_source=chatgpt.com "The console overview | IBM Cloud Docs"
