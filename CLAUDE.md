# cloud-certification-exam-prep — Editorial & Contribution Rules

> Read this before making ANY change to this repository.  
> These rules must be applied consistently across every file, commit, and GitHub setting.

---

## Owner & Attribution

- **Repo owner:** Shashank Chinchli (`schinchli`)
- **Mentor CTA:** Always link to `https://topmate.io/heyshashank`
- **Mentor profile:** Sr. Solutions Architect @ GitLab · ex-AWS · 13x AWS Certified · AWS Golden Jacket · 1,000+ engineers trained
- **Remove all third-party course credits** — no Udemy author names, no instructor credits (Cantrill, Maarek, Raykov, etc.)

---

## Content Rules — Zero Hallucination

### CCA-F (Anthropic Claude)
- **Source of truth:** `Anthropic Claude/Claude Certified Architect – Foundations Certification Exam Guide.pdf` (40 pages, Version 0.1, Feb 10 2025)
- Every domain, task statement, scenario, sample question, exercise, and appendix entry MUST come from that PDF
- Never invent exam questions, domain weights, or task statements
- When the PDF is updated, re-read it fully before revising any CCA-F content

### AWS Content
- Source from: `AWS/` folder notes (pulled from `certified-aws-solutions-architect-professional` and `shankynotes` repos), official AWS documentation
- No unverified content, no brain dumps

### GCP Content
- Source from: `GCP/` folder notes (pulled from `shankynotes` repo), official Google Cloud documentation

### General Rule
- Only reference official vendor documentation in external links
- No "coming soon" filler with fake content — either the content exists or it doesn't

---

## File Structure — Never Change Without Updating All References

```
Anthropic Claude/
  README.md                          — CCA-F full study guide (all PDF content)
  Claude Certified Architect – Foundations Certification Exam Guide.pdf

AWS/
  SAP-C02/                           — 16 modules
  AIF-C01-GenAI-Practitioner/
  MLS-C01-ML-Specialty/
  SCS-C02-Security-Specialty/
  security-labs/

GCP/
  Cloud-Digital-Leader/
  GenAI-Leader/

cheatsheets/
  aws-saa-c03.md
  gcp-ace-pca.md
  aws-core-services.md
  gcp-core-services.md
  azure-core-services.md             — exists but Azure folder removed
  claude-cca-f.md

practice-questions/
  aws.md
  gcp.md
  claude-cca-f.md

roadmap/
  aws-certification-guide.md
  gcp-certification-guide.md
```

**Azure:** NO Azure folder. Azure is "coming soon" in the roadmap checklist only. Do not create an Azure folder unless real study content exists.

---

## Root README.md Rules

### H1 / Title
Must target these SEO keywords in the H1:
- "Claude Certified Architect Exam Guide PDF"
- "AWS SAA-C03"
- "GCP Certification Prep 2026"

Current H1: `Claude Certified Architect Exam Guide PDF + AWS SAA-C03 Cheatsheet + GCP Certification Prep 2026`

### Section Order (FIXED — do not reorder)
1. H1 + tagline
2. Badges (AWS, GCP, CCA-F — no Azure badge unless Azure folder exists)
3. Overview bullet list
4. Who This Is For table
5. **Anthropic CCA-F section** (PDF link prominent, domain table, scenario list, key facts code block)
6. AWS Certification Prep table
7. GCP Certification Prep table
8. Learning Roadmap (code block)
9. Repo Structure (code block)
10. Official Study Resources
11. Practice Questions
12. Cheatsheets
13. Why This Repo
14. Learn With a Mentor (Shashank profile + CTA)
15. Roadmap checklist
16. Contributing
17. Footer line
18. **Star This Repo** ← ALWAYS LAST

### Star CTA
Always at the very end of README.md. Never move it to the top.

### Badges
Current badges: AWS · GCP · CCA-F · Stars · MIT License
Do NOT add Azure badge until Azure content folder exists with real notes.

---

## `Anthropic Claude/README.md` Rules

### Structure (FIXED)
1. H1 + tagline with PDF link
2. About the Certification
3. Exam Format table
4. Target Candidate
5. Exam Domains & Weights table
6. Exam Scenarios (all 6, with tool names and primary domain mappings)
7. Domain 1 through Domain 5 — all task statements with Knowledge and Skills bullets
8. Official Sample Questions — all 12, with full answer choices + correct answer + explanation
9. Preparation Exercises — all 4 with full steps and domains reinforced
10. Appendix (Technologies table, In-Scope list, Out-of-Scope list, 8 Prep Recommendations)
11. Preparation Timeline
12. Official Study Resources
13. Footer with PDF attribution

### Never:
- Invent or paraphrase exam questions
- Add questions not in the PDF
- Remove questions from the official 12
- Change correct answers
- Summarize exercises — include all steps

---

## Commit Message Rules

### Format
```
<type>: <concise description of actual change>

- bullet of specific changes
- another bullet
```

### Types: `docs`, `feat`, `fix`, `refactor`, `chore`

### NEVER include these words in commit messages:
- "SEO"
- "optimize for search"
- "keyword"
- "ranking"

### Good examples:
```
docs: add full CCA-F domain breakdown, all 12 sample questions, 4 exercises from official exam guide
docs: remove Azure placeholder, move star CTA to end of README
docs: remove third-party attribution from GCP and AWS study notes
chore: update GitHub topics and repo description
```

### Bad examples (do not use):
```
docs: SEO optimize README for claude certification keywords
docs: SEO improvements to CCA-F guide
```

---

## GitHub Repository Settings

### Description (160 char max)
Current: `Free cloud certification exam prep: AWS SAA-C03, SAP-C02, GCP ACE, PCA + Anthropic Claude CCA-F exam guide PDF with all sample questions. Built by a 13x AWS Certified architect.`

### Topics (exactly 20, ordered by priority)
```
claude-certification-exam-guide
cca-f
claude-certified-architect
anthropic-claude
aws-saa-c03
aws-certification
aws-solutions-architect
sap-c02
gcp-certification
gcp-ace
cloud-certification
exam-prep
cheatsheet
study-guide
mcp-integration
claude-agent-sdk
claude-code
free-resources
solutions-architect
ai-certification
```

To update topics atomically (must be exactly 20):
```bash
gh api --method PUT repos/schinchli/cloud-certification-exam-prep/topics \
  --field 'names[]=claude-certification-exam-guide' \
  ... (all 20)
```

---

## Cheatsheet Rules

Each cheatsheet must have:
- Exam at a glance table (questions, duration, passing score, cost, format, register link)
- Domain weights table
- Service comparison tables with AWS equivalents (where relevant)
- Decision trees for service selection
- Exam tips section at the end (numbered list, 8–10 tips)
- Footer with official guide links + topmate.io/heyshashank

---

## Roadmap Guide Rules

Each roadmap guide (`aws-certification-guide.md`, `gcp-certification-guide.md`) must have:
- Which cert to take first (decision table by background)
- Full cert path (code block diagram)
- Week-by-week study plan for each cert covered
- 5 common mistakes section
- Official resources table
- Mentor CTA (Shashank profile + topmate link)
- Navigation footer: ← Back to main repo | Cheatsheet → | Other Roadmap →

---

## What NEVER Goes in This Repo

- Third-party course credits or instructor names
- Azure folder with only external links and no study content
- Unverified exam questions ("brain dumps")
- Content fabricated without an official source
- Salary data presented as guaranteed (use "estimates — actual impact varies")
- Star CTA at the top of README

---

## When Adding a New Certification

1. Create folder: `<Platform>/<Cert-Code>/`
2. Add study notes sourced from official exam guide
3. Remove any third-party attribution
4. Add entry to root README tables (Who This Is For, cert table, roadmap checklist)
5. Add cheatsheet to `cheatsheets/` and link from cert table
6. Add practice questions to `practice-questions/`
7. Update repo structure code block in README
8. Update GitHub topics if the new cert warrants a topic
9. Commit with descriptive message (no "SEO")

---

## PDF-Sourced Content Workflow

When the official exam guide PDF is updated:
1. Read the full new PDF
2. Note version number and date (currently: Version 0.1, Feb 10 2025)
3. Update `Anthropic Claude/README.md` — all sections, not selectively
4. Update root README CCA-F section if domain weights or scenarios changed
5. Update `cheatsheets/claude-cca-f.md`
6. Commit: `docs: update CCA-F content to exam guide v<X.Y> (<date>)`

---

*Last updated: April 2026*
