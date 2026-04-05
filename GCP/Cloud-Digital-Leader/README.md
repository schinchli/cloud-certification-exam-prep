# Google Cloud Digital Leader Certification

This folder contains comprehensive study materials for the Google Cloud Digital Leader certification exam.

## Contents

- `GCP-Cloud-Digital-Leader-Complete-Study-Guide.md` - Complete study guide with all key concepts and AWS equivalents
- `GCP-Cloud-Digital-Leader-Practice-Questions-by-Service.md` - Practice questions organized by GCP service

## Exam Overview

The Google Cloud Digital Leader certification validates foundational knowledge of cloud concepts and Google Cloud products and services.

### Domain Breakdown

| Domain | Weight | Topics |
|--------|--------|--------|
| **1. Digital Transformation with Google Cloud** | ~17% | Cloud value, transformation pillars, business benefits |
| **2. Innovating with Data and Google Cloud** | ~23% | Data types, BigQuery, data lifecycle, AI/ML basics |
| **3. Infrastructure and Application Modernization** | ~30% | Compute, storage, networking, containers, serverless |
| **4. Google Cloud Security and Operations** | ~30% | Security, IAM, monitoring, cost management |

### Key Services to Master

#### Compute
| Service | Type | AWS Equivalent | Use Case |
|---------|------|----------------|----------|
| **Compute Engine** | IaaS | EC2 | VMs, full control |
| **GKE** | Container | EKS | Kubernetes orchestration |
| **Cloud Run** | Serverless | Fargate | Stateless containers |
| **Cloud Functions** | FaaS | Lambda | Event-driven functions |
| **App Engine** | PaaS | Elastic Beanstalk | Web applications |

#### Database
| Service | Type | AWS Equivalent | Use Case |
|---------|------|----------------|----------|
| **Cloud SQL** | Relational | RDS | Regional OLTP |
| **Cloud Spanner** | Global SQL | Aurora Global | Global consistency |
| **Bigtable** | NoSQL | DynamoDB | High throughput, IoT |
| **Firestore** | Document | DynamoDB | Mobile/web apps |
| **BigQuery** | Analytics | Redshift | Data warehouse, OLAP |

#### Security & Operations
| Service | AWS Equivalent | Purpose |
|---------|----------------|---------|
| **IAM** | IAM | Identity management |
| **Security Command Center** | Security Hub | Security posture |
| **Cloud Armor** | WAF + Shield | DDoS protection |
| **Cloud Logging** | CloudWatch Logs | Log management |
| **Cloud Monitoring** | CloudWatch | Metrics and alerts |

### Exam Details

| Attribute | Value |
|-----------|-------|
| **Duration** | 90 minutes |
| **Questions** | ~50-60 multiple choice |
| **Passing Score** | ~70% |
| **Cost** | $99 USD |
| **Validity** | 3 years |
| **Prerequisites** | None |

## Study Approach

### Phase 1: Cloud Fundamentals (Week 1)
- Cloud vs on-premises concepts
- IaaS, PaaS, SaaS models
- Shared responsibility model
- Digital transformation pillars

### Phase 2: Core Services (Week 2-3)
- Compute options (VMs, containers, serverless)
- Storage and database selection
- Networking and connectivity
- Security and IAM

### Phase 3: Data & Analytics (Week 4)
- BigQuery and data warehousing
- ETL and data processing
- AI/ML services overview
- Looker and visualization

### Phase 4: Practice & Review (Week 5)
- Practice exams
- Review weak areas
- Decision matrix memorization
- Final preparation

## Critical Exam Topics

### Service Selection Patterns

**Compute Selection:**
```
Full OS control needed? → Compute Engine
Containerized, serverless? → Cloud Run
Event-driven, lightweight? → Cloud Functions
Complex microservices? → GKE
Simple web app, PaaS? → App Engine
```

**Database Selection:**
```
Relational, regional? → Cloud SQL
Relational, global? → Cloud Spanner
NoSQL, high throughput? → Bigtable
Document, mobile/web? → Firestore
Analytics, warehouse? → BigQuery
```

**Storage Selection:**
```
Frequent access? → Standard
Monthly access? → Nearline
Quarterly access? → Coldline
Yearly access? → Archive
```

### Key Decision Keywords

| Keyword | Usually Means |
|---------|---------------|
| "Quickly/ASAP" | Cloud VPN, on-demand, Cloud Run |
| "Cost-optimized" | Preemptible, appropriate storage class |
| "Serverless" | Cloud Functions, Cloud Run, App Engine |
| "Global" | Cloud Spanner, Cloud CDN, multi-region |
| "Sensitive data" | Partner Interconnect, CMEK |
| "Event-driven" | Cloud Functions, Pub/Sub |
| "Analytics" | BigQuery, Dataflow |
| "Mobile" | Firebase |
| "Millions of sensors" | Bigtable |

### Common Exam Traps

- **Committed use discount** for short-term → Use on-demand
- **Cloud VPN** for sensitive data → Use Partner Interconnect
- **Single zone** for redundancy → Use multiple zones
- **Annual cost review** → Review frequently
- **Physical hardware** for temporary needs → Use cloud VMs

## Success Tips

1. **Service Mapping**: Learn GCP to AWS equivalents if coming from AWS
2. **Decision Trees**: Memorize compute, database, storage selection flows
3. **Keywords**: Spot decision keywords in questions
4. **Hands-on**: Try GCP free tier for practical experience
5. **Practice**: Use official practice exams

## Recommended Resources

### Google Materials
- [Google Cloud Skills Boost](https://www.cloudskillsboost.google/)
- [Cloud Digital Leader Learning Path](https://cloud.google.com/learn/certification/cloud-digital-leader)
- [Google Cloud Documentation](https://cloud.google.com/docs)

### Practice
- Official Google Cloud practice exams
- Hands-on labs in Cloud Skills Boost
- Tutorials Dojo practice tests

Good luck with your certification!
