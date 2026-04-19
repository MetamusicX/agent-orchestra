# The Hiring Pipeline

The hiring pipeline is Agent Orchestra's most distinctive feature: the system can design and onboard its own new members.

## How it works

```
You need a new capability
        │
        ▼
"Larry, I need a [role] on the team"
        │
        ▼
Larry asks PAX to research the role
        │
        ▼
PAX investigates: what does a world-class
professional in this role actually do?
        │
        ▼
PAX delivers a Hire Brief to Nolan
        │
        ▼
Nolan designs the full agent profile:
name, persona, responsibilities, guardrails
        │
        ▼
Nolan saves the profile to Team/
and updates the roster
        │
        ▼
Larry delegates the original task
to the new agent
```

## Why this matters

Most people write agent prompts from their own understanding of a role. This works for roles they know well, but produces shallow agents for roles outside their expertise.

PAX changes this. When you say "I need an evaluator for academic hiring", PAX doesn't just write a prompt — PAX researches what real evaluation experts do: their assessment frameworks, their failure modes, what distinguishes an excellent evaluator from a mediocre one. This intelligence flows directly into the agent's design.

The result: agents that are more nuanced and more reliable than what you would design from scratch.

## The Hire Brief

PAX produces a structured document for Nolan:

```
HIRE BRIEF — [Role Name]
Requested by: Larry
Date: [date]

1. WHAT THIS PERSON DOES (in a real organisation)
   What the role looks like in practice, not in theory.

2. CORE SKILLS REQUIRED
   The non-negotiable competencies.

3. TOOLS AND METHODS THEY USE
   How they actually work — frameworks, processes, tools.

4. WHAT MAKES THEM EXCELLENT (vs average)
   The difference between good and great in this role.

5. EDGE CASES AND FAILURE MODES TO AVOID
   Where people in this role typically go wrong.

6. RECOMMENDED PERSONA TRAITS FOR THE AI VERSION
   How the AI agent should behave to embody this role.
```

## What Nolan does with it

Nolan takes PAX's research and produces a complete agent profile:

- **Name** — a short, memorable name for the agent
- **Role title** — clear and specific
- **Persona** — 2-3 sentences defining character and behaviour
- **Primary responsibilities** — numbered list, usually 3-5 items
- **How to engage** — how the user addresses this agent
- **Guardrails** — what the agent explicitly does NOT do

Nolan then saves the profile to `Team/[NAME].md` and updates `Team/ROSTER.md`.

## Example

**User:** "Larry, I need someone who can evaluate grant proposals."

**Larry:** "Routing to PAX for a Hire Brief on grant evaluation expertise."

**PAX** researches grant evaluation — what panels look for, common weaknesses, evaluation frameworks (NIH, ERC, NSF), how experienced reviewers think — and delivers the brief.

**Nolan** designs an agent: GRANT (Grant Review and Assessment Analyst), with a persona of a "veteran panel member who has reviewed hundreds of proposals and knows the difference between promising and fundable", with guardrails that GRANT does not write proposals (only evaluates them) and does not make funding decisions (only advises).

**Larry** delegates the original grant evaluation task to GRANT.

The entire process happens in one conversation. No manual configuration required.
