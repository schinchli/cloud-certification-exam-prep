# How to Pass AWS Certification in 2026 — Complete Roadmap (CLF-C02 to SAP-C02)

> Written by a **13x AWS Certified architect** (AWS Golden Jacket). Covers every AWS certification path from foundational to professional with study plans, common mistakes, and exam strategy.

---

## Which AWS Certification Should You Take First?

This is the most common question — and the answer depends on where you are right now:

| Your Background | Start With |
|---|---|
| Non-technical (business, sales, management) | AWS Cloud Practitioner (CLF-C02) |
| Developer with no AWS exp | AWS Cloud Practitioner (CLF-C02) → SAA-C03 |
| Experienced developer / sysadmin | Skip CLF-C02 → Go straight to SAA-C03 |
| Architect or senior engineer | SAA-C03 → SAP-C02 |
| AI / ML focus | SAA-C03 or AIF-C01 depending on role |

**The highest ROI cert in the market is SAA-C03.** It opens doors to cloud architect and senior engineer roles. Start there unless you truly need the foundational CLF-C02 first.

---

## Full AWS Certification Path

```
FOUNDATIONAL
└── AWS Certified Cloud Practitioner (CLF-C02)
      │ 4–6 weeks study
      │ Best for: non-technical or first-time cloud learners
      ▼
ASSOCIATE
├── AWS Certified Solutions Architect – Associate (SAA-C03)   ← HIGHEST ROI
├── AWS Certified Developer – Associate (DVA-C02)
└── AWS Certified SysOps Administrator – Associate (SOA-C02)
      │
      ▼
SPECIALTY
├── AWS Certified AI Practitioner (AIF-C01)
├── AWS Certified ML Engineer – Associate (MLA-C01)
├── AWS Certified Machine Learning – Specialty (MLS-C01)
├── AWS Certified Security – Specialty (SCS-C02)
├── AWS Certified Database – Specialty (DBS-C01)
└── AWS Certified Advanced Networking – Specialty (ANS-C01)
      │
      ▼
PROFESSIONAL
├── AWS Certified Solutions Architect – Professional (SAP-C02)
└── AWS Certified DevOps Engineer – Professional (DOP-C02)
```

---

## AWS Cloud Practitioner (CLF-C02) Study Plan

**Time required:** 4–6 weeks (1 hour/day)

| Week | Focus |
|---|---|
| Week 1 | Cloud concepts: IaaS vs PaaS vs SaaS, shared responsibility, global infrastructure |
| Week 2 | Core services: EC2, S3, RDS, VPC, IAM, Lambda |
| Week 3 | Security, compliance, support plans, billing and cost management |
| Week 4 | Practice exams — target 80%+ before booking |

**Key domains:**
- Cloud Concepts (24%)
- Security and Compliance (30%)
- Cloud Technology and Services (34%)
- Billing, Pricing, and Support (12%)

**Official resources:**
- [AWS Cloud Practitioner Essentials](https://explore.skillbuilder.aws/learn/course/134) — free on Skill Builder
- [CLF-C02 Official Practice Exam](https://explore.skillbuilder.aws) — $29 for official questions
- [CLF-C02 Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-cloud-practitioner/AWS-Certified-Cloud-Practitioner_Exam-Guide.pdf)

**Pass target:** 700/1,000 (score 750+ to be safe)

---

## AWS Solutions Architect Associate (SAA-C03) Study Plan

**Time required:** 6–10 weeks (1–2 hours/day)

| Week | Focus |
|---|---|
| Week 1–2 | EC2, IAM, S3, VPC fundamentals |
| Week 3 | RDS, Aurora, DynamoDB, ElastiCache |
| Week 4 | Load balancers, Auto Scaling, Route 53, CloudFront |
| Week 5 | Lambda, SQS, SNS, EventBridge, Step Functions |
| Week 6 | Security: KMS, Secrets Manager, GuardDuty, Config, CloudTrail |
| Week 7 | Storage: EBS, EFS, FSx, Storage Gateway, Snow |
| Week 8–9 | Architecture patterns — HA, DR, cost optimization |
| Week 10 | Practice exams — target 85%+ before booking |

**Key exam domains:**
- Design Secure Architectures (30%) ← heaviest domain
- Design Resilient Architectures (26%)
- Design High-Performing Architectures (24%)
- Design Cost-Optimized Architectures (20%)

**Exam strategy:**
- Every question is a scenario — think "what is the BEST solution" not just "what works"
- BEST = most available, most secure, MOST cost-effective, or most operationally simple
- Eliminate obviously wrong answers first (2 of 4 are usually easy to rule out)
- "Fully managed" clues → Lambda, Fargate, DynamoDB, RDS (not EC2)
- "Decouple" clue → SQS
- "Fan-out" clue → SNS → SQS
- "Least operational overhead" → always the managed/serverless option

**Cheatsheet:** [→ AWS SAA-C03 Cheatsheet](../cheatsheets/aws-saa-c03.md)  
**Official guide:** [SAA-C03 Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate_Exam-Guide.pdf)

---

## AWS Solutions Architect Professional (SAP-C02) Study Plan

**Time required:** 10–16 weeks (1.5–2 hours/day)

> Do not attempt SAP-C02 without passing SAA-C03 first and having at least 1 year of real AWS experience.

| Module | Topics | Notes |
|---|---|---|
| Accounts & Identity | IAM advanced, Organizations, SCPs, Control Tower | [Notes](../AWS/SAP-C02/01-accounts/) |
| Networking | VPC, Transit Gateway, Direct Connect, BGP, PrivateLink | [Notes](../AWS/SAP-C02/03-networking/) |
| Storage | S3 advanced, FSx, EFS, Storage Gateway, Snow | [Notes](../AWS/SAP-C02/04-storage/) |
| Compute | EC2 advanced, ASG, ELB, Lambda edge cases | [Notes](../AWS/SAP-C02/05-compute/) |
| Databases | RDS, Aurora, DynamoDB advanced patterns | [Notes](../AWS/SAP-C02/07-databases/) |
| Security | KMS, CloudHSM, Inspector, GuardDuty, Security Hub | [Notes](../AWS/SAP-C02/12-security-and-config/) |
| Disaster Recovery | RTO/RPO strategies, pilot light, warm standby | [Notes](../AWS/SAP-C02/13-disaster-recovery/) |
| IaC | CloudFormation advanced, CDK, Service Catalog | [Notes](../AWS/SAP-C02/14-iac/) |
| Deployment | CodePipeline, CodeDeploy, Elastic Beanstalk, OpsWorks | [Notes](../AWS/SAP-C02/15-deployment/) |

---

## 5 Mistakes That Cause People to Fail AWS Exams

**1. Studying theory without hands-on practice**
Reading about EC2 is not the same as launching one. Use the AWS Free Tier.

**2. Using braindumps**
They change the exam regularly. Dumps get you familiar with outdated questions, not the concepts you need.

**3. Skipping the exam guide**
The official exam guide tells you exactly what domains are tested and at what weight. Read it first.

**4. Underestimating the security domain (SAA-C03)**
Security is 30% of SAA-C03. Most people under-prepare it. Study IAM, KMS, GuardDuty, Config, CloudTrail.

**5. Booking the exam before you're ready**
You should be scoring 80–85% on full practice exams before booking. AWS Skill Builder practice tests are the most accurate proxy.

---

## AWS Certification ROI in 2026

| Cert | Average Salary Impact | Demand |
|---|---|---|
| CLF-C02 | +$5K–15K (entry positions) | High |
| SAA-C03 | +$15K–30K | Very High |
| SAP-C02 | +$25K–50K | High |
| SCS-C02 | +$20K–40K | High |
| MLS-C01 | +$25K–50K | Very High |

*Salary ranges are market estimates — actual impact varies by role, location, and experience.*

---

## Hands-On Labs in This Repo

Practice the security services that appear on every AWS exam:

- [AWS KMS Masterclass](../AWS/security-labs/AWS%20KMS%20Masterclass%20-%20Encryption,%20Key%20Rotation,%20and%20Multi-Region%20Keys%20(Hands-On%20Lab)/) — encryption, key rotation, multi-region
- [CloudFront WAF Edge Security](../AWS/security-labs/CloudFront%20WAF%20Edge%20Security/) — WAF rules, rate limiting
- [RDS + Secrets Manager + KMS](../AWS/security-labs/Securing%20RDS%20Database%20Credentials%20with%20AWS%20KMS%20and%20Secrets%20Manager%20(Hands-On,%20Zero-Downtime%20Rotation)/) — zero-downtime rotation

---

## Want to Accelerate Your Path?

Skip the guesswork. Work 1:1 with **Shashank Chinchli** — Sr. Solutions Architect at GitLab, ex-AWS, 13x AWS Certified, AWS Golden Jacket recipient.

**[→ Book a session on Topmate](https://topmate.io/heyshashank)**

What you get:
- Personalized study plan based on your current role and goal cert
- Exam strategy for SAA-C03 or SAP-C02
- Architecture review and scenario coaching
- Career positioning for cloud architect roles

---

← [Back to main repo](../README.md) | [AWS SAA-C03 Cheatsheet →](../cheatsheets/aws-saa-c03.md) | [GCP Roadmap →](./gcp-certification-guide.md)
