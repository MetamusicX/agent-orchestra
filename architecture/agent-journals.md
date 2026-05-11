# Agent Journals

## The problem with institutional knowledge

Agents learn things during work. Kai discovers that a particular API returns dates in an unexpected format. Merlin finds that a specific research database has unreliable abstracts before 2020. These insights are valuable — but without a place to record them, they vanish at the end of the session.

Journals give every agent a persistent memory of what they have learned.

## How journals work

Each agent has a journal directory at `Team/journals/<agent-name>/`. Journal entries are short `.md` files — one insight per file.

```
Team/journals/
├── kai/
│   ├── 2026-05-03-transcript-naming.md
│   ├── 2026-05-08-api-date-format.md
│   └── ...
├── merlin/
│   ├── 2026-04-28-database-abstracts.md
│   └── ...
└── ...
```

## Entry structure

Every journal entry has YAML frontmatter and a three-part body:

```yaml
---
agent: Kai
date: 2026-05-03
task: TASK-042
type: anti-pattern
---
```

The `type` field is one of:
- **insight** — something learned that improves future work
- **anti-pattern** — a mistake or pitfall to avoid
- **decision-rule** — a conditional rule for handling a specific situation
- **process-note** — an observation about how a procedure works in practice

The body has three sections:

```markdown
## Context
What was happening when this was learned.

## Insight
The specific thing learned, stated clearly and concretely.

## Applies when
The conditions under which this insight is relevant.
```

## "Applies when" is the critical section

Without it, journal entries become a pile of vaguely useful observations. "Applies when" forces specificity — it defines the trigger condition for the insight.

Good:
> Applies when: Processing transcript files with dates before 2025-09. These use the old naming convention `YYYYMMDD_raw.txt` instead of `YYYY-MM-DD_clean.txt`.

Bad:
> Applies when: Working with old transcripts.

The first version tells a future session exactly when to apply the insight. The second is too vague to be actionable.

## How Atlas uses journals

Before delegating a task, Atlas checks the assigned agent's journal for entries relevant to the work. If Kai is about to process transcripts from 2024, Atlas includes the naming convention entry in the delegation brief.

This means the agent starts the task with its own accumulated wisdom, not from zero. The more work an agent does, the more journal entries accumulate, and the better-informed future delegations become.

## When entries are written

Journal entries are written in two situations:

1. **After task completion** — Atlas (or the agent itself) identifies durable insights from the work and writes them as entries
2. **During session close** — as part of the session logging process, Atlas reviews the session for insights worth preserving

Not every task produces a journal entry. Entries are for things worth remembering — specific, actionable lessons that will change how future work is done.

## What journals are NOT

Journals are not retrospectives. They do not summarise a task or reflect on how it went. Each entry captures one specific lesson. If a task produces three insights, that is three separate entries, each with its own "Applies when" section.

Journals are also not logs. Session logs track what happened chronologically. Journal entries are organised by agent and by relevance, not by time.

## The feedback loop

Journal entries feed into SOP "Known issues" sections. When an insight applies broadly to a recurring procedure, it gets promoted from a journal entry into the SOP itself. This is the connection between operational memory and codified process:

```
Work happens → insight emerges → journal entry written →
pattern recognised → SOP "Known issues" updated →
future work benefits automatically
```

Learning compounds across sessions. Each task leaves the system slightly smarter than before.
