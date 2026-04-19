# Agent Collaboration

## The problem with single agents

Some tasks are too complex or too multifaceted for a single agent. A research project might need deep domain analysis AND technical output generation AND scholarly writing. Asking one agent to do all three produces mediocre results across the board.

## How collaboration works in Agent Orchestra

Agents collaborate through **sequential handoffs**, managed by Larry:

1. Larry breaks a complex task into stages
2. Each stage is assigned to the agent best suited for it
3. Each agent's output becomes the next agent's input
4. Larry manages the sequence and ensures clean transitions

### Example: a three-agent pipeline

Imagine you need to produce a technical report on a complex topic:

```
Task: "Produce a technical analysis of [topic] with visualisations"

Larry's routing plan:
  Stage 1 → Domain Expert: deep analysis and findings
  Stage 2 → Technical Engineer: data processing and visualisations
  Stage 3 → Writer: final report integrating analysis and visuals
```

Each agent works within its guardrails:
- The **domain expert** provides the thinking but does not generate code or write the final prose
- The **technical engineer** produces the visualisations but does not analyse or write
- The **writer** integrates everything into a coherent document but does not re-analyse or re-engineer

## Designing collaborator pairs

When you know two agents will frequently work together, design their profiles to complement each other:

### Complementary responsibilities
Agent A's output should be exactly what Agent B needs as input. If your domain expert produces "compositional briefs" and your technical agent expects "compositional briefs", the handoff is seamless.

### Non-overlapping guardrails
If Agent A "does not generate code" and Agent B "does not do analysis", there is no ambiguity about who does what.

### Shared vocabulary
Both agents should use the same terminology for shared concepts. If Agent A calls something a "brief" and Agent B expects a "specification", the handoff breaks.

## When NOT to use collaboration

Not every task needs multiple agents. Use collaboration when:

- The task genuinely requires **different types of expertise** (analysis + engineering + writing)
- A single agent would need to **switch cognitive modes** mid-task (researching, then building, then evaluating)
- The output quality of each stage matters enough to warrant a **specialist**

Do not use collaboration for tasks a single well-designed agent can handle. Adding agents adds complexity. The goal is the right number of agents, not the most.

## The hub-and-spoke model

All collaboration flows through Larry. Agents never communicate directly with each other. This keeps the system:

- **Auditable** — you can trace every handoff
- **Debuggable** — if something goes wrong, you know which agent produced which output
- **Flexible** — you can change the collaboration sequence without modifying the agents themselves
