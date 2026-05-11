# SOPs and Workstreams

## Two types of reusable process

Zissa Agent Orchestra codifies recurring work in two forms:

- **SOPs** (Standard Operating Procedures) — atomic, single-agent procedures for tasks that happen repeatedly
- **Workstreams** — multi-agent orchestration flows for complex processes that require handoffs between agents

Both live in `Team Knowledge/` and are referenced by ID: `SOP-001`, `WS-001`, etc.

## SOPs

An SOP is a step-by-step procedure that one agent follows. It captures how a specific type of work should be done — not in theory, but based on how it has actually been done successfully.

### Structure

```yaml
---
id: SOP-003
title: Transcript clustering and tagging
owner: Kai
frequency: per-batch
inputs: Raw transcript files in Owner's Inbox
outputs: Clustered and tagged transcripts in Completed Work
---
```

The body contains:

- **Steps** — numbered, concrete, in order. Each step describes what to do and what the output should look like.
- **Completion criteria** — how to know the procedure is done correctly.
- **Known issues** — specific pitfalls learned from experience. These are populated from journal entries over time.

### Where SOPs come from

SOPs codify what agents already do. When an agent handles the same type of task multiple times and the approach stabilises, the procedure gets extracted into an SOP. The agent profile says what the agent is capable of. The SOP says exactly how to do a specific recurring task.

Atlas also watches for patterns. When Atlas notices the same kind of request appearing repeatedly with no SOP, Atlas suggests creating one. This keeps the system from relying on agents re-inventing the same process each session.

## Workstreams

A workstream is a multi-step, multi-agent flow. It defines the sequence of handoffs for a complex process that no single agent can handle alone.

### Structure

```yaml
---
id: WS-001
title: New agent hiring
coordinator: Atlas
agents: [Merlin, Nolan]
handoff-protocol: sequential
completion-criteria: Agent profile saved, roster updated, first task delegated
---
```

The body contains:

- **Steps** — each step names the responsible agent, describes the input, the work, and the expected output
- **Handoff points** — where one agent's output becomes the next agent's input, and what Atlas confirms before proceeding
- **Completion criteria** — how to know the entire flow is done

### How Atlas manages workstreams

Atlas does not just kick off a workstream and walk away. Atlas manages each handoff explicitly:

1. Delegates step 1 to the first agent
2. Reviews the output
3. Confirms the handoff to the next agent with the previous output as input
4. Repeats until the final step is complete

This is deliberate. Automated handoffs without confirmation are where quality degrades. Atlas acts as the quality gate between each step.

## How SOPs and workstreams relate

Workstreams reference SOPs where individual steps follow established procedures. A workstream step might say "Kai processes the transcripts following SOP-003." The workstream defines the orchestration. The SOP defines the execution.

This keeps both artefacts clean: SOPs stay focused on one agent doing one thing well. Workstreams stay focused on the sequence and handoffs between agents.

## The learning loop

SOPs are not static. Their "Known issues" sections are populated from agent journal entries — real problems encountered during real work. When Kai discovers that transcripts before 2025-09 use a different naming convention, that becomes a journal entry, and then a known issue in SOP-003.

This means SOPs improve over time without anyone sitting down to rewrite them. The learning happens during work, gets recorded in journals, and flows back into the procedures that govern future work.
