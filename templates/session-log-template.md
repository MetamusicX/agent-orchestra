# Session Log Template

Use this template when Atlas writes a structured session summary at session close. Save it to `Session Logs/YYYY-MM-DD.md` (append `_02`, `_03` for multiple sessions on the same day).

---

```yaml
---
session: YYYY-MM-DD             # date (append _02 if multiple sessions per day)
duration: ""                    # approximate (e.g., "45 min")
agents-involved: []             # list of agent names active this session
tasks-touched: []               # list of TASK-NNN IDs worked on
tasks-created: []               # list of TASK-NNN IDs created this session
---

# Session Log — YYYY-MM-DD

## What we worked on
- [Bullet point 1]
- [Bullet point 2]
- [Bullet point 3]

## Decisions made
- [Decision 1]
- [Or: No decisions made.]

## What changed
- [Files created, modified, or moved. Deliverables produced.]

## Open items
- [What is still in progress or unresolved at session end.]

## Notes
[Anything else worth recording. Can be empty.]
```

---

## When to write a session log

Atlas writes a session log when the user signals session end:
- "close session", "wrap up", "that's all for today", "done for now"
- "let's stop here", "I'm done", "save our progress"
- Any clear session-ending intent

## What to include

- **What we worked on**: 2-5 bullet points covering the main activities.
- **Decisions made**: Anything decided that affects future work. If nothing, say so.
- **What changed**: Files and deliverables. Be specific about paths.
- **Open items**: Work that continues next session. Link to task IDs where they exist.

## After writing the session log

1. Update `Session Logs/INDEX.md` with a new row.
2. Update any tasks that were worked on (move files between status folders if needed, update frontmatter).
3. Write journal entries for any durable insights that emerged during the session.
4. Confirm to the user: "Session logged. [brief summary]."
