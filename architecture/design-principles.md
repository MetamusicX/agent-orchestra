# Design Principles

These seven principles govern how Agent Orchestra works. They are not suggestions — they are load-bearing constraints that make the system reliable.

## 1. The orchestrator never does the work

Larry routes. That's it.

When the orchestrator starts doing substantive work — writing, researching, coding — two things break: the routing degrades (because the orchestrator is distracted), and the quality drops (because a generalist is doing a specialist's job).

The constraint is simple: Larry analyses the request, identifies the right agent, and delegates. Larry confirms the handoff. Larry never writes a paragraph, never runs a query, never evaluates a candidate.

## 2. Guardrails define what agents DON'T do

Every agent profile includes an explicit "Guardrails" section listing what the agent must never do. This is as important as the responsibilities section — often more so.

Why: without guardrails, agents drift. A researcher starts building things. A writer starts doing research. A builder starts making design decisions. Each drift is small, but they compound into a system where no agent has a clear role and output quality degrades.

Good guardrails:
- "Merlin does not hire. Merlin does not build. Merlin researches and briefs."
- "KAI does not over-engineer. Simple and working beats clever and fragile."
- "Nolan does not research. Nolan does not carry out tasks. Nolan hires and onboards."

Every guardrail ends with what the agent *does* do, reinforcing the boundary.

## 3. Personas produce better output

An agent with a character — a point of view, a communication style, a professional identity — consistently outperforms a generic prompt.

"A seasoned backend engineer who prefers clean, simple systems over clever ones" produces different output than "a coding assistant". The persona shapes decisions at every level: what to prioritise, how to communicate, when to push back, what to leave out.

Effective personas are:
- **Specific** — not "helpful and knowledgeable" but "a sharp startup recruiter who deeply cares about fit"
- **Behavioural** — they describe how the agent acts, not just what it knows
- **Bounded** — they imply what the agent does NOT do as much as what it does

## 4. The team grows itself

The hiring pipeline (Merlin + Nolan) means you never have to write an agent profile from scratch. The process:

1. You tell Larry you need a new capability
2. Larry asks Merlin to research what that role requires in the real world
3. Merlin delivers a structured Hire Brief: what the role does, core skills, tools, what makes someone excellent at it, failure modes, recommended persona traits
4. Nolan takes the Hire Brief and designs the full agent profile: name, persona, responsibilities, communication style, guardrails
5. The new agent is added to the roster and ready to work

This matters because Merlin's research step produces better agents than you would likely design from scratch. Merlin investigates what real-world professionals in that role actually do — their mental models, their tools, their failure modes — and this intelligence flows into the agent's design.

## 5. Model selection is intentional

Not every agent needs the most powerful model. Matching the model tier to the cognitive demand of the role keeps costs proportional to complexity:

- **Top tier** (Opus, GPT-4o, Gemini Pro): Complex reasoning, nuanced analysis, creative or scholarly work. Use for domain experts, writers, analysts.
- **Mid tier** (Sonnet, GPT-4o-mini, Gemini Flash): Technical tasks, structured output, code generation. Use for engineers, formatters, notation tools.
- **Light tier** (Haiku, smaller models): Simple structured tasks, administrative work, roster management. Use for talent management, routing support.

The orchestrator (Larry) should run on the top tier, since routing quality affects everything downstream.

## 6. Agents collaborate, not compete

Complex projects often require multiple agents working in sequence:

- A domain expert provides the analytical thinking
- A technical agent generates structured output
- A writer produces the final documentation

Each agent's guardrails ensure clean handoffs. The domain expert does not try to generate the technical output. The technical agent does not try to write the documentation. Larry manages the sequence.

This means you can build collaborator pairs or trios for complex workflows — agents designed to pass work between them in a defined order.

## 7. No code required

Every agent is a markdown file. The entire system runs on your LLM platform's native features:

- A system prompt for the orchestrator
- Individual definition files for each agent
- A folder structure for workflow management

There is no framework to install, no API to configure, no runtime to maintain. If you can edit a text file, you can build and modify agents.
