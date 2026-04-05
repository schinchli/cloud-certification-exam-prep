# Claude Certified Architect – Foundations (CCA-F) Practice Questions

> Sample questions based on the official CCA-F exam guide format (scenario-based, 4-option multiple choice).  
> Source: [Anthropic Academy](https://anthropic.skilljar.com) — official exam guide distributed to Claude Partner Network members.

---

## How the Exam Works

- **60 questions** drawn from **4 of 6 possible scenarios** (randomly selected per session)
- Each scenario tests 2–3 domains
- All questions are **scenario-based** — a situation is described, you pick the best engineering decision
- Pass: **720 / 1,000** (scaled score)

---

## Sample Questions by Domain

### Domain 1 — Agentic Architecture & Orchestration (27%)

**Q1.** An agent skips `get_customer` 12% of the time, causing order-lookup identity mismatches. What is the most reliable fix?

- A. Add prompt-level instructions emphasizing tool call order
- B. Add programmatic prerequisite blocking `lookup_order` until customer ID is verified ✅
- C. Increase max_tokens to allow more reasoning before tool use
- D. Add a retry loop when `lookup_order` fails

> **Why B:** Programmatic enforcement is deterministic. Prompt-based ordering is probabilistic — it will fail some percentage of the time regardless of how clearly worded.

---

**Q2.** A multi-agent research system returns an incomplete report despite all subagents completing. Which is the most likely root cause?

- A. One subagent timed out silently
- B. The coordinator's task decomposition was too narrow ✅
- C. Subagents shared context incorrectly
- D. The synthesis model hit its context limit

> **Why B:** Subagents can only research topics they are explicitly assigned. If the coordinator's decomposition omits areas, no subagent covers them.

---

### Domain 2 — Tool Design & MCP Integration (18%)

**Q3.** An agent consistently confuses `get_customer` and `lookup_order` despite both being correctly implemented. What is the most effective fix?

- A. Rename the functions to be more distinct
- B. Add disambiguation to the system prompt
- C. Expand the tool descriptions with input formats, examples, and edge cases ✅
- D. Reduce the tool count by merging both into one tool

> **Why C:** Tool descriptions are the primary signal the model uses for tool selection. Function names and system prompts are secondary.

---

**Q4.** A teammate clones the repo but cannot see the MCP server configuration you set up. What is the cause?

- A. The MCP server is not running
- B. The config was saved to `~/.claude.json` instead of `.mcp.json` in the project root ✅
- C. The teammate needs to reinstall Claude Code
- D. MCP configs are encrypted per user

> **Why B:** `~/.claude.json` is personal and not version-controlled. Project-shared MCP config belongs in `.mcp.json` at the project root.

---

### Domain 3 — Claude Code Configuration & Workflows (20%)

**Q5.** You need a `/review` slash command accessible to all teammates after they clone the repo. Where do you create it?

- A. `~/.claude/commands/review.md`
- B. `.claude/commands/review.md` ✅
- C. `CLAUDE.md` under a commands section
- D. `.mcp.json` as a registered command

> **Why B:** `.claude/commands/` is version-controlled and shared with the team. `~/.claude/commands/` is personal only.

---

**Q6.** Claude Code hangs in your CI/CD pipeline waiting for user input. What is the fix?

- A. Set `CI=true` environment variable
- B. Use `--non-interactive` flag
- C. Use the `-p` flag for headless/non-interactive mode ✅
- D. Pipe `/dev/null` to stdin

> **Why C:** `-p` is the official Claude Code flag for non-interactive (headless) mode in CI/CD pipelines.

---

### Domain 4 — Prompt Engineering & Structured Output (20%)

**Q7.** Your manager proposes using the Message Batches API for both PR review automation and a nightly codebase audit. Which use is appropriate?

- A. Both are appropriate
- B. Neither — always use synchronous API
- C. PR review only
- D. Nightly audit only ✅

> **Why D:** Message Batches API has up to a 24-hour processing window with no SLA. This blocks PR workflows. Use it only for non-time-sensitive batch jobs.

---

**Q8.** A single-pass review of 14 files produces inconsistent feedback quality. What is the most effective improvement?

- A. Use a larger model
- B. Increase max_tokens
- C. Split into per-file analysis pass followed by an integration review pass ✅
- D. Run the same prompt three times and take the best output

> **Why C:** Reviewing too many files in one pass causes attention dilution. Splitting into focused passes addresses the root cause.

---

### Domain 5 — Context Management & Reliability (15%)

**Q9.** A customer service agent loses order details (amounts, IDs, dates) after summarizing long conversations. What is the fix?

- A. Increase the context window size
- B. Replace progressive summarization with a persistent case-facts block ✅
- C. Store transcripts in a database and retrieve on demand
- D. Use a lower temperature to reduce hallucinations

> **Why B:** Progressive summarization destroys transactional specifics. A persistent case-facts block is never summarized — key facts are extracted once and appended.

---

**Q10.** An agent escalates to a human whenever a customer uses angry language. Is this a valid escalation trigger?

- A. Yes — negative sentiment indicates customer dissatisfaction
- B. No — sentiment analysis is not a valid escalation trigger ✅
- C. Yes — if the tone score exceeds a threshold
- D. Only if combined with a confidence score below 50%

> **Why B:** Valid triggers are: customer requests human, policy gap, agent cannot progress. Sentiment analysis and confidence scores are not reliable escalation signals.

---

## Official Practice Exam

Anthropic provides a full 60-question practice exam through Anthropic Academy.  
**Target 900+ / 1,000 before scheduling the real exam.**

Register: [anthropic.skilljar.com](https://anthropic.skilljar.com)

---

*Questions reflect the official CCA-F exam guide format. Verify against the latest guide at [anthropic.skilljar.com](https://anthropic.skilljar.com).*
