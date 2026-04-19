# Model Selection

## The principle

Not every agent needs the most powerful model. Matching model capability to role complexity keeps costs proportional and performance optimal.

## The three tiers

### Top tier — complex reasoning

Use for agents that need to reason deeply, handle nuance, produce creative or scholarly output, or make judgement calls.

| Platform | Model | Use cases |
|----------|-------|-----------|
| Anthropic | Claude Opus | Domain experts, writers, analysts, evaluators |
| OpenAI | GPT-4o | Complex reasoning, creative tasks |
| Google | Gemini Pro | Deep analysis, research |

**Assign to:** Atlas (routing quality matters), Merlin (research depth matters), domain specialists, writers, evaluators, analysts.

### Mid tier — structured execution

Use for agents that execute well-defined tasks, produce structured output, write code, or process data.

| Platform | Model | Use cases |
|----------|-------|-----------|
| Anthropic | Claude Sonnet | Technical tasks, code, structured output |
| OpenAI | GPT-4o-mini | Engineering, formatting |
| Google | Gemini Flash | Technical processing |

**Assign to:** Kai (engineering), technical agents, notation tools, formatters, data processors.

### Light tier — simple tasks

Use for agents that perform administrative work, manage rosters, format documents, or handle simple structured operations.

| Platform | Model | Use cases |
|----------|-------|-----------|
| Anthropic | Claude Haiku | Simple routing, formatting, admin |
| OpenAI | Smaller models | Roster management, templates |
| Google | Smaller models | Administrative tasks |

**Assign to:** Nolan (agent design is structured, not complex), administrative agents.

## How to decide

Ask yourself: **What is the hardest cognitive task this agent will perform?**

- If the answer involves **judgement, nuance, or creativity** → top tier
- If the answer involves **structured execution or code** → mid tier
- If the answer involves **formatting or simple decisions** → light tier

## Cost implications

In a typical team of 8-10 agents:

- 1 orchestrator on top tier (always active)
- 1-2 core team members on mid/light tier (active as needed)
- 3-5 domain specialists on top tier (active only when working)
- 1-2 technical agents on mid tier (active only when working)

Most agents are idle most of the time. Cost scales with usage, not with team size. Having ten well-designed agents is not ten times more expensive than having one — it's marginally more expensive and significantly more effective.
