# Workstream Template

Use this template to define a multi-agent orchestration flow — a sequence of handoffs coordinated by Atlas. Save it to `Team Knowledge/Workstreams/WS-NNN-short-name.md`.

---

```yaml
---
id: WS-NNN
title: ""
coordinator: atlas              # who manages the flow (always Atlas unless stated)
agents: []                      # ordered list of agents involved
frequency: ""                   # ongoing | per-chapter | per-batch | per-event
status: active                  # active | paused | completed
version: 1
---

# WS-NNN: [Title]

## Purpose
[One sentence: what does this multi-agent workflow accomplish?]

## Agents and roles

| Step | Agent | What they do | Input from | Output to |
|------|-------|-------------|------------|-----------|
| 1 | [name] | [action] | [source] | [next step or location] |
| 2 | [name] | [action] | Step 1 output | [next step or location] |
| 3 | [name] | [action] | Step 2 output | [final location] |

## Trigger
[What initiates this workstream?]

## Handoff protocol
[How output moves between agents. What Atlas checks at each transition.]

## Completion criteria
[How do you know the workstream is done for this cycle?]

## Related SOPs
[List any SOPs that individual agents follow within this workstream.]
```

---

## What makes a good workstream

- **Sequential**: Each step's output is the next step's input. The table makes this visible.
- **Coordinated**: Atlas manages every handoff. No agent-to-agent communication without Atlas in the middle.
- **Bounded**: Clear trigger, clear completion criteria, clear output location.

## When to create a workstream

- A task requires two or more agents working in sequence.
- The same multi-agent sequence has been executed more than once.
- The handoff protocol needs to be explicit to prevent errors.

## Relationship to SOPs

Individual steps within a workstream may follow their own SOPs. For example, a workstream for chapter production might include a research step that follows SOP-002 (meeting extraction) and a writing step that follows the agent's standard procedure. The workstream defines the sequence; the SOPs define the individual steps.
