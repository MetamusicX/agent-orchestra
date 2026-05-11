# Task Template

Use this template when creating a new task file. Save it to `Team Knowledge/tasks/open/TASK-YYYY-NNN.md`.

---

```yaml
---
id: TASK-YYYY-NNN
title: ""
status: open                    # open | in-progress | done | cancelled
assignee: ""                    # agent name (e.g., sigmund, mira)
created: YYYY-MM-DD
updated: YYYY-MM-DD
due: ""                         # optional: YYYY-MM-DD
sop: ""                         # optional: SOP-NNN reference
workstream: ""                  # optional: WS-NNN reference
source: ""                      # what triggered this (session, user request, recurring)
blocking: ""                    # optional: what is blocking progress
tags: []                        # optional: free-form tags
---

# TASK-YYYY-NNN: [Title]

## Description
[What needs to be done. 1-3 sentences.]

## Input
[What materials or context the assignee needs. File paths, references.]

## Expected Output
[What the deliverable looks like. Where it should be placed.]

## Notes
[Any additional context, constraints, or decisions.]

## Log
- YYYY-MM-DD: Created. [by whom/how]
```

---

## Field guide

| Field | Required | Notes |
|-------|----------|-------|
| `id` | Yes | Year + sequential number. Human-readable, sortable. |
| `title` | Yes | Short, specific description of the work. |
| `status` | Yes | Must match folder location. Frontmatter is authoritative. |
| `assignee` | Yes | The agent who will do the work. |
| `created` / `updated` | Yes | ISO dates. Updated on every status change. |
| `due` | No | Only if there is a real deadline. |
| `sop` | No | Reference to the SOP this task follows, if any. |
| `workstream` | No | Reference to the workstream this task belongs to, if any. |
| `source` | No | Audit trail: what triggered this task. |
| `blocking` | No | Filled when a task is stuck. Helps Atlas surface blockers. |
| `tags` | No | Free-form. Use sparingly. |

## Lifecycle

1. **Created** in `tasks/open/` — waiting to be picked up.
2. **Moved** to `tasks/in-progress/` — an agent is working on it.
3. **Moved** to `tasks/done/YYYY/MM/` — work is complete and approved.
4. **Or moved** to `tasks/cancelled/YYYY/MM/` — no longer needed.

Every move updates both the frontmatter `status` and `updated` fields, and appends a line to the Log section.

## When to create a task

Not every request becomes a task. Tasks are for work that:
- Spans multiple sessions
- Requires explicit tracking
- Follows an SOP or workstream
- Has dependencies or deadlines

Quick, single-session requests (e.g., "check what's in the Team Inbox") are NOT tasks.
