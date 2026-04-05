# Claude CCA-F Cheatsheet — Key Concepts

> One-page reference for the Claude Certified Architect – Foundations exam.

---

## Exam at a Glance

| | |
|---|---|
| Questions | 60 scenario-based MCQ |
| Time | 120 minutes |
| Pass | 720 / 1,000 |
| Register | [anthropic.skilljar.com](https://anthropic.skilljar.com) |

---

## Domain Weights

| Domain | Weight |
|---|---|
| D1: Agentic Architecture & Orchestration | 27% |
| D3: Claude Code Configuration | 20% |
| D4: Prompt Engineering & Structured Output | 20% |
| D2: Tool Design & MCP Integration | 18% |
| D5: Context Management & Reliability | 15% |

---

## Agentic Loop (D1)

```python
while True:
    response = client.messages.create(...)
    if response.stop_reason == "end_turn":   # done
        break
    if response.stop_reason == "tool_use":   # keep going
        result = execute_tool(...)
        messages.append(result)
```

- `"end_turn"` → stop
- `"tool_use"` → execute and continue
- Never use natural language detection or iteration caps to terminate

---

## CLAUDE.md Hierarchy (D3)

| File | Scope | VCS? |
|---|---|---|
| `~/.claude/CLAUDE.md` | Personal only | No |
| `.claude/CLAUDE.md` | Team-shared | Yes |
| `.claude/rules/*.md` | Per-file-type (glob) | Yes |

**Trap:** Team standards in `~/.claude/CLAUDE.md` = never shared with teammates.

---

## MCP Config (D2)

| File | Scope | VCS? |
|---|---|---|
| `.mcp.json` (project root) | Team-shared | Yes |
| `~/.claude.json` | Personal | No |

---

## tool_choice Modes (D2)

| Value | Behaviour |
|---|---|
| `"auto"` | Model decides |
| `"any"` | Must call at least one tool |
| `{"type":"tool","name":"x"}` | Forces specific tool |

**Optimal tools per agent: 4–5. Degraded at 18+.**

---

## Message Batches API (D4)

| | Batches | Sync |
|---|---|---|
| Cost | 50% cheaper | Full |
| Latency | Up to 24 hrs | Immediate |
| SLA | None | Yes |
| Multi-turn | No | Yes |
| Use for | Nightly reports, bulk jobs | PR reviews, agents |

---

## Escalation Triggers (D5)

| Valid | Invalid |
|---|---|
| Customer requests human | Angry tone / sentiment |
| Policy gap or ambiguity | Self-reported LLM confidence |
| Agent cannot progress | High message count |

---

## Slash Commands (D3)

| Location | Scope |
|---|---|
| `.claude/commands/` | Team (VCS) |
| `~/.claude/commands/` | Personal only |

---

## CI/CD Flags (D3)

```bash
claude -p "..."                          # non-interactive (headless)
claude -p "..." --output-format json     # machine-parseable output
```

---

## Top Anti-Patterns (Wrong Answers)

| Anti-Pattern | Correct Approach |
|---|---|
| Prompt-based tool ordering | Programmatic prerequisites |
| Sentiment-based escalation | Policy-gap escalation |
| Progressive summarization | Persistent case-facts block |
| Same-session self-review | Independent review instances |
| Regex for structured output | `tool_use` + JSON Schema |
| Batches API for PR review | Synchronous API |
| 18+ tools per agent | 4–5 tools, distribute to subagents |
| Team config in `~/.claude` | `.claude/CLAUDE.md` in VCS |

---

*Source: [Anthropic Academy](https://anthropic.skilljar.com) · [docs.anthropic.com](https://docs.anthropic.com)*
