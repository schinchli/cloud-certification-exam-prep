# AWS Core Services Cheatsheet

> Quick reference for SAA-C03 and core AWS certification exams.

---

## Compute

| Service | Use Case |
|---|---|
| EC2 | Virtual machines, full OS control |
| Lambda | Serverless functions, event-driven, no server management |
| ECS | Docker containers on managed clusters |
| EKS | Managed Kubernetes |
| Fargate | Serverless containers (no EC2 to manage) |
| Elastic Beanstalk | Deploy apps without managing infrastructure |

## Storage

| Service | Type | Use Case |
|---|---|---|
| S3 | Object | Unstructured data, static websites, backups |
| EBS | Block | EC2 persistent disks, databases |
| EFS | File | Shared NFS storage across EC2 instances |
| S3 Glacier | Object (archive) | Long-term archival, infrequent access |

## Database

| Service | Type | Use Case |
|---|---|---|
| RDS | Relational | MySQL, PostgreSQL, SQL Server, Oracle |
| Aurora | Relational | High-performance MySQL/PostgreSQL compatible |
| DynamoDB | NoSQL (key-value) | Single-digit ms latency, serverless scale |
| ElastiCache | In-memory | Redis/Memcached caching layer |
| Redshift | Data warehouse | Analytics, large-scale SQL queries |

## Networking

| Service | Use Case |
|---|---|
| VPC | Isolated virtual network |
| CloudFront | Global CDN, edge caching |
| Route 53 | DNS, health checks, routing policies |
| ALB | Layer 7 load balancing (HTTP/HTTPS) |
| NLB | Layer 4 load balancing (TCP/UDP, low latency) |
| API Gateway | Managed REST/WebSocket APIs |
| NAT Gateway | Outbound internet for private subnets |

## Security

| Service | Use Case |
|---|---|
| IAM | Users, roles, policies, MFA |
| KMS | Encryption key management |
| Secrets Manager | Store and rotate credentials |
| WAF | Web application firewall |
| Shield | DDoS protection |
| GuardDuty | Threat detection |
| Inspector | Vulnerability scanning |

## Integration

| Service | Use Case |
|---|---|
| SQS | Message queue, decouple services |
| SNS | Pub/sub notifications, fan-out |
| EventBridge | Event bus, rule-based routing |
| Step Functions | Serverless workflow orchestration |

---

*Source: [AWS Documentation](https://docs.aws.amazon.com) · [AWS Skill Builder](https://skillbuilder.aws)*
