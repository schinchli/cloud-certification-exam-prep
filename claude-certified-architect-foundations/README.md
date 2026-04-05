# Claude Certified Architect – Foundations (CCA-F)

> Official exam prep guide based on Anthropic's published exam guide and Anthropic Academy course content.

---

## About the Certification

The **Claude Certified Architect – Foundations (CCA-F)** is Anthropic's official certification for solution architects building production systems with Claude AI. It was launched on **March 12, 2026** as part of the [Claude Partner Network](https://www.anthropic.com/news/claude-partner-network).

**Registration:** [Anthropic Academy — anthropic.skilljar.com](https://anthropic.skilljar.com)  
**Eligibility:** Claude Partner Network membership required  
**Official Exam Guide:** Available inside Anthropic Academy after partner enrollment

---

## Exam Format

| Attribute | Details |
|---|---|
| Questions | 60 scenario-based multiple-choice |
| Duration | 120 minutes |
| Delivery | Remote proctored (ProctorFree) |
| Passing Score | 720 / 1,000 (scaled) |
| Cost | Free for first 5,000 Claude Partner Network employees; $99/attempt otherwise |
| Score Report | Within 2 business days (per-domain breakdown) |

*Source: [Claude Partner Network announcement](https://www.anthropic.com/news/claude-partner-network) and community-verified exam guide summaries.*

---

## Exam Domains

| # | Domain | Weight |
|---|---|---|
| D1 | Agentic Architecture & Orchestration | 27% |
| D2 | Tool Design & MCP Integration | 18% |
| D3 | Claude Code Configuration & Workflows | 20% |
| D4 | Prompt Engineering & Structured Output | 20% |
| D5 | Context Management & Reliability | 15% |

---

## Key Topics by Domain

### D1 — Agentic Architecture & Orchestration (27%)
- Agentic loop lifecycle: `stop_reason = "tool_use"` → continue; `stop_reason = "end_turn"` → stop
- Multi-agent hub-and-spoke pattern: coordinator routes all tasks; subagents receive only scoped context
- `PreToolUse` / `PostToolUse` hooks for deterministic policy enforcement
- Session strategies: resume, fork, fresh start with summary injection
- Task decomposition: fixed vs dynamic adaptive

### D2 — Tool Design & MCP Integration (18%)
- Tool descriptions (not function names) drive model tool-selection accuracy
- Optimal: 4–5 tools per agent; 18+ tools degrades selection reliability
- `tool_choice` modes: `"auto"` / `"any"` / specific tool name
- Four error categories: transient, validation, business, permission
- MCP config: `.mcp.json` (project-scoped, VCS) vs `~/.claude.json` (personal, not shared)

### D3 — Claude Code Configuration & Workflows (20%)
- `~/.claude/CLAUDE.md` = personal only, never version-controlled
- `.claude/CLAUDE.md` (project root) = team-shared via VCS
- `.claude/rules/` = path-specific rules using glob patterns in YAML frontmatter
- Custom slash commands: `.claude/commands/` (shared) vs `~/.claude/commands/` (personal)
- Plan Mode: use for complex multi-file / architectural changes
- CI/CD: `-p` flag for non-interactive (headless) mode; `--output-format json` for machine parsing

### D4 — Prompt Engineering & Structured Output (20%)
- Use explicit criteria + 2–4 few-shot examples over vague instructions
- `tool_use` + JSON Schema eliminates syntax errors; semantic errors still require validation-retry loops
- Message Batches API: 50% cost savings, up to 24-hour window, no SLA — use for nightly/batch jobs only, never for real-time workflows (PR reviews, user-facing agents)
- Multi-pass review: split into per-file analysis pass + integration review pass; independent instances catch more issues than same-session self-review

### D5 — Context Management & Reliability (15%)
- Progressive summarization destroys transactional details — use a persistent "case facts" block instead
- Lost-in-the-middle: models process beginning/end reliably; mitigate middle-section loss with summaries at top + section headers
- Valid escalation triggers: customer requests human, policy gap, agent cannot progress
- Invalid escalation triggers: sentiment analysis, self-reported LLM confidence
- Structured error propagation from subagents: always include failure type, partial results, recovery options — never suppress silently

---

## Official Study Resources

| Resource | Link |
|---|---|
| Anthropic Academy (all courses free) | [anthropic.skilljar.com](https://anthropic.skilljar.com) |
| Claude Partner Network | [anthropic.com/news/claude-partner-network](https://www.anthropic.com/news/claude-partner-network) |
| Claude Documentation | [docs.anthropic.com](https://docs.anthropic.com) |
| Claude Code Docs | [docs.anthropic.com/en/docs/claude-code](https://docs.anthropic.com/en/docs/claude-code) |
| Model Context Protocol | [modelcontextprotocol.io](https://modelcontextprotocol.io) |
| Anthropic Learn Hub | [anthropic.com/learn](https://www.anthropic.com/learn) |

**Recommended Anthropic Academy courses (free):**
1. Claude 101
2. Building with the Claude API
3. Claude Code in Action
4. Introduction to Model Context Protocol (MCP)
5. Building Applications with the Claude API

---

## Preparation Timeline

| Profile | Recommended Time |
|---|---|
| Daily Claude practitioner (6+ months production use) | 2–4 weeks |
| Newer to Claude APIs | 2–4 months (build real projects first) |

**Benchmark:** Aim for 900+ / 1,000 on the official Anthropic Academy practice exam before scheduling.

---

*Content based on Anthropic's official exam guide (distributed via Anthropic Academy) and the [Claude Partner Network announcement](https://www.anthropic.com/news/claude-partner-network). Always verify against the latest official exam guide at [anthropic.skilljar.com](https://anthropic.skilljar.com).*
