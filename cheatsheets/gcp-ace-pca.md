# GCP ACE & PCA Cheatsheet — Exam Day Quick Reference

> Covers the highest-yield topics for GCP Associate Cloud Engineer (ACE) and Professional Cloud Architect (PCA).

---

## Exam at a Glance

| | ACE | PCA |
|---|---|---|
| Questions | 50–60 | 50–60 |
| Duration | 2 hours | 2 hours |
| Passing Score | ~70% (not published) | ~70% (not published) |
| Cost | $200 USD | $200 USD |
| Format | Multiple choice + multiple select | Case study + scenario |
| Register | [cloud.google.com/learn/certification](https://cloud.google.com/learn/certification) | [cloud.google.com/learn/certification](https://cloud.google.com/learn/certification) |

### ACE Domains

| Domain | Weight |
|---|---|
| Setting up a cloud solution environment | ~17% |
| Planning and configuring a cloud solution | ~17% |
| Deploying and implementing a cloud solution | ~25% |
| Ensuring successful operation | ~20% |
| Configuring access and security | ~20% |

### PCA Domains

| Domain | Weight |
|---|---|
| Designing and planning cloud solution architecture | ~24% |
| Managing and provisioning cloud infrastructure | ~15% |
| Designing for security and compliance | ~18% |
| Analyzing and optimizing technical and business processes | ~18% |
| Managing implementation | ~11% |
| Ensuring solution and operations reliability | ~14% |

---

## Compute

| Service | Use Case | AWS Equivalent |
|---|---|---|
| Compute Engine | IaaS virtual machines | EC2 |
| App Engine Standard | Auto-scaling PaaS, managed runtime | Elastic Beanstalk |
| App Engine Flexible | Container-based PaaS | Elastic Beanstalk (container) |
| Cloud Functions | Serverless event-driven | Lambda |
| Cloud Run | Serverless containers, HTTP-triggered | Lambda (container) / Fargate |
| GKE | Managed Kubernetes | EKS |
| GKE Autopilot | Fully managed K8s (no node management) | EKS + Fargate |
| Batch | Managed batch compute | AWS Batch |

### Compute Decision Tree

```
Need full control over OS?                     → Compute Engine
Need managed PaaS, no containers?             → App Engine Standard
Need serverless HTTP endpoints?               → Cloud Run
Need event-driven functions?                  → Cloud Functions
Need Kubernetes?                              → GKE
Need managed K8s with no node ops?           → GKE Autopilot
```

### Compute Engine Key Concepts

| Concept | Details |
|---|---|
| Machine families | General-purpose (N, E2), Compute-optimized (C), Memory-optimized (M), GPU (A, G) |
| Preemptible VMs | Up to 91% cheaper, can be terminated with 30s notice |
| Spot VMs | No max runtime limit (unlike preemptible), same pricing |
| Managed Instance Groups (MIG) | Auto-scaling, auto-healing, rolling updates |
| Unmanaged Instance Groups | Static group, no autoscaling |
| Custom machine types | Define exact vCPU + memory for your workload |

---

## Storage

| Service | Type | Use Case | AWS Equivalent |
|---|---|---|---|
| Cloud Storage | Object | Unstructured data, backups, static sites | S3 |
| Persistent Disk | Block (HDD/SSD) | VM boot disks, databases | EBS |
| Hyperdisk | Block (high perf) | I/O intensive workloads | EBS io2 |
| Filestore | NFS file share | Shared storage for VMs | EFS |
| Cloud Storage for Firebase | Object | Mobile/web app data | S3 |

### Cloud Storage Classes

| Class | Use Case | Retrieval Cost |
|---|---|---|
| Standard | Frequently accessed | None |
| Nearline | Access < once/month | Yes |
| Coldline | Access < once/quarter | Yes |
| Archive | Access < once/year, compliance | Yes (highest) |

---

## Databases

| Service | Type | Use Case | AWS Equivalent |
|---|---|---|---|
| Cloud SQL | Relational (MySQL, PG, SQL Server) | OLTP, web apps | RDS |
| Cloud Spanner | Relational (globally distributed) | Global ACID, high scale | Aurora Global |
| Firestore | NoSQL document | Mobile/web, real-time sync | DynamoDB |
| Bigtable | NoSQL wide-column | Time-series, IoT, analytics | DynamoDB (HPC) |
| BigQuery | Data warehouse | Analytics, ML, petabyte-scale | Redshift |
| Memorystore | In-memory (Redis/Memcached) | Caching, session storage | ElastiCache |
| AlloyDB | PostgreSQL-compatible, high perf | HTAP workloads | Aurora |

### Database Decision Tree

```
Need relational, standard OLTP?              → Cloud SQL
Need global transactions with strong consistency? → Cloud Spanner
Need NoSQL, document model, real-time?       → Firestore
Need NoSQL, high throughput, time-series?    → Bigtable
Need analytics, SQL on large datasets?       → BigQuery
Need caching?                                → Memorystore
```

---

## Networking

| Service | Function | AWS Equivalent |
|---|---|---|
| VPC | Global virtual network (spans regions by default) | VPC (regional) |
| Subnet | Regional — spans all zones in a region | Subnet (AZ-specific) |
| Cloud Router | Dynamic BGP routing with on-premises | Transit Gateway |
| Cloud Interconnect | Dedicated private connection | Direct Connect |
| Cloud VPN | Encrypted IPsec tunnel | Site-to-Site VPN |
| Cloud Load Balancing | Global/regional LB | ALB/NLB/GWLB |
| Cloud CDN | Content delivery network | CloudFront |
| Cloud Armor | WAF + DDoS protection | WAF + Shield |
| Cloud DNS | Managed DNS | Route 53 |
| Private Google Access | VMs without public IP can reach Google APIs | VPC Endpoints |

### GCP vs AWS Networking — Key Differences

| | GCP | AWS |
|---|---|---|
| VPC scope | Global — one VPC spans all regions | Regional — separate VPC per region |
| Subnet scope | Regional — spans all zones | AZ-specific |
| Default network | Exists by default (delete for production) | Exists by default |
| Load balancer (global) | One LB, global anycast IP | CloudFront + ALB (separate) |

### Load Balancers

| Type | Scope | Protocol |
|---|---|---|
| Global External HTTP(S) LB | Global | HTTP/HTTPS |
| Regional External HTTP(S) LB | Regional | HTTP/HTTPS |
| External TCP/UDP Network LB | Regional | TCP/UDP |
| Internal HTTP(S) LB | Regional (internal) | HTTP/HTTPS |
| Internal TCP/UDP LB | Regional (internal) | TCP/UDP |

---

## IAM & Security

### IAM Hierarchy

```
Organization
    └── Folder(s)
            └── Project(s)
                    └── Resources
```

- Permissions are inherited downward
- Deny policies override allow policies

### IAM Role Types

| Type | Use Case |
|---|---|
| Basic roles | Owner / Editor / Viewer — legacy, overly broad |
| Predefined roles | Service-specific, fine-grained (recommended) |
| Custom roles | Your own combination of permissions |

### Key IAM Concepts

- **Service Account**: identity for applications/VMs (like AWS IAM Role)
- **Workload Identity Federation**: allow external identities (GitHub Actions, AWS) to authenticate without keys
- **IAM Conditions**: attribute-based access (time, resource, IP)
- **VPC Service Controls**: perimeter to prevent data exfiltration from GCP APIs

### Security Services

| Service | Function | AWS Equivalent |
|---|---|---|
| Cloud Armor | WAF + DDoS | WAF + Shield |
| Security Command Center | Posture management, threat detection | Security Hub |
| Cloud KMS | Key management | KMS |
| Cloud HSM | Hardware security module | CloudHSM |
| Secret Manager | Secrets storage and rotation | Secrets Manager |
| Cloud Audit Logs | API call logging | CloudTrail |
| VPC Flow Logs | Network traffic logging | VPC Flow Logs |

---

## Operations & Monitoring

| Service | Function | AWS Equivalent |
|---|---|---|
| Cloud Monitoring | Metrics, dashboards, alerting | CloudWatch Metrics |
| Cloud Logging | Log ingestion and analysis | CloudWatch Logs |
| Cloud Trace | Distributed tracing | X-Ray |
| Cloud Profiler | CPU/memory profiling | — |
| Error Reporting | Aggregates application errors | CloudWatch + SNS |
| Cloud Debugger | Live debugging in production | — |

---

## Data & Analytics

| Service | Function | AWS Equivalent |
|---|---|---|
| BigQuery | Serverless data warehouse | Redshift |
| Dataflow | Managed Apache Beam (streaming + batch) | Kinesis Data Analytics |
| Dataproc | Managed Hadoop/Spark | EMR |
| Pub/Sub | Message queue / event streaming | SNS + SQS / Kinesis |
| Looker | BI and data exploration | QuickSight |
| Data Catalog | Metadata management | Glue Data Catalog |

---

## AI & ML Services

| Service | Function | AWS Equivalent |
|---|---|---|
| Vertex AI | Unified ML platform | SageMaker |
| Gemini API | Multimodal LLM | Bedrock (Claude/Titan) |
| Cloud Vision AI | Image recognition | Rekognition |
| Cloud Natural Language | Text analysis, entity extraction | Comprehend |
| Cloud Speech-to-Text | Audio → text | Transcribe |
| Cloud Text-to-Speech | Text → audio | Polly |
| Document AI | Document parsing | Textract |
| Recommendations AI | Personalization | Personalize |

---

## Exam Tips — ACE

1. **Default service account has Editor role** — change it to least-privilege in production
2. **Cloud Storage is global** — bucket name must be globally unique
3. **Preemptible/Spot VMs** for fault-tolerant batch jobs — up to 91% cheaper
4. **GKE Autopilot** = no node management; standard GKE = you manage nodes
5. **Firestore** for real-time mobile/web apps; **Bigtable** for time-series + analytics
6. **BigQuery is serverless** — no cluster management, pay per query or flat-rate
7. **Cloud Spanner** when you need ACID + global scale (very expensive)
8. **Managed Instance Groups (MIG)** for auto-scaling + auto-healing
9. **`gcloud`, `bq`, `gsutil` (now `gcloud storage`)** — know the CLI tools
10. **Organization > Folder > Project hierarchy** — permissions inherit downward

## Exam Tips — PCA (Case Study Tips)

1. Read the case study requirements first — map to GCP products
2. **Reliability** → Multi-region Cloud SQL with failover + Cloud Armor
3. **Cost optimization** → Preemptible VMs, committed use discounts, right-sizing
4. **Migration** → Lift-and-shift = Compute Engine; modernize = GKE or Cloud Run
5. **Security** → VPC Service Controls + IAM least-privilege + Cloud Armor
6. **Data strategy** → BigQuery for analytics; Firestore for operational; Bigtable for IoT

---

*Official guides: [ACE](https://cloud.google.com/learn/certification/cloud-engineer) · [PCA](https://cloud.google.com/learn/certification/cloud-architect)*  
*Practice: [Cloud Skills Boost](https://cloudskillsboost.google)*  
*1:1 mentorship: [topmate.io/heyshashank](https://topmate.io/heyshashank)*
