# Task Continuity

## The problem

LLMs forget everything between sessions. Every conversation starts from zero. If you were working on something yesterday, the model does not know that today unless you tell it again.

This is the fundamental limitation that task continuity solves. Tasks are persistent artefacts that survive session boundaries. They sit in the file system waiting to be picked up, regardless of whether the agent that created them is still in context.

## How tasks work

Tasks are plain `.md` files with YAML frontmatter, stored in `Team Knowledge/tasks/`. Their folder location determines their status:

```
Team Knowledge/tasks/
├── open/              # Waiting to be started
├── in-progress/       # Currently being worked on
├── done/YYYY/MM/      # Completed, archived by month
└── cancelled/YYYY/MM/ # Abandoned, archived by month
```

Moving a file between folders changes its status. There is no database, no state file, no external system. The file system is the source of truth.

## Task structure

Every task file has YAML frontmatter followed by a body:

```yaml
---
id: TASK-042
title: Build transcript clustering pipeline
status: in-progress
assignee: Kai
created: 2026-05-01
updated: 2026-05-10
due: 2026-05-15
sop: SOP-003
workstream: WS-001
source: "Session 2026-05-01"
blocking: TASK-043
tags: [engineering, transcripts]
---
```

The body contains the task description, acceptance criteria, and a **Log** section that tracks every status change and meaningful update.

## The Task Walk

Atlas is the Task Walker. At the start of every session, Atlas walks `open/` and `in-progress/` to see what is waiting. This is how continuity works — Atlas does not remember previous sessions, but it does not need to. The tasks are there, in the file system, with all their context.

The walk surfaces:
- Tasks that are blocked and need attention
- Tasks that are in progress and may need a status check
- Tasks that are open and ready to be picked up
- Due dates that are approaching or overdue

## Task lifecycle

```
Created in open/
       │
       ▼
Moved to in-progress/ (assignee begins work)
       │
       ├── Completed → moved to done/YYYY/MM/
       └── Abandoned → moved to cancelled/YYYY/MM/
```

Every status change does two things:
1. Updates the `status` and `updated` fields in frontmatter
2. Appends an entry to the Log section with the date, what changed, and why

## Not everything is a task

Tasks exist for work that spans sessions, requires tracking, or follows an SOP. A quick question, a one-off generation, a simple lookup — these are not tasks. They happen in the session and that is enough.

Use a task when:
- The work will not finish in this session
- Multiple agents need to coordinate on it
- You need to track progress or blockers
- The work follows a defined SOP or workstream
- Someone needs to pick it up later without context from today

## Why this matters

Without tasks, every session is an island. You can export conversations, but a raw conversation log is not a work item — it does not tell the next session what needs to happen, what is blocking, or who should do it.

Tasks give the orchestra a persistent to-do list that any session can read. They are the mechanism that turns a stateless system into one that can sustain work across days and weeks.
