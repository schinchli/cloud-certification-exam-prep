# GCP Cloud Digital Leader - Questions Organized by Service

> **Source:** 289 practice questions from exam preparation material
> **Organization:** Questions grouped by GCP service/topic for focused study

---

## Table of Contents
1. [Compute Services](#compute-services)
2. [Database Services](#database-services)
3. [Storage Services](#storage-services)
4. [Networking & Connectivity](#networking--connectivity)
5. [Security & Identity](#security--identity)
6. [Data & Analytics](#data--analytics)
7. [DevOps & CI/CD](#devops--cicd)
8. [Cost Optimization](#cost-optimization)
9. [Migration & Hybrid Cloud](#migration--hybrid-cloud)
10. [Organization & Governance](#organization--governance)

---

## Compute Services

### Compute Engine (VMs)

**Q: Short-term compute needs (2 weeks)**
- Scenario: Need extra computing power for 2 weeks only
- Options: A) Committed use discount B) Physical computer C) On-demand VM D) Multiple physical computers
- **Answer: C** - On-demand VM without committed use discount
- **Why:** Pay-as-you-go for temporary workloads, no long-term commitment
- **AWS Equivalent:** EC2 On-Demand instances

**Q: Windows Server license optimization**
- Scenario: Windows VMs only used during work hours, licenses expiring
- Options: A) Renew 3 years + negotiate B) Renew 2 years + auto-renew C) BYOL D) PAYG
- **Answer: D** - Migrate to Compute Engine with PAYG licensing
- **Why:** Per-second billing eliminates weekend license costs
- **AWS Equivalent:** EC2 with License Included pricing

**Q: Rendering workload (interruptible)**
- Scenario: <12 hours per job, can be interrupted, no SLA, global storage
- Options: A) Preemptible instances B) Unmanaged instance group C) Reservations D) More instances with fewer vCPUs
- **Answer: A** - Deploy on preemptible instances
- **Why:** 80% cost savings for fault-tolerant workloads
- **AWS Equivalent:** EC2 Spot Instances

### Cloud Run (Serverless Containers)

**Q: Container image storage for Cloud Run**
- Scenario: CI/CD pipeline for Cloud Run deployment
- Options: A) Compute Engine image B) Container Registry C) Cloud Storage D) Compute Engine disk
- **Answer: B** - Store images in Container Registry (now Artifact Registry)
- **Why:** Native integration with Cloud Run, seamless deployment
- **AWS Equivalent:** Amazon ECR

### Cloud Functions (Event-Driven)

**Q: Event-driven follower notifications**
- Scenario: Respond to database writes, scale to zero, integrate with Pub/Sub
- Options: A) GKE B) Cloud Functions C) App Engine flexible D) Compute Engine
- **Answer: B** - Cloud Functions
- **Why:** Serverless, event-driven, auto-scales to zero, integrates with Firebase
- **AWS Equivalent:** Lambda with DynamoDB Streams

### App Engine (PaaS)

**Q: SaaS vs PaaS vs IaaS**
- Scenario: Minimize customer management overhead
- Options: A) Balance flexibility B) Minimize management C) Maximize flexibility D) Shift emphasis
- **Answer: B** - SaaS minimizes customer management
- **Why:** Provider manages everything except data/users
- **AWS Equivalent:** Use SaaS products (Salesforce, Workday)

### Containers vs VMs

**Q: Slow VM rolling updates**
- Scenario: OS boot times slow down deployments, need faster releases
- Options: A) Migrate VMs to cloud B) Convert to containers C) Increase VM resources D) Automate rollouts
- **Answer: B** - Convert applications to containers
- **Why:** Containers start in seconds vs minutes for VMs
- **AWS Equivalent:** Docker + ECS/EKS

---

## Database Services

### Cloud SQL (Regional Relational)

**Q: Standard database selection**
- Scenario: Regional relational database needs
- **Answer:** Cloud SQL for MySQL, PostgreSQL, SQL Server
- **Why:** Managed service, automatic backups, high availability
- **AWS Equivalent:** Amazon RDS

### Cloud Spanner (Global Relational)

**Q: Global database requirements**
- Scenario: Need globally distributed relational database with strong consistency
- **Answer:** Cloud Spanner
- **Why:** Global scale, horizontal scaling, ACID transactions
- **AWS Equivalent:** Aurora Global Database

### Bigtable (NoSQL High Throughput)

**Q: IoT sensor data (millions of devices)**
- Scenario: Worldwide, high-speed, large unstructured data from sensors
- Options: A) Firestore B) Data Fusion C) Cloud SQL D) Bigtable
- **Answer: D** - Cloud Bigtable
- **Why:** NoSQL, high throughput, petabyte-scale, low latency
- **AWS Equivalent:** DynamoDB or Timestream

### Firestore (Mobile/Web)

**Q: Mobile app backend**
- Scenario: Document database for mobile/web apps with real-time sync
- **Answer:** Firestore
- **Why:** Real-time synchronization, offline support, mobile SDKs
- **AWS Equivalent:** DynamoDB + AppSync

### BigQuery (Data Warehouse)

**Q: Analytics and data warehouse**
- Scenario: Need to analyze petabytes of data, OLAP workloads
- **Answer:** BigQuery
- **Why:** Serverless, petabyte-scale, SQL interface, ML integration
- **AWS Equivalent:** Redshift + Athena

---

## Storage Services

### Cloud Storage Classes

**Q: Standard vs Coldline storage**
- Scenario: What's the difference?
- Options: A) Transfer rate B) Durability C) APIs D) Access frequency
- **Answer: D** - Coldline is for infrequently accessed data
- **Why:** Lower storage cost, higher retrieval cost, 90-day minimum
- **AWS Equivalent:** S3 Standard vs Glacier

**Storage Class Decision Matrix:**
- **Standard** → Frequent access (daily)
- **Nearline** → Monthly access (30-day minimum)
- **Coldline** → Quarterly access (90-day minimum)
- **Archive** → Yearly access (365-day minimum)

---

## Networking & Connectivity

### Cloud VPN (Fast Setup)

**Q: Fast private connectivity setup**
- Scenario: Connect on-prem to cloud ASAP
- Options: A) Cloud Interconnect B) Direct Peering C) Cloud VPN D) Cloud CDN
- **Answer: C** - Cloud VPN
- **Why:** Quick setup (hours), encrypted over internet
- **AWS Equivalent:** Site-to-Site VPN

### Cloud Interconnect (Dedicated)

**Q: Sensitive data, no public internet**
- Scenario: On-prem data can't traverse public internet
- Options: A) IAP B) Cloud VPN C) Partner Interconnect D) Private Google Access
- **Answer: C** - Partner Interconnect
- **Why:** Dedicated private connection, bypasses internet entirely
- **AWS Equivalent:** Direct Connect

### VPC & Networking

**Q: Low latency + redundancy**
- Scenario: <10ms latency between VMs, need redundancy
- Options: A) Single zone B) Different zones, same region C) Multiple regions, one zone D) Multiple regions, multiple zones
- **Answer: B** - Different zones within same region
- **Why:** Zones are close (low latency) but separate (redundancy)
- **AWS Equivalent:** Multi-AZ deployment in same region

---

## Security & Identity

### IAM (Identity & Access Management)

**Q: Active Directory integration**
- Scenario: Remove Google access when AD account terminated
- Options: A) Two-factor auth B) Remove from IAM policies C) BeyondCorp D) Single Sign-On
- **Answer: D** - Configure Single Sign-On (SSO)
- **Why:** Centralized identity, automatic deprovisioning
- **AWS Equivalent:** AWS SSO with AD integration

### Security Command Center

**Q: Security vulnerability scanning**
- Scenario: Identify VMs with outdated OS images
- Options: A) SCC vulnerable disk images B) Compliance Reports PCI C) SCC VMs >2 weeks D) Compliance Reports SOC 1
- **Answer: A** - Security Command Center to identify vulnerable disk images
- **Why:** Centralized security posture, active vulnerability scanning
- **AWS Equivalent:** Security Hub + Inspector

**Q: Org-wide compliance monitoring**
- Scenario: Report compliance across all projects
- Options: A) Cloud Logging B) IAM C) Cloud Armor D) Security Command Center
- **Answer: D** - Security Command Center
- **Why:** Centralized security and compliance view across organization
- **AWS Equivalent:** AWS Security Hub

### Organization Policy

**Q: Restrict external IPs org-wide**
- Scenario: Prevent all VMs from having external IPs, new projects coming
- Options: A) Policy at root node B) Policy on all folders C) Policy on all projects D) Communicate with teams
- **Answer: A** - Organization policy at root organization node
- **Why:** Inherited by all folders/projects automatically
- **AWS Equivalent:** Service Control Policies (SCPs)

---

## Data & Analytics

### Pub/Sub (Messaging)

**Q: Event-driven messaging**
- Scenario: Asynchronous communication between services
- **Answer:** Pub/Sub
- **Why:** Decouples services, handles millions of messages/second
- **AWS Equivalent:** SNS + SQS

### Dataflow (Stream/Batch Processing)

**Q: Streaming data pipelines**
- Scenario: Managed service, auto-scaling, no server management
- Options: A) Pub/Sub B) Dataflow C) Data Catalog D) Dataprep
- **Answer: B** - Dataflow
- **Why:** Fully managed, serverless, Apache Beam-based
- **AWS Equivalent:** Kinesis Data Analytics

### Dataproc (Hadoop/Spark)

**Q: Big data processing**
- Scenario: Need managed Hadoop/Spark clusters
- **Answer:** Dataproc
- **Why:** Fast cluster creation, per-second billing
- **AWS Equivalent:** Amazon EMR

---

## DevOps & CI/CD

### Cloud Build

**Q: Automate build/test/deploy**
- Scenario: Reduce manual work in CI/CD pipeline
- Options: A) Cloud Scheduler B) Cloud Code C) Cloud Build D) Deployment Manager
- **Answer: C** - Cloud Build
- **Why:** Managed CI/CD platform, integrates with repositories
- **AWS Equivalent:** CodeBuild + CodePipeline

---

## Cost Optimization

### Pricing Models

**Q: Cloud cost planning frequency**
- Scenario: How often to review cloud costs?
- Options: A) Frequently B) Annually C) No longer needed D) Fewer people
- **Answer: A** - Review frequently (costs change based on usage)
- **Why:** Cloud costs are dynamic, not fixed like on-prem
- **AWS Equivalent:** Use Cost Explorer regularly

**Key Pricing Concepts:**
- **On-Demand:** Pay-as-you-go, no commitment
- **Committed Use:** 1-3 year commitment, 57% discount
- **Preemptible:** 80% discount, can be terminated
- **Sustained Use:** Automatic discount for running >25% of month

---

## Migration & Hybrid Cloud

### Cloud Models

**Q: Stop managing infrastructure**
- Scenario: Manage workloads globally, stop infrastructure management
- Options: A) Public cloud B) Central office C) Co-location D) Private clouds
- **Answer: A** - Migrate to public cloud
- **Why:** Cloud abstracts infrastructure management
- **AWS Equivalent:** Use AWS managed services

**Q: Multi-country acquisitions**
- Scenario: Reduce overhead, low cost, maintain security
- Options: A) On-premises B) Public cloud C) Homogenous at each subsidiary D) Hire more engineers
- **Answer: B** - Host all services on public cloud
- **Why:** Economies of scale, managed services, global reach
- **AWS Equivalent:** Consolidate to AWS

**Q: Global data residency**
- Scenario: Serve customers worldwide, data must stay in specific geographic area
- Options: A) Provider only in area B) Private cloud global replication C) Public cloud with guaranteed location D) Private cloud in area
- **Answer: C** - Public cloud with guaranteed data location
- **Why:** Global reach + regional compliance
- **AWS Equivalent:** AWS Regions with data residency controls

---

## Organization & Governance

### Shared Responsibility Model

**Q: Public cloud provider responsibilities**
- Scenario: What does cloud provider own?
- Options: A) Hardware maintenance B) Infrastructure architecture C) Deployment automation D) Hardware capacity E) Application security
- **Answer: A & D** - Hardware maintenance + Hardware capacity management
- **Why:** Provider manages physical infrastructure
- **AWS Equivalent:** Same shared responsibility model

---

## Mobile & Web

### Firebase

**Q: Mobile app platform**
- Scenario: Fully featured cloud platform for mobile development
- Options: A) GKE B) Firebase C) Cloud Functions D) App Engine
- **Answer: B** - Firebase
- **Why:** Complete mobile backend (auth, DB, storage, analytics, hosting)
- **AWS Equivalent:** AWS Amplify

---

## Quick Reference: Service Selection Patterns

### When to Choose What

**Compute:**
- Full control needed → **Compute Engine**
- Containers, serverless → **Cloud Run**
- Event-driven, lightweight → **Cloud Functions**
- Complex microservices → **GKE**
- Simple web app, PaaS → **App Engine**

**Database:**
- Relational, regional → **Cloud SQL**
- Relational, global → **Cloud Spanner**
- NoSQL, high throughput → **Bigtable**
- Document, mobile/web → **Firestore**
- Analytics, data warehouse → **BigQuery**

**Storage:**
- Frequent access → **Standard**
- Monthly access → **Nearline**
- Quarterly access → **Coldline**
- Yearly access → **Archive**

**Connectivity:**
- Fast setup needed → **Cloud VPN**
- Sensitive data, no internet → **Partner Interconnect**
- Dedicated, high bandwidth → **Dedicated Interconnect**

---

## Exam Keywords to Watch

- **"Quickly/ASAP"** → Cloud VPN, on-demand, Cloud Run
- **"Cost-optimized"** → Preemptible, appropriate storage class, PAYG
- **"Serverless"** → Cloud Functions, Cloud Run, App Engine
- **"Global"** → Cloud Spanner, Cloud CDN, multi-region
- **"Sensitive data"** → Partner Interconnect, CMEK, VPC Service Controls
- **"Compliance"** → Security Command Center, audit logs
- **"Event-driven"** → Cloud Functions, Pub/Sub
- **"Analytics"** → BigQuery, Dataflow
- **"Mobile"** → Firebase
- **"Container"** → Cloud Run, GKE, Artifact Registry
- **"Millions of sensors"** → Bigtable
- **"Real-time database"** → Firestore
- **"Data warehouse"** → BigQuery
- **"Streaming pipeline"** → Dataflow
- **"CI/CD"** → Cloud Build
- **"Org-wide policy"** → Organization policy at root node

---

## Study Tips

1. **Pattern Recognition:** Most questions test service selection based on requirements
2. **AWS Knowledge:** Leverage your AWS experience - services are very similar
3. **Keywords:** Learn to spot decision keywords (quickly, cost, global, serverless)
4. **Decision Trees:** Memorize the compute, database, storage, connectivity decision flows
5. **Hands-on:** Try free tier services to understand practical differences

**Good luck with your exam! 🚀**
