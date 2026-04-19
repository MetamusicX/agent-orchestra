# Agent Orchestra: Beyond Coding Agents

## A self-organising AI team for knowledge work without coding

---

There is a growing ecosystem of tools for managing AI coding agents. Platforms like [Multica](https://github.com/multica-ai/multica), [Devin](https://devin.ai/), and [Factory](https://factory.ai/) let you assign GitHub issues to AI teammates who autonomously write code, create pull requests, and close tickets. They are impressive engineering. They are also solving only half the problem.

Most knowledge work is not code.

It is writing a monograph. Analysing a journal for patterns you cannot see from inside your own life. Researching the compositional systems of a historical figure across a seventy-work catalogue. Drafting a libretto in German that is designed to be fragmented and reassembled by a composer. Producing a structured report from a hundred pages of raw notes. Translating a complex brief into publication-ready musical notation.

These tasks require expertise, judgement, and sustained consistency — exactly what a well-designed AI agent can provide. Yet almost every agent framework assumes the agent's job is to produce software.

I needed something different. So I built it.

---

## Agent Orchestra: a team, not a tool

Agent Orchestra is an open-source blueprint for building a self-organising team of AI agents. Each agent has a distinct role, a professional persona, domain-specific expertise, and — crucially — explicit boundaries defining what it does *not* do.

The system ships with four core agents:

- **Atlas** — the Chief of Staff. Atlas never does substantive work. He analyses every incoming request and routes it to the best-fit specialist on the team. If no specialist exists for a given task, Atlas triggers the hiring pipeline to create one.
- **Merlin** — the Senior Researcher. When a new capability is needed, Merlin investigates what a world-class professional in that role actually does — their core skills, their tools, their mental models, their characteristic failure modes. Merlin delivers this as a structured Hire Brief.
- **Nolan** — the Head of AI Talent. Nolan takes Merlin's research and designs a complete agent profile: a name, a persona, a set of responsibilities, and — most importantly — a set of guardrails defining the agent's boundaries.
- **Kai** — the Technical Engineer. Scripting, automation, databases, infrastructure. Kai keeps the system running so that every other agent can focus on their domain.

Everything beyond these four — every specialist, every domain expert, every analyst — is built by you, for your specific needs. Or rather, built by the system itself: you tell Atlas what you need, Merlin researches the role, Nolan designs the agent. Your team grows organically, and each new member is informed by real-world research into what that role actually demands.

No code required. Every agent is a markdown file.

---

## What can non-coding agents actually do?

Once you stop assuming that AI agents exist to generate code, the landscape of useful applications opens dramatically. Here are concrete examples from a working deployment.

### Write scholarly prose

Not summaries. Not blog posts. Dense, analytically precise, carefully argued academic prose — maintaining a consistent voice and register across entire chapters of a monograph.

The key design decision was a single instruction in the agent's guardrails: *"Do not summarise. Expand and deepen."* This matters because without it, every language model defaults to compression. It will condense a rich argument into a tidy paragraph. The guardrail reverses this tendency. The result is an agent that produces genuinely analytical writing — prose that builds and develops ideas rather than flattening them.

A second critical choice was designating the user's own published writing as the style reference — not to imitate, but to match register and intellectual density. The agent writes *as* a scholar, not *about* scholarship.

### Analyse personal journals

A monthly journal exported as a PDF — hundreds of pages of daily entries mixing professional work, athletic training, intellectual reading, personal reflections, encounters with people — analysed and distilled into a structured seven-section report under two thousand words.

The agent identifies patterns the writer cannot see from inside their own life: recurring stress signatures, shifting priorities, relationships that appear more than the writer realises, threads left unresolved from month to month.

The guardrail here is as important as the capability: *"Do not psychoanalyse. Reflect, do not diagnose."* The agent holds up a mirror. It does not play therapist. This boundary is what makes the output trustworthy rather than intrusive.

### Think as a composer thought

This is perhaps the most unusual agent in the system: a domain specialist that has internalised the complete compositional language, techniques, aesthetic commitments, and catalogue of a specific historical composer. The agent does not imitate the composer's surface sound — it thinks compositionally as the composer thought, applying documented systems and procedures to generate new pre-compositional material.

The agent works from structured glossaries of the composer's own terminology, organised both alphabetically and by conceptual domain. Every compositional decision it makes must be articulable in the composer's own terms. The guardrail: *"Do not invent systems or import techniques foreign to the composer's documented practice."*

This is deep domain expertise encoded in natural language — the kind of specialisation that would normally require years of study.

### Generate musical notation

Another agent translates compositional briefs into executable Python scripts that produce publication-ready MusicXML files — handling extended techniques, microtones, complex tuplet structures, and contemporary notation conventions. The agent receives a description of what the music should contain and delivers a `.musicxml` file ready for import into professional notation software.

The guardrail: *"Do not compose. Execute the brief exactly as stated."* The compositional thinking happens elsewhere; this agent is a precision tool for realising it.

### Collaborate across agents

The most powerful configuration is not a single agent but a pipeline. In my system, a domain analyst provides the compositional thinking, a dramaturg provides the textual material, and a notation engineer generates the score. Each agent's guardrails ensure clean handoffs: the analyst does not write text, the dramaturg does not make compositional decisions, the engineer does not alter the brief. Atlas manages the sequence.

This is not a theoretical architecture. It is how I work every day.

### And beyond

The architecture is domain-agnostic. Depending on your field, you might build agents that:

- **Draft legal briefs** — maintaining jurisdictional conventions and citation standards
- **Edit manuscripts** — applying a house style guide with absolute consistency across hundreds of pages
- **Curate research literature** — conducting systematic reviews with explicit inclusion and exclusion criteria
- **Translate with domain expertise** — not just linguistic fluency but mastery of field-specific terminology and conventions
- **Produce clinical summaries** — structured reports from case notes following institutional protocols
- **Design course curricula** — learning structures aligned with specific accreditation frameworks
- **Analyse financial filings** — extracting patterns and anomalies across quarterly reports
- **Write project proposals** — maintaining funder-specific conventions, constraints, and rhetorical expectations

The pattern is always the same: a persona that embodies genuine expertise, responsibilities that define the scope precisely, and guardrails that prevent the agent from drifting beyond its competence.

---

## How is this different from existing agent platforms?

Platforms like [Multica](https://github.com/multica-ai/multica) are excellent at what they do: managing coding agents through a visual project board with issue tracking, real-time progress streaming, and autonomous execution. I installed and tested Multica on my own system — it works well. You assign an issue, an agent picks it up, executes the task, reports progress, and closes the ticket.

But it is built for a specific workflow: software development. Agent Orchestra addresses a different need.

### 1. It is not limited to coding

Most of my agents never write a line of code. They write academic prose, analyse journals, generate compositional material, produce musical notation. The architecture makes no assumptions about output format. A pull request, a chapter draft, a structured report, a MusicXML file — the system treats them all as deliverables.

This is the core insight: **the agent pattern — persona, expertise, guardrails, clear scope — works for any domain of knowledge work**, not only software engineering.

### 2. It is radically simple

There is no platform to install. No web dashboard. No database. No WebSocket connections. No daemon running in the background. No Docker containers to configure.

Every agent is a markdown file. The entire system runs on your LLM's native features: a system prompt for the orchestrator, individual definition files for specialists, and a folder structure for workflow management.

This simplicity is deliberate, not accidental:
- You can read and modify every agent in any text editor
- You can version-control your entire team with git
- You can switch LLM platforms without rebuilding anything
- You can understand the complete system in an afternoon
- You can start in five minutes

The tradeoff is real: you do not get a visual dashboard, you do not get autonomous background execution, you do not get real-time streaming. What you get is a system you fully understand, fully control, and can fully adapt to your needs.

### 3. The team designs its own new members

The self-hiring pipeline — Merlin researches the role, Nolan designs the agent — means you never need to write an agent profile from scratch. You describe the capability you need in plain language. The system investigates what that role demands in the real world and produces a specialist calibrated to those demands.

More importantly, Merlin's research step produces better agents than most users would design manually. When you write an agent prompt yourself, you draw on your own understanding of the role — which may be incomplete or skewed. Merlin investigates what real-world professionals in that field actually do: not just their stated responsibilities, but the mental models that make them effective and the failure modes that make them unreliable. That intelligence flows directly into the agent's guardrails.

---

## The guardrail philosophy

The most counterintuitive lesson from building this system: **what an agent does not do is more important than what it does.**

Without explicit boundaries, agents drift. A researcher starts building things. A writer starts doing research instead of writing. A technical engineer starts making design decisions that belong to the domain expert. Each drift is individually small, but they compound. Within a few interactions, no agent has a clear role, and output quality degrades across the board.

Every agent in Agent Orchestra ends with a line like:

> *Merlin researches. Merlin does not build, hire, or execute tasks.*

> *Kai builds. Kai does not research, hire, or theorise.*

This looks like bureaucracy. It is architecture. The boundary is what makes the specialist a specialist. An agent that knows what it must *not* do produces sharper, more reliable work within the domain it owns.

The guardrail checklist included in the repository asks four questions before any agent is deployed:

1. What is this agent's single core function?
2. Which other agents' territory could it drift into?
3. What would go wrong if it exceeded its scope?
4. Does this agent produce output that another agent consumes?

If you cannot answer all four clearly, the agent is not ready.

---

## Personas are architecture, not decoration

There is a widespread assumption that giving an AI agent a "personality" is cosmetic — a bit of flavour text that makes the interaction more pleasant but does not affect output quality. This is wrong.

"A seasoned backend engineer who prefers clean, simple systems over clever ones" produces fundamentally different code than "a coding assistant." The persona encodes priorities (simplicity over cleverness), aesthetic judgement (clean systems), and experience level (seasoned — meaning: has seen what happens when you over-engineer). These are not decorative attributes. They shape every decision the agent makes.

"A scholar-writer: do not summarise — expand and deepen" produces fundamentally different prose than "a writing assistant." The persona tells the model not just *what* to produce but *how to think* while producing it.

In Agent Orchestra, persona design follows three principles:

1. **Be specific.** Not "helpful and knowledgeable" but "a sharp startup recruiter who deeply cares about fit — not just skills on paper, but the right personality and communication style for the team."
2. **Be behavioural.** Describe how the agent acts and decides, not just what it knows.
3. **Be bounded.** A good persona implies what the agent does *not* do as clearly as what it does.

The most effective personas I have built are the ones that describe a professional identity so precisely that the agent's behaviour becomes predictable — in the best sense. You know what it will prioritise, how it will communicate, and where it will draw the line.

---

## Model selection as cost architecture

A common mistake in multi-agent systems is running every agent on the most powerful available model. This is wasteful and, surprisingly, sometimes counterproductive — the highest-capability models can overthink simple tasks and introduce unnecessary complexity.

In my team of ten agents:

- **The orchestrator and domain experts** run on top-tier models (Claude Opus) — routing quality and analytical depth justify the cost, because errors at this level cascade through the entire system
- **The technical engineer** runs on a mid-tier model (Claude Sonnet) — the tasks are well-defined, structured, and do not require maximum reasoning capability
- **The talent manager** runs on the lightest model (Claude Haiku) — agent profile design is structured work that follows a clear template

The economics are more favourable than they appear. Most agents are idle most of the time — they only consume resources when they have active work. Cost scales with actual usage, not with the size of the team. Maintaining ten well-designed agents is marginally more expensive than maintaining one generalist, and the output is significantly better.

---

## Getting started

Agent Orchestra is open source and available on GitHub:

**[github.com/MetamusicX/agent-orchestra][1]**

The repository includes:
- The four core agents, ready to deploy
- Architecture documentation explaining every design decision in detail
- Templates for building your own specialist agents
- Anonymised examples drawn from a real working deployment
- Setup guides for Claude Code, with adaptation notes for other platforms

Clone it. Copy the core agents into your project. Open your LLM and say: *"Atlas, I need a [role] on the team."*

The system will research the role, design the agent, and add it to your roster. No configuration required. No infrastructure to maintain. Just markdown files and a clear idea about how to organise intelligence.

---

*Works with Claude Code, Codex, Gemini, Cursor Agent, OpenCode, and any LLM agent system that supports system prompts and markdown configuration.*

---

**Paulo de Assis** is a Senior Research Fellow at the Orpheus Institute (Ghent, Belgium) and Principal Investigator of the ERC-funded project *Posthuman Music*. He works at the intersection of artistic research, musical composition, contemporary philosophy, and AI.

[GitHub: MetamusicX][2]

[1]:	https://github.com/MetamusicX/agent-orchestra
[2]:	https://github.com/MetamusicX