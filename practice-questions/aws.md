# AWS Certification Practice Questions

> Sample questions covering core AWS certification domains.  
> Source: [AWS Skill Builder](https://skillbuilder.aws) — official practice questions available after free registration.

---

## Where to Get Official Practice Questions

| Exam | Official Practice |
|---|---|
| All AWS certs | [AWS Skill Builder — Official Practice Exams](https://skillbuilder.aws) (free + paid) |
| Solutions Architect Associate (SAA-C03) | [SAA-C03 Practice Set](https://explore.skillbuilder.aws/learn/catalog?ctldoc-catalog-0=se-practice%20exam~l-_en) |
| AI Practitioner (AIF-C01) | [AIF-C01 Practice Set](https://explore.skillbuilder.aws) |
| GenAI Developer (AIP-C01) | [AIP-C01 Practice Set](https://explore.skillbuilder.aws) |

---

## SAA-C03 — Key Domain Areas

| Domain | Weight |
|---|---|
| Design Resilient Architectures | 26% |
| Design High-Performing Architectures | 24% |
| Design Secure Architectures | 30% |
| Design Cost-Optimized Architectures | 20% |

*Source: [AWS SAA-C03 Exam Guide](https://d1.awsstatic.com/training-and-certification/docs-sa-assoc/AWS-Certified-Solutions-Architect-Associate_Exam-Guide.pdf)*

---

## Sample Questions (SAA-C03 Format)

**Q1.** A company needs a storage solution for frequently accessed data with the lowest latency. Which AWS service is most appropriate?

- A. Amazon S3 Standard
- B. Amazon EBS (gp3) ✅
- C. Amazon S3 Glacier
- D. Amazon EFS

> **Why B:** EBS gp3 provides block storage with single-digit millisecond latency for EC2 workloads. S3 is object storage with higher latency.

---

**Q2.** An application must remain available if a single Availability Zone fails. What is the minimum architecture?

- A. Deploy in one AZ with Auto Scaling
- B. Deploy in two AZs behind an Application Load Balancer ✅
- C. Deploy in one AZ with a standby instance
- D. Use CloudFront to cache content globally

> **Why B:** Multi-AZ deployment with an ALB is the standard pattern for AZ-level fault tolerance.

---

**Q3.** A company wants to decouple a producer application from a consumer application to handle traffic spikes. Which service is most appropriate?

- A. Amazon SNS
- B. Amazon SQS ✅
- C. Amazon EventBridge
- D. AWS Step Functions

> **Why B:** SQS is a managed message queue that decouples producers from consumers and absorbs traffic spikes via buffering.

---

*For the full official practice exam, register free at [skillbuilder.aws](https://skillbuilder.aws).*
