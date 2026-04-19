# Agent Orchestra

**Turn one AI assistant into a self-organising team.**

A blueprint for building a team of specialised AI agents — each with a role, a persona, and clear boundaries — orchestrated by a single Chief of Staff. The system even hires its own new members.

**Works with Claude Code, Codex, Gemini, Cursor Agent, OpenCode, and any LLM agent system that supports system prompts and markdown configuration.**

---

## The idea

One AI assistant doing everything is like one employee doing every job. It works — until it doesn't.

Agent Orchestra takes a different approach: a small **core team** handles orchestration, research, hiring, and infrastructure. You then build **your own specialists** — agents tailored to your domain, your projects, your workflow. The system helps you design them.

No code required. Every agent is a markdown file.

---

## Core team (included)

These four agents are the engine. They ship with the blueprint.

| Agent  | Role                    | What it does |
|--------|-------------------------|--------------|
| **Atlas**  | Chief of Staff          | Routes every request to the right agent. Never does the work himself. |
| **Merlin**    | Senior Researcher       | Researches any topic. When a new agent is needed, produces a Hire Brief. |
| **Nolan**  | Head of AI Talent       | Designs and onboards new agents from Merlin's briefs. Maintains the roster. |
| **Kai**    | Technical Engineer      | Scripting, automation, databases, infrastructure. Keeps the system running. |

> See [`core/`](core/) for the full agent profiles.

---

## Your agents (you build these)

The core team is domain-agnostic. Your specialists are not.

Depending on your field, you might build:

- A **writing agent** that drafts in your voice and academic style
- An **evaluator** that assesses applications, reviews, or submissions
- A **domain expert** deeply versed in one subject area
- An **analyst** that reads your journals, logs, or data and extracts patterns
- A **notation engineer** that translates creative briefs into technical output
- A **collaborator pair** — two agents that work together on a single project

The system supports any domain: academic research, software engineering, creative practice, legal work, consulting, journalism, scientific research — anything where specialised expertise matters.

> See [`templates/`](templates/) for blank templates to create your own agents.
> See [`examples/`](examples/) for anonymised examples from a real deployment.

---

## Design principles

### 1. The orchestrator never does the work

Atlas routes. That's it. This separation prevents the "do-everything" problem and ensures every task lands with the right specialist. When Atlas receives a request, he analyses it, identifies the best-fit agent, and delegates — stating who is handling it and why.

### 2. Guardrails define what agents DON'T do

Every agent profile includes explicit constraints. A researcher doesn't build. A writer doesn't research. A builder doesn't hire. This is not bureaucracy — it prevents role drift and keeps output quality high. An agent that knows its boundaries produces sharper work than one that tries to do everything.

### 3. Personas produce better output

An agent with a character — a point of view, a communication style, a professional identity — consistently outperforms a generic prompt. A "seasoned backend engineer who prefers clean, simple systems" produces different (and better) code than "a coding assistant". Persona is not decoration; it is architecture.

### 4. The team grows itself

When you need a new capability:

1. Tell Atlas
2. Atlas asks Merlin to research what that role requires in the real world
3. Merlin delivers a structured Hire Brief
4. Nolan designs the full agent profile — name, persona, responsibilities, guardrails
5. The new agent is ready to work

You never have to write an agent profile from scratch unless you want to.

### 5. Model selection is intentional

Not every agent needs the most powerful (and most expensive) model. Match the model to the cognitive demand:

| Tier | Use for | Examples |
|------|---------|----------|
| **Top tier** (Opus, GPT-4o, Gemini Pro) | Complex reasoning, deep analysis, creative work | Domain experts, writers, analysts |
| **Mid tier** (Sonnet, GPT-4o-mini, Gemini Flash) | Technical tasks, structured output, code | Engineers, notation tools, formatters |
| **Light tier** (Haiku, smaller models) | Simple routing, formatting, administrative | Talent management, roster updates |

This keeps costs proportional to complexity.

### 6. Agents collaborate, not compete

Complex projects often require multiple agents working in sequence. A domain expert provides the thinking. A technical agent generates the output. A writer produces the documentation. Each agent's guardrails ensure clean handoffs with no overlap or contradiction.

### 7. No code required

Every agent is a markdown file. The entire system runs on your agent platform's native features: a system prompt for the orchestrator, individual files for specialists, and a simple folder structure for workflow management.

---

## Quick start

### Claude Code (primary implementation)

1. Clone this repo
2. Copy `core/` agents into your project's `.claude/agents/` directory
3. Copy `core/atlas.md` content into your project's `CLAUDE.md`
4. Create the folder structure (see [`setup/folder-structure.md`](setup/folder-structure.md))
5. Open Claude Code and say: *"Atlas, I need a [role] on the team"*
6. Merlin researches, Nolan builds, you review

### Other platforms

The architecture is platform-agnostic. Adapt the orchestrator prompt and agent definitions to your platform's configuration format. See [`setup/platform-adaptation.md`](setup/platform-adaptation.md) for guidance.

> Full walkthrough: [`setup/getting-started.md`](setup/getting-started.md)

---

## Repository structure

```
agent-orchestra/
├── core/                    # The four core agents (included)
│   ├── atlas.md
│   ├── merlin.md
│   ├── nolan.md
│   └── kai.md
├── architecture/            # How the system works
│   ├── how-it-works.md
│   ├── design-principles.md
│   ├── hiring-pipeline.md
│   ├── collaboration.md
│   └── model-selection.md
├── templates/               # Build your own agents
│   ├── agent-template.md
│   ├── hire-brief-template.md
│   └── guardrails-checklist.md
├── examples/                # Anonymised examples from a real deployment
│   ├── academic-evaluator.md
│   ├── scholarly-writer.md
│   ├── journal-analyst.md
│   └── domain-specialist.md
├── setup/                   # Getting started
│   ├── getting-started.md
│   ├── folder-structure.md
│   ├── claude-code-config.md
│   └── platform-adaptation.md
└── diagrams/
    └── orchestra-topology.mermaid
```

---

## Requirements

- An LLM agent platform (Claude Code, Codex, Gemini, Cursor Agent, or similar)
- API access or a subscription to your chosen platform
- A project directory

---

## Author

**Paulo de Assis**
Senior Research Fellow, Orpheus Institute (Ghent, Belgium)
PI, MetamusicX — ERC Advanced Grant

GitHub: [@MetamusicX](https://github.com/MetamusicX)

This system was developed for a real academic and artistic research practice — managing doctoral admissions, scholarly writing, musical composition, journal analysis, and institutional evaluation — all through a team of AI agents. The core architecture proved general enough to share.

---

## Contributing

Contributions are welcome, especially:

- Adaptations for other platforms (Codex, Gemini, Cursor, etc.)
- New example agents for different domains
- Improvements to the core team profiles
- Translations

---

## Licence

MIT
