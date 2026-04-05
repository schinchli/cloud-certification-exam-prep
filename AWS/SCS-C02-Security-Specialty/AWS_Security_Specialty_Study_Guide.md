# AWS Certified Security - Specialty Study Guide

## Table of Contents
1. [Security Basics](#chapter-1-security-basics)
2. [AWS Security 101](#chapter-2-aws-security-101)
3. [IAM, S3, Security Policies](#chapter-3-iam-s3-security-policies)
4. [Logging and Monitoring](#chapter-4-logging-and-monitoring)
5. [Infrastructure Security](#chapter-5-infrastructure-security)
6. [VPC and Network Security](#chapter-6-vpc-and-network-security)
7. [Other Security Services](#chapter-7-other-security-services)
8. [Troubleshooting Security Scenarios](#chapter-8-troubleshooting-security-scenarios)
9. [DDoS and Incident Response](#chapter-9-ddos-and-incident-response)
10. [Exam Gotchas and Distractors](#chapter-10-exam-gotchas-and-distractors)
11. [Miscellaneous Exam Tips](#chapter-11-miscellaneous-exam-tips)

---

## Chapter 1: Security Basics

> **Important**: IAM is critical for the security exam. Know it inside out!

### The CIA Triad

Key mental models fundamental to understanding security objectives:

#### Confidentiality
- Principle that certain things should be kept uniquely accessible and privately segmented
- Examples: keys, passwords, medical records, identifying data
- **Related services**: IAM, MFA, encryption at rest/in transit, Macie

#### Integrity
- Principle of consistency within a system with expected immutability
- System should be verifiably unchanged to the expected degree
- **Related services**: GuardDuty, IAM, Bucket Policies, encryption, vaults, MFA delete

#### Availability
- System should be usable to the degree relevant for the system
- Should not become unavailable at inappropriate times
- **Related services**: HA, Multi-AZ, AWS Backup, disaster recovery, failovers

### AAA Model
- **Authentication** - Verifying identity
- **Authorization** - Granting permissions
- **Accounting** - Tracking activities

### Non-repudiation
- You cannot deny that you performed an action

### Essential Reading
- [AWS Security Reference Architecture](https://docs.aws.amazon.com/pdfs/prescriptive-guidance/latest/security-reference-architecture/security-reference-architecture.pdf)
- [AWS Security Identity & Compliance](https://aws.amazon.com/architecture/security-identity-compliance/)

---

## Chapter 2: AWS Security 101

### Shared Responsibility Model

Services fall under 3 types:

| Type | Services | Your Responsibility |
|------|----------|---------------------|
| **Infrastructure** | EC2, EBS, VPC | Similar to datacenter security |
| **Containerized** | RDS, EMR, Beanstalk | No OS access, service-level security |
| **Abstracted** | S3, DynamoDB, SNS, SES | API endpoints, access control |

### Security Controls (5 Categories)

| Control | Service | Purpose |
|---------|---------|---------|
| Visibility | **Config** | Inventory and configuration history |
| Auditability | **CloudTrail** | Who, what, when, how, from where |
| Controllability | **KMS, CloudHSM** | Control your keys |
| Agility | **CloudFormation** | Repeatable, auditable updates |
| Automation | **OpsWorks, CodeDeploy** | Automated security updates |

---

## Chapter 3: IAM, S3, Security Policies

### IAM Core Concepts

- **Roles** are typically assigned to services but can be assumed by IAM users
- **PowerUsers** have access to everything EXCEPT IAM
- Customer managed policies exist only within 1 account (cannot share)

### IAM Policy Size Limits
| Entity | Size Limit |
|--------|------------|
| Users | 2KB |
| Groups | 5KB |
| Roles | 10KB |

### IAM Best Practices
- **Never** create access keys for root account - delete if they exist
- Enable MFA on root account (tip: screenshot QR code and store safely)
- Use IAM Credentials Report for auditing (CSV with all user details)
- Understand `NotAction` in policies for both Deny and Allow effects

### S3 Bucket Policies & ACLs

**Key Rules:**
- Bucket policies can be granular to user level but NOT object level
- Bucket policies have 20KB size limit
- **Tip**: Add `/*` after ARN in Resource section to refer to bucket contents

### S3 Access Resolution

```
┌──────────────────────────────────────────────────┐
│           S3 Access Conflict Resolution          │
├──────────────────────────────────────────────────┤
│ 1. Is there Explicit DENY? → DENIED (period)     │
│ 2. No Deny + Any ALLOW? → ALLOWED (same account) │
│ 3. No Deny + No Allow? → Implicit DENIED         │
└──────────────────────────────────────────────────┘
```

**Cross-account**: Requires BOTH resource-based AND IAM policy explicit ALLOW

### S3 ACLs (Legacy)
- Can provide fine-grained permissions at object level
- Can only grant read/write to OTHER accounts, not users in your own account
- Can only ALLOW, not explicit DENY

### Cross Region Replication (CRR)

**Requirements:**
- Both source and destination buckets need versioning enabled
- S3 needs permission to read/write objects (role policy)
- If object owner ≠ bucket owner, object owner must grant permission via ACL

**CRR Replicates:**
- Unencrypted objects
- SSE-S3 encrypted objects
- SSE-KMS encrypted (only if enabled)
- Object metadata, ACL updates, tags, delete markers

**CRR Does NOT Replicate:**
- Older objects (before CRR enabled)
- Objects where bucket owner lacks permission
- Specific versions of source objects

### STS and Federation

**STS Methods:**
1. AD federation (based on AD credentials)
2. Mobile app federation (Google/FB/OpenID)
3. Other AWS accounts

**Federation Process:**
1. User logs in to Identity Broker → authenticates against LDAP
2. Identity Broker contacts STS using `GetFederationToken`
3. STS returns token (access key, secret key, token, duration)
4. User accesses S3 with token, validated against IAM

### Cognito

| Component | Purpose |
|-----------|---------|
| **User Pools** | Directory of user logins, generates JWTs |
| **Identity Pools** | Creates unique identity, generates temp credentials |

> User pools = Authentication (identity verification)
> Identity pools = Authorization (access control)

### Glacier Vault Lock
- Vault lock policies apply to ALL archives within a vault
- **24 hours** to validate policy, then **CANNOT change forever**
- Example: Deny DeleteArchive if AgeInDays < 365

### Organizations SCPs
- Apply to OUs or individual accounts
- SCPs do NOT affect service-linked roles
- SCPs don't affect management account users/roles
- SCPs do NOT grant access - they set guardrails
- Default: Allow * * (no guardrails, rely on IAM)

---

## Chapter 4: Logging and Monitoring

### CloudTrail

- Logs **API calls only** (not SSH/RDP - use VPC Flow Logs for that)
- Logs: metadata, requester identity, time, source IP, parameters, response
- Delivery: Every 5 minutes, up to 15 min delay
- Default: Enabled for 90 days in AWS-owned S3 bucket
- **Data events** (S3 GetObject/PutObject) not enabled by default - can be expensive

**Log Protection:**
1. IAM
2. Bucket policy
3. MFA delete + log file validation

### CloudWatch

- Detailed monitoring: 1 min refresh
- Standard monitoring: 5 min refresh
- Logs stored indefinitely (NOT in your S3)

**CloudWatch Events Sources:**
- CloudTrail
- Resource state changes
- Scheduled events (cron)
- Custom events

**Root Login Alert Setup:**
1. CloudTrail trail → CloudWatch Log group
2. Create Metric Filter: `userIdentity.type = Root`
3. Create Alarm: ≥1 occurrence → SNS notification

### VPC Flow Logs

- Captures IP traffic metadata (NOT packet data)
- Can be published to CloudWatch Logs or S3
- Levels: VPC, subnet, or network interface

**Flow Logs DO NOT Monitor:**
- EC2 to Amazon DNS traffic
- Windows license activation
- Instance metadata traffic
- DHCP traffic
- VPC router reserved IP
- Amazon Time Sync Service
- Mirrored traffic
- Endpoint to NLB traffic

### AWS Config

- Provides: resource inventory, configuration history, change notifications
- Must be enabled **per region**
- Needs IAM role with: read all resources, S3 access, SNS publish

**Config Timeline**: View history of all changes to any resource

### CloudHSM

| Feature | Detail |
|---------|--------|
| Compliance | FIPS 140-2 Level 3, EAL-4 |
| Keys | Symmetric and asymmetric |
| Hardware | Dedicated single tenant |

**User Types:**
- **PRECO** - Default first-time login
- **CO (Crypto Officer)** - Create/delete users, change passwords
- **CU (Crypto User)** - Key management and crypto operations
- **AU (Appliance User)** - Appliance management

**Security:**
- 5 failed CO attempts → HSM erases itself
- 5 failed CU attempts → user locked (CO must unlock)

---

## Chapter 5: Infrastructure Security

### KMS

- Keys are **region-bound** (multi-region now available)
- Cannot delete KMS keys immediately (7-day minimum cooling period)
- Imported keys CAN be deleted immediately
- CMK can encrypt up to **4KB** - use data keys for larger data

**Key Rotation:**

| Key Type | Rotation |
|----------|----------|
| AWS managed | Auto every 1 year |
| Customer managed (AWS generated) | Auto every 1 year (disabled by default) |
| Customer managed (imported) | Manual only |
| Asymmetric CMK | Not supported |

**KMS Grants:**
- Allow use of CMK to other users/accounts
- Can only ALLOW, not DENY
- CLI only: `create-grant`, `list-grants`, `revoke-grant`

**Key Conditions:**
- `kms:ViaService` - Restrict which services can use the CMK
- `kms:ValidTo` - Time-based restrictions

**Cross-Account Access:**
1. Change key policy in KMS account
2. Add IAM policy in external account with key ARN

**Encryption Context:**
- Key-value pair submitted while encrypting
- Required again for decryption
- Visible in CloudTrail (not secret)

### EC2 and EBS Keys

**EBS Encryption:**
- Volumes and snapshots always encrypted if created encrypted
- Unencrypted → encrypted: snapshot → copy encrypted → create volume

**Lost EC2 Key Recovery:**
1. Create new key pair
2. Stop original instance
3. Launch temp instance
4. Detach root volume, attach to temp
5. Add new public key to authorized_keys
6. Reattach volume, start instance

### WAF and Shield

**WAF Rules Match On:**
- IP, country, header values
- Regex strings, request length
- SQL injection, XSS

**WAF Protects:**
- CloudFront, ALB, API Gateway
- AppSync, Cognito User Pools, Verified Access

### Systems Manager Session Manager

- Browser-based secure remote login (PowerShell/Bash)
- No SSH keys or bastion host needed
- Requires outbound 443 (or VPC endpoint)
- All commands logged in CloudWatch, connections in CloudTrail

---

## Chapter 6: VPC and Network Security

### VPC Basics

- New VPC creates: default SG, default NACL, route table
- Reserved IPs: first 4 + last 1 (network, router, DNS, future, broadcast)
- Each VPC can have only 1 IGW

### NACL vs Security Groups

| Feature | NACL | Security Group |
|---------|------|----------------|
| State | Stateless | Stateful |
| Scope | Subnet level | Instance level |
| Rules | Allow and Deny | Allow only |
| Rule Order | By number (lower wins) | Most permissive wins |
| Ephemeral Ports | Must explicitly allow | Automatic |

### VPC Endpoints

| Type | Services | Cost |
|------|----------|------|
| **Gateway Endpoint** | S3, DynamoDB | FREE |
| **Interface Endpoint** | Everything else (+ S3) | Charged |

> **Tip**: For "most cost effective" questions, remember Gateway Endpoints are free!

### Transit Gateway
- Any VPC connected becomes available to all others
- Traffic always flows over AWS private network (including inter-region)
- Use route tables to control access

### CloudHSM Networking
- Must be in same region as VPC and resources
- Creates SG with ports 2223-2225
- Cluster requires at least 2 AZs

---

## Chapter 7: Other Security Services

### Amazon Macie
- Identifies PII in S3
- Analyzes CloudTrail logs for sensitive data access auditing
- Classification: content type, file extensions, themes, keywords, regex

### Amazon GuardDuty
- Monitors: CloudTrail, VPC Flow Logs, DNS logs, S3 data events
- Threat feeds from Proofpoint, CrowdStrike, AWS research
- **Needs 7-14 days** to establish baseline before findings

**Detects:**
- Unusual API calls, disabled CloudTrail logging
- Unauthorized deployments, compromised instances
- Port scanning, failed logins

### Secrets Manager vs Parameter Store

| Feature | Secrets Manager | Parameter Store |
|---------|-----------------|-----------------|
| RDS Integration | Built-in | No |
| Auto-rotation | Yes | No |
| Cross-account | Yes | No |
| Cross-region replication | Yes | No |
| Cost | Paid | Free |

### Security Hub
- Aggregates alerts from: GuardDuty, Macie, Inspector, IAM Access Analyzer, Firewall Manager
- **NOT CloudTrail directly**
- Automated checks for PCI-DSS and CIS requirements
- **Requires AWS Config to be enabled first**

### Amazon Detective
- Analyzes findings from GuardDuty, Macie, Security Hub
- Uses ML and graphs for root cause analysis

### AD Federation
- SAML enables SSO for AWS accounts

**Login Flow:**
1. User signs in to ADFS with corp login
2. ADFS sends SAML token to AWS sign-in
3. AWS calls STS `AssumeRoleWithSAML`
4. User redirected to AWS console

---

## Chapter 8: Troubleshooting Security Scenarios

### CloudWatch Issues
- Check IAM: `cloudwatch:Get`, `cloudwatch:List` permissions
- Verify CloudWatch agent is installed and running
- Check EC2 role has permission to write to CloudWatch Logs

### CloudTrail Issues
- Is CloudTrail enabled?
- S3 bucket name/prefix correct?
- Bucket policy configured?
- S3/Lambda Data events enabled? (not default)

### Network Connectivity
Check in order:
1. Subnet
2. Routing table
3. Security Group rules
4. NACL rules (inbound + outbound)
5. NAT Gateway
6. Internet Gateway

### Authentication/Authorization
- Evaluate least privilege
- Check Organizations service boundaries
- Cross-account: Check trust policies

**STS Role Types:**
| API | Use Case |
|-----|----------|
| `AssumeRoleWithWebIdentity` | FB, Google, OpenID |
| `AssumeRoleWithSAML` | AD, SAML providers |
| `AssumeRole` | AWS authenticated |

### Lambda Issues
- **Function policy** = what can trigger Lambda
- **Execution role** = what Lambda can access
- Needs explicit Secrets Manager permission for RDS credentials

---

## Chapter 9: DDoS and Incident Response

### DDoS Attack Types

**Amplification/Reflection:**
- Spoof IP, send request to third party (e.g., NTP)
- Response (50x larger) sent to victim

**Slowloris:**
- Multiple connections with partial HTTP requests
- Server runs out of concurrent connections
- Not caught by regular rate control

### Shield Advanced
- Flow-based monitoring at L7
- Price protection against usage spikes during attacks
- Protected: EC2, ELB, CloudFront, Global Accelerator, Route 53

### Incident Response for Hacked EC2
1. Stop the instance
2. Take EBS snapshot
3. Terminate instance
4. Create new instance in new VPC (private subnet)
5. Analyze logs

### Exposed Credentials
- **IAM users**: Deactivate then delete from IAM
- **Root**: Deactivate from "Security credentials" section

---

## Chapter 10: Exam Gotchas and Distractors

### Route53 DNS Logging
- Can log queries for public AND private hosted zones
- Logs: domain, time, record type, edge location, response code

### STS AssumeRole Types

| Type | Duration | Use Case |
|------|----------|----------|
| `AssumeRole` | 15 min - 12 hrs (default 1 hr) | Same/cross account access |
| `AssumeRoleWithSAML` | AD/SAML authenticated | Corporate SSO |
| `AssumeRoleWithWebIdentity` | FB/Google/Cognito | Mobile/web apps |
| `GetFederationToken` | Federated users | Internal apps |
| `GetSessionToken` | MFA-protected API calls | Additional security |

### VPC Quick Facts
- NAT Gateway goes in **public** subnet
- EC2 port 25 throttled by default (use 587 or request removal)
- Peering requires route table updates on BOTH VPCs

### Penetration Testing
**No approval needed:**
- EC2, RDS, Aurora, CloudFront, API Gateway
- Lambda, Lightsail, Beanstalk, ECS, Fargate
- Elasticsearch, FSx, Transit Gateway, S3-hosted apps

**Not allowed:**
- DNS zone walking, DDoS simulation
- Port/protocol/request flooding

### S3 Encryption Headers
- `AES256` = SSE-S3
- `aws:kms` = KMS encryption

### Elasticache Encryption
- Memcached: **No**
- Redis: **Yes**

### Direct Connect (DX)
- NOT always encrypted in transit
- Uses 802.1q VLAN with multiple virtual interfaces

---

## Chapter 11: Miscellaneous Exam Tips

### ACM Certificates
- Imported certs DO NOT auto-renew
- Public certs auto-renew if: in use + DNS validation
- Works with: CloudFront, ALB, Beanstalk, API Gateway, Nitro Enclaves
- **Not EC2 directly** (use IAM Certificate Store as workaround)

### API Gateway
- Throttling: 10,000/sec steady + 5,000 burst
- Response: 429 Too Many Requests
- Cache: default 300 sec, max 3600 sec

### Perfect Forward Secrecy
- Use ECDHE-* ciphers on ALB
- Prevents future traffic decryption if key compromised

### Memory/EBS Scrubbing
- Memory: Scrubbed immediately when unallocated
- EBS: Scrubbed before reuse (not immediately after deletion)

### Key CloudWatch Permissions for Lambda
- `CreateLogGroup`
- `CreateLogStream`
- `PutLogEvents`

### Compromised Account Response
1. Change root user password
2. Delete/rotate all root and IAM access keys
3. Delete compromised IAM users, change other passwords
4. Delete unauthorized resources

### Inspector vs Config

| Service | Focus |
|---------|-------|
| **Inspector** | Application vulnerabilities, exposure, best practices |
| **Config** | Resource configuration monitoring and compliance |

### Important Reminders
- NACL needs ephemeral ports (1024-65535) for outbound replies
- KMS aliases cannot be used in policies (use key IDs)
- S3 access logs cannot go to CloudWatch Logs
- AWS Config Conformance Pack deploys rules + remediation as single entity

---

## Quick Reference Cards

### Security Service Comparison

| Service | Purpose |
|---------|---------|
| **GuardDuty** | Threat detection (ML-based) |
| **Inspector** | Vulnerability assessment |
| **Macie** | PII discovery in S3 |
| **Security Hub** | Central security dashboard |
| **Detective** | Root cause analysis |
| **Config** | Configuration compliance |

### Encryption Options

| Type | Key Management | Use Case |
|------|----------------|----------|
| SSE-S3 | AWS managed | Simple encryption |
| SSE-KMS | Customer managed | Audit trail needed |
| SSE-C | Customer provided | Customer controls keys |
| Client-side | Customer managed | Encrypt before upload |

---

*Last Updated: January 2026*
*Exam Code: SCS-C02*
*Exam Duration: 170 minutes*
*Passing Score: 750/1000*
