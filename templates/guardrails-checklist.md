# Guardrails Checklist

Use this checklist when designing guardrails for a new agent. Good guardrails are the difference between a reliable specialist and an unreliable generalist.

## Before writing guardrails, answer these questions:

- [ ] **What is this agent's single core function?** (If you can't state it in one sentence, the role may be too broad.)
- [ ] **Which other agents' territory could this agent drift into?** (Research? Building? Hiring? Writing? Evaluating?)
- [ ] **What would go wrong if this agent exceeded its scope?** (Duplicate work? Contradictory output? Quality drop?)
- [ ] **Does this agent produce output that another agent consumes?** (If yes, guardrails must ensure clean handoff boundaries.)

## Guardrail patterns

### The boundary statement
State what the agent does NOT do, then restate what it DOES do:

> "[Name] does not research — that's Merlin's job."
> "[Name] does not make decisions — [Name] produces assessments; the decision belongs to the user."

### The quality constraint
Prevent common failure modes:

> "[Name] does not over-engineer. Simple and working beats clever and fragile."
> "[Name] does not speculate beyond what is documented in source materials."
> "[Name] does not soften critical assessments to avoid discomfort."

### The scope boundary
Prevent the agent from expanding its own role:

> "[Name] does not suggest alternatives unless asked."
> "[Name] does not modify existing work without explicit request."
> "[Name] does not introduce external sources without authorisation."

### The verification requirement
Ensure quality before completion:

> "[Name] always confirms a successful operation before declaring a task done."
> "[Name] always indicates when information comes from [source] versus general knowledge."

## The closing line

Every agent profile should end with a one-line summary that reinforces the boundary:

> *[Name] [verbs]. [Name] does not [other verbs].*

Examples:
- *Merlin researches. Merlin does not build, hire, or execute tasks.*
- *Kai builds. Kai does not research, hire, or theorise.*
- *Nolan hires. Nolan does not research, build, or execute tasks.*

This line is both documentation and a behavioural anchor.
