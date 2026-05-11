# Journal Entry Template

Use this template when an agent learns something durable during task execution. Save it to `Team/journals/<agent-name>/YYYY-MM-DD-slug.md`.

---

```yaml
---
agent: ""                       # agent name
date: YYYY-MM-DD
task: ""                        # optional: TASK-NNN that triggered this insight
type: insight                   # insight | anti-pattern | decision-rule | process-note
---

# [Concise title of what was learned]

## Context
[What was the agent doing when this came up? 1-2 sentences.]

## Insight
[The reusable lesson. What should the agent remember for next time?]

## Applies when
[Under what circumstances this insight is relevant. Be specific.]
```

---

## Type taxonomy

| Type | Use when |
|------|----------|
| `insight` | General learning — something that worked well or a useful observation. |
| `anti-pattern` | Something to avoid — "don't do this because..." |
| `decision-rule` | A conditional rule — "when X, do Y." |
| `process-note` | Procedural memory — how a tool, format, or material actually works. |

## What makes a good journal entry

- **Specific, not vague.** "Be careful with dates" is useless. "Cluster meeting transcripts before 2025-09 use a different naming convention — check the filename format before extracting" is actionable.
- **Forward-looking.** Written for the agent's future self, not as a retrospective. The question is: "what would I want to know if I had no memory of this session?"
- **Short.** A journal entry should take 30 seconds to write and 10 seconds to scan.

## When to write a journal entry

- The agent discovered an anti-pattern that wasted time
- The agent found a decision rule that resolved ambiguity
- A tool or source behaved differently than expected
- A procedure needed adjustment that isn't worth a full SOP update

Journal entries are NOT session summaries. They capture one specific, reusable lesson per entry.

## How journals are used

Before delegating a task to an agent, Atlas checks that agent's journal for relevant entries. If an entry's "Applies when" matches the current task context, Atlas includes it in the delegation brief. Learning compounds across sessions.
