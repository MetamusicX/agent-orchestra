# Session Logging

## What session logs are

Session logs capture what happened in a work session — the decisions, the changes, the open items. They are written by Atlas when the user signals the session is ending.

Session logs are not conversation exports. A raw conversation transcript contains everything that was said, including false starts, corrections, and tangents. A session log captures what mattered: what was decided, what changed, and what still needs attention.

## How it works

When the user signals the session is done — "close session", "wrap up", "done for now", or similar — Atlas writes a structured log to `Session Logs/YYYY-MM-DD.md`.

If multiple sessions happen on the same day, Atlas appends a suffix: `YYYY-MM-DD-2.md`.

## Log structure

Each session log has YAML frontmatter and a structured body:

```yaml
---
session-date: 2026-05-10
duration: ~90 minutes
agents-involved: [Atlas, Kai, Merlin]
tasks-touched: [TASK-042, TASK-038]
tasks-created: [TASK-045]
---
```

The body follows a fixed format:

```markdown
## What we worked on
What the session focused on, in 2-4 sentences.

## Decisions made
Specific decisions with enough context to understand them later.

## What changed
Files created, modified, or deleted. Tasks moved. Agents hired.

## Open items
What was not finished. What needs attention next session.

## Notes
Anything that does not fit above but should not be lost.
```

## The INDEX

`Session Logs/INDEX.md` tracks all sessions in a table:

```markdown
| Date       | Duration | Agents         | Tasks touched       | Summary           |
|------------|----------|----------------|---------------------|--------------------|
| 2026-05-10 | ~90 min  | Atlas, Kai     | TASK-042, TASK-038  | Pipeline work      |
| 2026-05-09 | ~45 min  | Atlas, Merlin  | TASK-041            | Research phase     |
```

This gives you a timeline view of all work done across the project without opening individual logs.

## What happens after the log is written

After writing the session log, Atlas does two things:

1. **Updates tasks** — every task touched during the session gets a Log entry noting what happened
2. **Writes journal entries** — if the session produced durable insights (an anti-pattern discovered, a decision rule established), Atlas writes them to the relevant agent's journal

This is the connective tissue. Session logs feed into tasks and journals, so the knowledge from one session propagates to the artefacts that future sessions will read.

## The complement to tasks

Tasks track what needs to happen. Session logs track what did happen.

Together, they form a complete picture: the task file tells you the work's current state and what remains. The session logs tell you the history — when it was worked on, what decisions shaped it, what was tried and abandoned.

A new session can read both: the task for context on what to do, and the session logs for context on what has already been done and why.

## Why this matters

Without session logs, the only record of a session is the raw conversation — which is long, noisy, and not structured for retrieval. Session logs compress a session into its essential signal: what mattered, what changed, what is next.

They also make the system auditable. You can trace any decision back to the session where it was made, who was involved, and what other work was happening at the time.
