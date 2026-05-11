# SOP Template

Use this template to define a Standard Operating Procedure — an atomic, repeatable procedure owned by a single agent. Save it to `Team Knowledge/SOPs/SOP-NNN-short-name.md`.

---

```yaml
---
id: SOP-NNN
title: ""
owner: ""                       # which agent executes this
frequency: ""                   # monthly | weekly | on-demand | per-event
inputs: []                      # what materials are needed
outputs: []                     # what deliverables are produced
output-location: ""             # where deliverables go
last-executed: YYYY-MM-DD
version: 1
---

# SOP-NNN: [Title]

## Purpose
[One sentence: why does this procedure exist?]

## Trigger
[What causes this SOP to be invoked? Who initiates it?]

## Prerequisites
[What must be true before starting? Materials available, prior tasks complete, etc.]

## Steps
1. [Step 1 — specific, executable instruction]
2. [Step 2]
3. [Step 3]
4. [Continue as needed]

## Output specification
[What the deliverable must look like. Format, location, naming convention.]

## Completion criteria
[How do you know this SOP has been executed correctly?]

## Known issues
[Edge cases, common mistakes, things that have gone wrong before. Updated from journal entries.]
```

---

## What makes a good SOP

- **Atomic**: One agent, one procedure, one clear outcome.
- **Executable**: Each step is a concrete action, not a vague guideline.
- **Versioned**: When the procedure changes, increment the version and note what changed.
- **Connected**: The `Known issues` section is populated from journal entries — this is where learning feeds back into procedures.

## When to create an SOP

- A workflow has been executed more than twice with the same basic steps.
- An agent's profile describes a procedure that should be extracted and made referenceable.
- Atlas observes a recurring pattern and suggests formalising it.

## How SOPs are used

When Atlas delegates a task that matches a known SOP (by assignee + task type), Atlas tells the agent to follow the SOP and references it by ID and path. The agent follows the steps. This ensures consistency across sessions, even when context from previous sessions is lost.
