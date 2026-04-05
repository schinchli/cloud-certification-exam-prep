# AWS SAA-C03 & CLF-C02 Cheatsheet — Exam Day Quick Reference

> Covers the highest-yield topics for AWS Certified Solutions Architect – Associate (SAA-C03) and AWS Certified Cloud Practitioner (CLF-C02).

---

## CLF-C02 — Exam at a Glance

| | |
|---|---|
| Questions | 65 (scored) |
| Duration | 90 minutes |
| Passing Score | 700 / 1,000 |
| Format | Multiple choice + multiple response |
| Domains | Cloud Concepts · Security · Technology · Billing |

## SAA-C03 — Exam at a Glance

| | |
|---|---|
| Questions | 65 (scored) |
| Duration | 130 minutes |
| Passing Score | 720 / 1,000 |
| Format | Scenario-based MCQ |
| Domains | Resilient (26%) · High-Performing (24%) · Secure (30%) · Cost-Optimized (20%) |

---

## Core Concepts (CLF-C02 + SAA-C03)

### Cloud Fundamentals

| Term | Definition |
|---|---|
| CapEx | Upfront capital expenditure — traditional on-premises |
| OpEx | Ongoing operational cost — cloud model |
| Elasticity | Scale up/down automatically with demand |
| High Availability | System stays operational despite component failures |
| Fault Tolerance | System continues operating even when components fail |
| Scalability | Ability to handle growing workload |
| Shared Responsibility Model | AWS secures the cloud; customer secures what's in the cloud |

### AWS Global Infrastructure

| Component | What It Is |
|---|---|
| Region | Geographic area with 2+ AZs |
| Availability Zone (AZ) | One or more data centers, isolated from other AZs |
| Edge Location | CloudFront CDN cache point — 400+ globally |
| Local Zone | Extension of a region closer to end users |
| Wavelength Zone | Ultra-low latency for 5G applications |

---

## Compute

### EC2 Pricing Models

| Model | Use Case | Savings vs On-Demand |
|---|---|---|
| On-Demand | Unpredictable workloads, dev/test | Baseline |
| Reserved (1yr/3yr) | Steady-state, predictable | Up to 72% |
| Savings Plans | Flexible compute, any instance type | Up to 66% |
| Spot | Fault-tolerant, flexible, interruptible | Up to 90% |
| Dedicated Host | Licensing compliance, physical server control | — |

### EC2 Instance Families (SAA-C03 must-know)

| Family | Optimized For | Examples |
|---|---|---|
| T (General) | Burstable, dev/test | t3.micro, t3.small |
| M (General) | Balanced CPU/RAM | m6i.large |
| C (Compute) | CPU-intensive workloads | c6i.xlarge |
| R (Memory) | In-memory DBs, caches | r6i.2xlarge |
| I (Storage) | High I/O, NVMe | i3.large |
| P / G / Inf | GPU / ML inference | p3.2xlarge |

### Lambda

- Serverless, event-driven, no server management
- Max execution time: **15 minutes**
- Max memory: **10,240 MB**
- Concurrency: 1,000 default (soft limit, can increase)
- Triggers: API Gateway, S3, DynamoDB Streams, SQS, EventBridge, SNS

---

## Storage

### S3 Storage Classes

| Class | Use Case | Retrieval |
|---|---|---|
| S3 Standard | Frequently accessed data | Instant |
| S3 Standard-IA | Infrequent access, rapid retrieval | Instant |
| S3 One Zone-IA | Infrequent, single AZ | Instant |
| S3 Intelligent-Tiering | Unknown access patterns | Instant |
| S3 Glacier Instant Retrieval | Archives, ms retrieval | Milliseconds |
| S3 Glacier Flexible Retrieval | Archives, minutes–hours | Minutes to hours |
| S3 Glacier Deep Archive | Lowest cost, 7–10yr retention | Up to 12 hours |

### EBS Volume Types

| Type | Use Case | Max IOPS |
|---|---|---|
| gp3 | General purpose, default | 16,000 |
| gp2 | Legacy general purpose | 16,000 |
| io2 Block Express | High-performance DBs | 256,000 |
| st1 | Throughput HDD (big data) | 500 |
| sc1 | Cold HDD, archival | 250 |

### Storage Decision Tree

```
Need block storage for EC2?          → EBS
Need shared file storage (NFS)?      → EFS (Linux) / FSx for Windows
Need object storage?                 → S3
Need lowest latency key-value?       → DynamoDB
Need relational DB?                  → RDS / Aurora
Need in-memory caching?              → ElastiCache (Redis or Memcached)
```

---

## Networking

### VPC Core Components

| Component | Function |
|---|---|
| VPC | Isolated virtual network |
| Subnet | Public (has IGW route) or Private (no IGW route) |
| Internet Gateway (IGW) | Enables internet access for public subnets |
| NAT Gateway | Outbound-only internet for private subnets |
| Security Group | Stateful firewall at instance level |
| Network ACL | Stateless firewall at subnet level |
| Route Table | Directs traffic within VPC and to gateways |
| VPC Peering | Private connectivity between two VPCs |
| Transit Gateway | Hub connecting many VPCs and on-premises |
| PrivateLink | Expose services privately without public internet |

### Load Balancer Types

| Type | Layer | Best For |
|---|---|---|
| Application LB (ALB) | 7 (HTTP/HTTPS) | Path/host routing, microservices, containers |
| Network LB (NLB) | 4 (TCP/UDP) | Ultra-low latency, static IP, high throughput |
| Gateway LB (GWLB) | 3 | Network security appliances, inline inspection |

---

## Databases

| Service | Type | Key Feature |
|---|---|---|
| RDS | Relational (OLTP) | Managed, Multi-AZ, automated backups |
| Aurora | Relational | 5x faster than MySQL, serverless option |
| DynamoDB | NoSQL (key-value) | Single-digit ms, serverless, global tables |
| ElastiCache | In-memory | Redis (persistence) or Memcached (simple cache) |
| Redshift | Data warehouse | Columnar, OLAP, Petabyte-scale analytics |
| DocumentDB | Document (MongoDB-compatible) | JSON documents |
| Neptune | Graph database | Social networks, knowledge graphs |

### RDS Multi-AZ vs Read Replicas

| | Multi-AZ | Read Replica |
|---|---|---|
| Purpose | High availability / DR | Read scaling |
| Replication | Synchronous | Asynchronous |
| Failover | Automatic | Manual promotion |
| Region | Same region (cross-region option) | Same or cross-region |
| Readable | No (standby) | Yes |

---

## Security (SAA-C03 Domain: 30%)

### IAM Key Concepts

- **Users**: individual identities with credentials
- **Groups**: collection of users sharing permissions
- **Roles**: temporary credentials assumed by services or users
- **Policies**: JSON documents granting/denying permissions
- **Least privilege**: grant only what is needed, nothing more
- MFA should be enabled on root and all IAM users

### Encryption Services

| Service | Use Case |
|---|---|
| KMS | Create and manage encryption keys; integrates with S3, EBS, RDS |
| CloudHSM | Dedicated hardware security module; you control the keys |
| Secrets Manager | Store, rotate, and retrieve database credentials and API keys |
| Parameter Store | Lightweight config and secrets (free tier available) |
| ACM | Provision and manage SSL/TLS certificates |

### Threat Detection & Compliance

| Service | What It Does |
|---|---|
| GuardDuty | ML-based threat detection across CloudTrail, VPC Flow Logs, DNS |
| Inspector | Automated vulnerability scanning for EC2, Lambda, containers |
| Security Hub | Central security findings aggregator |
| Config | Records and evaluates AWS resource configurations against rules |
| CloudTrail | API call logging — who did what, when, from where |
| Macie | Discovers and protects sensitive data in S3 (PII, financial) |
| Shield Standard | Free automatic DDoS protection |
| Shield Advanced | Enhanced DDoS + 24/7 DRT support (paid) |
| WAF | Block malicious web traffic based on rules |

---

## High Availability Patterns (SAA-C03)

### Disaster Recovery Strategies (least → most expensive)

| Strategy | RTO | RPO | Cost |
|---|---|---|---|
| Backup & Restore | Hours | Hours | $ |
| Pilot Light | 10s of minutes | Minutes | $$ |
| Warm Standby | Minutes | Seconds | $$$ |
| Multi-Site Active-Active | Near zero | Near zero | $$$$ |

### Auto Scaling + Load Balancer Pattern

```
Internet → Route 53 → CloudFront → ALB → ASG (EC2 in Multi-AZ)
                                              ↓
                                    RDS Multi-AZ (primary + standby)
                                              ↓
                                    ElastiCache (read cache)
```

---

## Integration Services

| Service | Pattern | Use Case |
|---|---|---|
| SQS | Queue (pull) | Decouple producers from consumers, absorb spikes |
| SNS | Pub/Sub (push) | Fan-out notifications to multiple subscribers |
| EventBridge | Event bus | Route events from AWS services to targets |
| Step Functions | Workflow orchestration | Multi-step serverless workflows |
| Kinesis Data Streams | Real-time streaming | High-throughput data ingestion |
| Kinesis Firehose | Streaming to S3/Redshift | ETL, no consumer code needed |

### SQS vs SNS vs EventBridge

| | SQS | SNS | EventBridge |
|---|---|---|---|
| Model | Queue (pull) | Topic (push) | Event bus (rules) |
| Retention | Up to 14 days | No retention | No retention |
| Consumers | One (each message) | Many (fan-out) | Many (rule-matched) |
| Use case | Task queue | Broadcast alerts | AWS event routing |

---

## Cost Optimization Tips (CLF-C02 + SAA-C03)

- Use **Reserved Instances or Savings Plans** for steady-state workloads
- Use **Spot Instances** for batch, CI/CD, fault-tolerant jobs
- Use **S3 Intelligent-Tiering** for unpredictable access patterns
- Use **CloudFront** to reduce data transfer costs from origin
- Use **Auto Scaling** to right-size capacity to demand
- Use **Trusted Advisor** and **Cost Explorer** to find waste
- Delete unattached EBS volumes, idle load balancers, and unused Elastic IPs

---

## Exam Tips — SAA-C03

1. **"Highly available" → Multi-AZ** for RDS and EC2 behind an ALB
2. **"Cost-effective + flexible" → Spot Instances** for stateless/batch
3. **"Decouple" → SQS** between producer and consumer
4. **"Fan-out" → SNS → SQS** (SNS pushing to multiple SQS queues)
5. **"Serverless" → Lambda + DynamoDB + API Gateway**
6. **"Global low latency" → CloudFront + Route 53 latency routing**
7. **"Encrypt at rest" → KMS** (S3 SSE-KMS, EBS, RDS encryption)
8. **"Shared file system for Linux EC2" → EFS**
9. **"Migrate large data to AWS" → Snowball Edge or DataSync**
10. **"Temporary credentials for EC2/Lambda" → IAM Role (not access keys)**

---

*Official exam guides: [SAA-C03](https://d1.awsstatic.com/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate_Exam-Guide.pdf) · [CLF-C02](https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf)*  
*Practice tests: [AWS Skill Builder](https://skillbuilder.aws)*  
*1:1 mentorship: [topmate.io/heyshashank](https://topmate.io/heyshashank)*
