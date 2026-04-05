# Claude Certified Architect Exam Guide PDF + AWS SAA-C03 Cheatsheet + GCP Certification Prep 2026

> The most complete free resource for AWS (CLF-C02, SAA-C03, SAP-C02), GCP (ACE, PCA), and Anthropic Claude (CCA-F) certifications.  
> Real notes from a **13x AWS Certified architect** who has trained 1,000+ engineers — including the official Anthropic CCA-F exam guide with all sample questions and exercises.

[![AWS](https://img.shields.io/badge/AWS-13x%20Certified-FF9900?logo=amazonaws&logoColor=white)](./AWS/)
[![GCP](https://img.shields.io/badge/GCP-Certified-4285F4?logo=googlecloud&logoColor=white)](./GCP/)
[![Claude CCA-F](https://img.shields.io/badge/Anthropic-CCA--F-7C3AED)](./Anthropic%20Claude/)
[![Stars](https://img.shields.io/github/stars/schinchli/cloud-certification-exam-prep?style=social)](https://github.com/schinchli/cloud-certification-exam-prep/stargazers)
[![License: MIT](https://img.shields.io/badge/License-MIT-green)](./LICENSE)

---

## Overview

This repository is a **free, structured certification prep hub** built from real exam experience across AWS, GCP, and Anthropic Claude. Every guide is mapped to official exam domains. No paywalls. No dumps. No filler.

**What's inside:**
- Deep-dive study notes for 8 certifications
- SAP-C02 professional notes across 16 topic modules
- AWS hands-on security labs (KMS, WAF, RDS, Secrets Manager)
- GCP Cloud Digital Leader + GenAI Leader complete guides
- **Official Anthropic CCA-F exam guide PDF** — all 5 domains, 12 sample questions with answers, 4 hands-on exercises, full appendix
- Cheatsheets, practice questions, and learning roadmaps

---

## Who This Is For

| Profile | What You'll Get |
|---|---|
| Beginner (0 → Cloud) | CLF-C02 + GCP Digital Leader roadmap |
| Developer / DevOps | SAA-C03 study guide + hands-on labs |
| Architect | SAP-C02 professional notes (16 modules) |
| AI / ML Engineer | AIF-C01, MLS-C01, GCP ML Engineer paths |
| Claude / AI SDK developer | CCA-F exam guide with official PDF + all sample questions |
| Multi-cloud professional | AWS + GCP comparison + Claude CCA-F |

---

## Anthropic Claude CCA-F — Official Exam Guide

The **Claude Certified Architect – Foundations (CCA-F)** is Anthropic's certification for solution architects building production systems with Claude. Launched March 2026 as part of the Claude Partner Network.

**[📄 Download Official CCA-F Exam Guide PDF](./Anthropic%20Claude/Claude%20Certified%20Architect%20%E2%80%93%20Foundations%20Certification%20Exam%20Guide.pdf)**  
**[→ Full CCA-F Study Guide with All Sample Questions](./Anthropic%20Claude/README.md)**

### Exam at a Glance

| | |
|---|---|
| Questions | 60 multiple-choice, scenario-based |
| Duration | 120 minutes |
| Passing Score | 720 / 1,000 (scaled 100–1,000) |
| Format | 4 of 6 scenarios randomly selected |
| Cost | Free (Claude Partner Network) / $99 otherwise |
| Registration | [anthropic.skilljar.com](https://anthropic.skilljar.com) |

### 5 Exam Domains

| Domain | Weight | Core Topics |
|---|---|---|
| D1: Agentic Architecture & Orchestration | 27% | Agentic loops (`stop_reason`), hub-and-spoke multi-agent, `Task` tool spawning, `PostToolUse` hooks, session forking |
| D2: Tool Design & MCP Integration | 18% | Tool descriptions for selection, 4–5 tools per agent, `tool_choice` modes, `.mcp.json` vs `~/.claude.json`, `isError` flag |
| D3: Claude Code Configuration | 20% | CLAUDE.md hierarchy, `.claude/rules/` glob patterns, `.claude/commands/`, plan mode vs direct execution, `-p` flag for CI |
| D4: Prompt Engineering & Structured Output | 20% | Explicit criteria, few-shot examples, `tool_use` + JSON Schema, validation-retry loops, Message Batches API |
| D5: Context Management & Reliability | 15% | "Case facts" blocks, lost-in-the-middle, escalation triggers, structured error propagation, scratchpad files |

### 6 Exam Scenarios
1. **Customer Support Resolution Agent** — `get_customer`, `lookup_order`, `process_refund`, `escalate_to_human`
2. **Code Generation with Claude Code** — CLAUDE.md, slash commands, plan mode
3. **Multi-Agent Research System** — coordinator/subagent, parallel `Task` calls, provenance tracking
4. **Developer Productivity with Claude** — built-in tools (Read/Write/Grep/Glob), MCP servers
5. **Claude Code for CI/CD** — `-p` flag, `--output-format json`, PR review automation
6. **Structured Data Extraction** — JSON schemas, validation-retry, Message Batches API

### Key Facts the Exam Tests

```
stop_reason = "tool_use"  → continue agentic loop
stop_reason = "end_turn"  → stop

tool_choice: "auto"       → model may return text
tool_choice: "any"        → model MUST call a tool
tool_choice: {forced}     → model calls specific tool

~/.claude/CLAUDE.md       → personal only, NOT version-controlled
.claude/CLAUDE.md         → team-shared via VCS
.claude/rules/            → path-specific, YAML frontmatter glob patterns
.claude/commands/         → project slash commands (shared)
~/.claude/commands/       → personal slash commands (not shared)

-p / --print              → non-interactive mode for CI/CD

Message Batches API       → 50% cost savings, up to 24h, no SLA
                          → never use for blocking pre-merge checks

Programmatic enforcement  → deterministic (use for financial operations)
Prompt instructions       → probabilistic (non-zero failure rate)
```

---

## AWS Certification Prep

| Exam | Level | Guide | Cheatsheet |
|---|---|---|---|
| AWS Cloud Practitioner (CLF-C02) | Foundational | [Roadmap →](./roadmap/aws-certification-guide.md) | [Cheatsheet →](./cheatsheets/aws-saa-c03.md) |
| AWS Solutions Architect Associate (SAA-C03) | Associate | [Study Guide →](./AWS/) | [Cheatsheet →](./cheatsheets/aws-saa-c03.md) |
| AWS AI Practitioner (AIF-C01) | Foundational | [Notes →](./AWS/AIF-C01-GenAI-Practitioner/) | [AWS Core →](./cheatsheets/aws-core-services.md) |
| AWS ML Specialty (MLS-C01) | Specialty | [Notes →](./AWS/MLS-C01-ML-Specialty/) | [AWS Core →](./cheatsheets/aws-core-services.md) |
| AWS Security Specialty (SCS-C02) | Specialty | [Notes →](./AWS/SCS-C02-Security-Specialty/) | [AWS Core →](./cheatsheets/aws-core-services.md) |
| AWS Solutions Architect Professional (SAP-C02) | Professional | [16-Module Notes →](./AWS/SAP-C02/) | [AWS Core →](./cheatsheets/aws-core-services.md) |

→ Full AWS guide: [**How to Pass AWS Certification in 2026**](./roadmap/aws-certification-guide.md)

---

## GCP Certification Prep

| Exam | Level | Guide | Cheatsheet |
|---|---|---|---|
| GCP Cloud Digital Leader | Foundational | [Complete Guide →](./GCP/Cloud-Digital-Leader/) | [GCP Cheatsheet →](./cheatsheets/gcp-ace-pca.md) |
| GCP Associate Cloud Engineer (ACE) | Associate | [Roadmap →](./roadmap/gcp-certification-guide.md) | [GCP Cheatsheet →](./cheatsheets/gcp-ace-pca.md) |
| GCP Professional Cloud Architect (PCA) | Professional | [Roadmap →](./roadmap/gcp-certification-guide.md) | [GCP Cheatsheet →](./cheatsheets/gcp-ace-pca.md) |
| Google Cloud GenAI Leader | Foundational | [Complete Guide →](./GCP/GenAI-Leader/) | [GCP Core →](./cheatsheets/gcp-core-services.md) |
| GCP Professional ML Engineer | Professional | [Roadmap →](./roadmap/gcp-certification-guide.md) | [GCP Cheatsheet →](./cheatsheets/gcp-ace-pca.md) |

→ Full GCP guide: [**GCP Associate Cloud Engineer Complete Guide 2026**](./roadmap/gcp-certification-guide.md)

---

## Cloud Certification Learning Roadmap

```
START HERE
    │
    ▼
FOUNDATIONAL (4–6 weeks each)
    ├── AWS Cloud Practitioner (CLF-C02)      → first cert, validates cloud basics
    └── GCP Cloud Digital Leader               → GCP equivalent of CLF
    │
    ▼
ASSOCIATE (6–10 weeks each)
    ├── AWS Solutions Architect Associate (SAA-C03)   ← highest ROI cert in market
    └── GCP Associate Cloud Engineer (ACE)
    │
    ▼
SPECIALIST / AI
    ├── AWS GenAI Practitioner (AIF-C01)
    ├── AWS ML Specialty (MLS-C01)
    ├── AWS Security Specialty (SCS-C02)
    ├── GCP Professional ML Engineer
    └── Anthropic Claude Certified Architect – Foundations (CCA-F)  ← new 2026
    │
    ▼
PROFESSIONAL (10–16 weeks)
    ├── AWS Solutions Architect Professional (SAP-C02)
    └── GCP Professional Cloud Architect (PCA)
```

---

## Repo Structure

```
cloud-certification-exam-prep/
│
├── Anthropic Claude/
│   ├── README.md                     All 5 domains · 12 sample Qs · 4 exercises · appendix
│   └── Claude Certified Architect – Foundations Certification Exam Guide.pdf
│
├── AWS/
│   ├── SAP-C02/                      16-module professional notes (IAM → DR → IaC)
│   ├── AIF-C01-GenAI-Practitioner/
│   ├── MLS-C01-ML-Specialty/
│   ├── SCS-C02-Security-Specialty/
│   └── security-labs/               Hands-on: KMS · WAF · RDS Secrets Manager
│
├── GCP/
│   ├── Cloud-Digital-Leader/         Complete guide + practice questions
│   └── GenAI-Leader/                 Google Cloud AI certification guide
│
├── cheatsheets/
│   ├── aws-saa-c03.md               SAA-C03 + CLF-C02 exam day reference
│   ├── gcp-ace-pca.md               ACE + PCA exam day reference
│   ├── aws-core-services.md
│   ├── gcp-core-services.md
│   └── claude-cca-f.md
│
├── practice-questions/               AWS · GCP · Claude CCA-F
│
└── roadmap/
    ├── aws-certification-guide.md    How to pass AWS SAA-C03 in 2026
    └── gcp-certification-guide.md   How to pass GCP ACE in 2026
```

---

## Official Study Resources

| Platform | Free Courses | Practice Tests | Docs |
|---|---|---|---|
| AWS | [Skill Builder](https://skillbuilder.aws) | [Official Practice](https://explore.skillbuilder.aws) | [docs.aws.amazon.com](https://docs.aws.amazon.com) |
| GCP | [Cloud Skills Boost](https://cloudskillsboost.google) | [GCP Practice](https://cloudskillsboost.google) | [cloud.google.com/docs](https://cloud.google.com/docs) |
| Anthropic | [Anthropic Academy](https://anthropic.skilljar.com) | [Official Exam](https://anthropic.skilljar.com) | [docs.anthropic.com](https://docs.anthropic.com) |

---

## Practice Questions

- [AWS Practice Questions](./practice-questions/aws.md) — SAA-C03 format
- [GCP Practice Questions](./practice-questions/gcp.md) — ACE format
- [Claude CCA-F Practice Questions](./practice-questions/claude-cca-f.md) — official format

---

## Cheatsheets

| Cheatsheet | Best For |
|---|---|
| [AWS SAA-C03 + CLF-C02](./cheatsheets/aws-saa-c03.md) | AWS exam day quick reference |
| [GCP ACE + PCA](./cheatsheets/gcp-ace-pca.md) | GCP exam day quick reference |
| [AWS Core Services](./cheatsheets/aws-core-services.md) | Service-by-service reference |
| [GCP Core Services](./cheatsheets/gcp-core-services.md) | GCP service reference |
| [Claude CCA-F Key Concepts](./cheatsheets/claude-cca-f.md) | CCA-F exam day reference |

---

## Why This Repo

- **13x AWS Certified** — notes built from real certification experience
- **1,000+ engineers trained** — content tested against what actually appears on exams
- **Official sources only** — no third-party dumps, no unverified content
- **No paywalls** — 100% free
- **Actively maintained** — covers 2026 certifications including Anthropic CCA-F
- **Hands-on labs** — not just theory; deployable AWS security labs included
- **Official PDF hosted here** — Anthropic CCA-F exam guide PDF with all sample questions and exercises, downloadable directly from this repo

---

## Learn With a Mentor — 1:1 Guidance

Struggling to know where to start? Stuck on exam concepts?  
Work directly with **Shashank Chinchli** — Sr. Solutions Architect at GitLab, ex-AWS, AWS Golden Jacket recipient.

| | |
|---|---|
| **Role** | Sr. Solutions Architect @ GitLab |
| **Background** | ex-AWS |
| **Certifications** | 13x AWS Certified |
| **Recognition** | AWS Golden Jacket — awarded to top AWS community contributors |
| **Engineers Trained** | 1,000+ |
| **Mentor Rating** | Top 1% on Topmate |

**What you get from 1:1 mentorship:**

- Personalized certification roadmap for your background and goals
- Exam strategy — what to focus on, what to skip
- Architecture review and real-world scenario coaching
- Resume and career positioning for cloud roles
- Direct answers from someone who has passed 13 AWS exams

**Common pain points solved:**

> *"I don't know which cert to take first."*  
> *"I've been studying for months and keep failing."*  
> *"I passed the exam but can't get interviews."*  
> *"I need to go from developer to solutions architect."*

**[→ Book a session on Topmate](https://topmate.io/heyshashank)**

---

## Roadmap

- [x] AWS SAP-C02 professional notes (16 modules)
- [x] AWS specialty notes — AIF-C01, MLS-C01, SCS-C02
- [x] AWS hands-on security labs
- [x] GCP Cloud Digital Leader complete guide + practice questions
- [x] GCP GenAI Leader complete guide
- [x] Anthropic Claude CCA-F exam guide (official PDF + full study guide)
- [x] Platform cheatsheets and practice questions
- [x] AWS + GCP certification roadmap guides
- [ ] AWS SAA-C03 dedicated notes
- [ ] AWS CLF-C02 foundational guide
- [ ] GCP ACE dedicated notes
- [ ] GCP PCA dedicated notes
- [ ] AWS vs GCP comparison guide
- [ ] Azure certification guides *(coming soon)*

---

## Contributing

PRs welcome. To contribute:

1. Fork this repo
2. Add content under the relevant platform folder
3. Link only to official vendor documentation
4. Keep it factual — no unverified exam dumps

---

*Built from real exam experience. Maintained by a 13x AWS Certified architect. Last updated April 2026.*  
*[📖 Book 1:1 mentorship](https://topmate.io/heyshashank)*

---

## Star This Repo

If this saved you time, **[star the repo](https://github.com/schinchli/cloud-certification-exam-prep/stargazers)** — it helps other engineers find it.

[![GitHub stars](https://img.shields.io/github/stars/schinchli/cloud-certification-exam-prep?style=social)](https://github.com/schinchli/cloud-certification-exam-prep/stargazers)
