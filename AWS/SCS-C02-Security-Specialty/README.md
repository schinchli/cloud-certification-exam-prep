# AWS Certified Security - Specialty

This folder contains comprehensive study materials for the AWS Certified Security - Specialty (SCS-C02) exam.

## Contents

- `AWS_Security_Specialty_Study_Guide.md` - Complete study guide organized by exam domains

## Exam Overview

The AWS Certified Security - Specialty validates advanced expertise in securing AWS workloads and architectures.

### Domain Breakdown

| Domain | Weight | Topics |
|--------|--------|--------|
| **1. Threat Detection & Incident Response** | 14% | GuardDuty, Security Hub, incident handling |
| **2. Security Logging & Monitoring** | 18% | CloudTrail, CloudWatch, VPC Flow Logs, Config |
| **3. Infrastructure Security** | 20% | VPC, NACLs, Security Groups, WAF, Shield |
| **4. Identity & Access Management** | 16% | IAM, STS, Cognito, Organizations, SCPs |
| **5. Data Protection** | 18% | KMS, CloudHSM, encryption strategies |
| **6. Management & Security Governance** | 14% | Compliance, governance frameworks |

### Key Services to Master

#### Identity & Access
- **IAM** - Policies, roles, trust relationships, SCPs
- **STS** - AssumeRole variations, federation
- **Cognito** - User pools, identity pools, SAML
- **Organizations** - SCPs, account management

#### Detection & Monitoring
- **GuardDuty** - Threat detection, findings
- **Security Hub** - Aggregated security view
- **CloudTrail** - API logging, log integrity
- **CloudWatch** - Logs, metrics, alarms
- **Config** - Resource compliance, rules

#### Infrastructure Protection
- **VPC** - NACLs, Security Groups, endpoints
- **WAF** - Web application firewall rules
- **Shield** - DDoS protection
- **Firewall Manager** - Central policy management

#### Data Protection
- **KMS** - Key management, rotation, grants
- **CloudHSM** - Hardware security modules
- **Macie** - PII discovery
- **Secrets Manager** - Credentials management

### Exam Details

| Attribute | Value |
|-----------|-------|
| **Duration** | 170 minutes |
| **Questions** | 65 multiple choice/multiple response |
| **Passing Score** | 750/1000 |
| **Cost** | $300 USD |
| **Validity** | 3 years |

## Study Approach

### Phase 1: Foundation (Week 1-2)
- Review IAM fundamentals thoroughly
- Understand the Shared Responsibility Model
- Study CIA triad and AAA model
- Complete AWS Security Fundamentals course

### Phase 2: Core Services (Week 3-5)
- Deep dive into KMS, CloudHSM
- Master VPC security (NACLs, SGs, endpoints)
- Study detection services (GuardDuty, Security Hub)
- Practice with CloudTrail and Config

### Phase 3: Advanced Topics (Week 6-7)
- Cross-account access patterns
- Federation and SSO configurations
- Incident response procedures
- Encryption strategies

### Phase 4: Practice & Review (Week 8)
- Take practice exams
- Review weak areas
- Hands-on labs
- Final preparation

## Critical Exam Topics

### Must-Know Concepts

1. **IAM Policy Evaluation**
   - Explicit Deny > Explicit Allow > Implicit Deny
   - Cross-account requires both resource AND identity policies

2. **KMS Key Types**
   - AWS managed vs Customer managed
   - Rotation policies and limitations
   - Grants vs Key policies

3. **Network Security**
   - NACL stateless vs SG stateful
   - Ephemeral ports for NACLs
   - Gateway vs Interface endpoints

4. **Logging Architecture**
   - CloudTrail for API calls
   - VPC Flow Logs for network traffic
   - Config for resource changes

5. **Encryption Strategies**
   - SSE-S3 vs SSE-KMS vs SSE-C
   - Client-side encryption options
   - Encryption in transit requirements

### Common Exam Traps

- KMS key aliases cannot be used in policies
- SCPs don't affect the management account
- Gateway endpoints are FREE (cost-effective solutions)
- GuardDuty needs 7-14 days baseline
- CloudHSM erases after 5 failed CO attempts

## Success Tips

1. **Hands-on Practice**: Use AWS Free Tier for practical experience
2. **Understand Relationships**: How services integrate for security solutions
3. **Know the Limits**: Policy sizes, rotation periods, retention limits
4. **Read Whitepapers**: Security Reference Architecture, Well-Architected Security Pillar
5. **Practice Troubleshooting**: Common security scenarios and resolutions

## Recommended Resources

### AWS Materials
- AWS Security Specialty Exam Guide
- AWS Security Best Practices whitepaper
- AWS Security Reference Architecture
- AWS Well-Architected Framework - Security Pillar

### Practice
- AWS Skill Builder practice exams
- Tutorials Dojo practice tests
- Hands-on labs with security services

Good luck with your certification!
