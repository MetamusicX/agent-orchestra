# How Agent Orchestra Works

## The three layers

Agent Orchestra has three layers, each with a distinct function:

### Layer 1: The Orchestrator (Larry)

Larry is the system prompt — the first thing the AI reads when a session begins. Larry's job is pure routing:

1. Receive a request from the user
2. Analyse what kind of work it requires
3. Check the team roster for the best-fit agent
4. Delegate to that agent with a clear handoff
5. If no agent exists for the task, trigger the hiring pipeline

Larry never does substantive work. This constraint is what makes the system reliable — there is always a single point of entry, and every task is handled by a specialist.

### Layer 2: The Core Team (PAX, Nolan, KAI)

These three agents handle the system's own needs:

- **PAX** researches what any new role requires — what skills, what persona, what guardrails
- **Nolan** designs and onboards new agents based on PAX's research
- **KAI** handles technical infrastructure — scripting, databases, automation

Together with Larry, they form a self-sustaining system that can grow without the user needing to write agent profiles manually.

### Layer 3: Domain Specialists (you build these)

These are the agents that do your actual work — writing, evaluating, analysing, composing, coding, reviewing. They are built by the hiring pipeline (PAX + Nolan) or manually by the user from the provided templates.

## The workflow

```
User request
    │
    ▼
  Larry (analyses and routes)
    │
    ├── Known task type → Delegate to existing specialist
    │                          │
    │                          ▼
    │                     Agent executes
    │                          │
    │                          ▼
    │                     Output to Team Inbox
    │
    └── Unknown task type → Trigger hiring pipeline
                               │
                               ▼
                          PAX researches the role
                               │
                               ▼
                          PAX delivers Hire Brief
                               │
                               ▼
                          Nolan designs the agent
                               │
                               ▼
                          New agent added to roster
                               │
                               ▼
                          Larry delegates the original task
```

## Folder structure

The system uses a simple folder structure to manage workflow:

```
your-project/
├── Owner's Inbox/       # You drop requests and files here
├── Team Inbox/          # Agents deliver output here for your review
├── Completed Work/      # Finished deliverables (one subfolder per task)
├── Team/                # Agent profiles and roster
│   ├── ROSTER.md
│   ├── [Agent1].md
│   ├── [Agent2].md
│   └── ...
├── CLAUDE.md            # Larry's system prompt (Claude Code)
└── .claude/agents/      # Agent definition files (Claude Code)
```

## How agents communicate

Agents do not talk to each other directly. All communication flows through Larry or through the folder structure:

1. **Larry delegates** a task to an agent
2. The agent **executes** and places output in the appropriate location
3. If the output needs further work by another agent, **Larry routes** it forward
4. The user reviews output in **Team Inbox** and moves finished work to **Completed Work**

This hub-and-spoke model keeps things simple and auditable. You always know who did what.

## The roster

The roster (`Team/ROSTER.md`) is a living document maintained by Nolan. It lists every active agent with their role and status:

```markdown
# Team Roster

| Name   | Role                  | Status |
|--------|-----------------------|--------|
| PAX    | Senior Researcher     | Active |
| Nolan  | Head of AI Talent     | Active |
| KAI    | Technical Engineer    | Active |
| [Your agents appear here as you build them]  |        |
```

The roster is the team's single source of truth. Larry consults it before every delegation.
