# How Zissa Agent Orchestra Works

## The four layers

Zissa Agent Orchestra has four layers, each with a distinct function:

### Layer 1: The Orchestrator (Atlas)

Atlas is the system prompt — the first thing the AI reads when a session begins. Atlas's job is pure routing:

1. Receive a request from the user
2. Analyse what kind of work it requires
3. Check the team roster for the best-fit agent
4. Delegate to that agent with a clear handoff
5. If no agent exists for the task, trigger the hiring pipeline

Atlas never does substantive work. This constraint is what makes the system reliable — there is always a single point of entry, and every task is handled by a specialist.

### Layer 2: The Core Team (Merlin, Nolan, Kai)

These three agents handle the system's own needs:

- **Merlin** researches what any new role requires — what skills, what persona, what guardrails
- **Nolan** designs and onboards new agents based on Merlin's research
- **Kai** handles technical infrastructure — scripting, databases, automation

Together with Atlas, they form a self-sustaining system that can grow without the user needing to write agent profiles manually.

### Layer 3: Domain Specialists (you build these)

These are the agents that do your actual work — writing, evaluating, analysing, composing, coding, reviewing. They are built by the hiring pipeline (Merlin + Nolan) or manually by the user from the provided templates.

### Layer 4: Team Knowledge (the persistence layer)

Between sessions, an LLM forgets everything. Layer 4 compensates for this with three mechanisms:

- **Tasks** (`Team Knowledge/tasks/`) — Work that spans sessions is tracked as plain markdown files. Folder location is status: `open/`, `in-progress/`, `done/`, `cancelled/`. Atlas walks open and in-progress tasks at session start, so the team knows what's waiting before doing anything else.
- **Agent Journals** (`Team/journals/<agent-name>/`) — When an agent learns something durable — an anti-pattern, a decision rule, a process note — it gets written down. Next time Atlas delegates to that agent, relevant journal entries are included in the brief. Learning compounds across sessions.
- **Session Logs** (`Session Logs/`) — Structured summaries of what happened, written by Atlas at session close. Not raw transcripts — concise records of what the team worked on, what changed, what decisions were made, and what remains open.
- **SOPs and Workstreams** (`Team Knowledge/SOPs/` and `Team Knowledge/Workstreams/`) — Codified procedures. SOPs are atomic, single-agent procedures for recurring tasks. Workstreams are multi-agent orchestration flows. Atlas references these when delegating, ensuring consistency even when session context is lost.

This layer is what makes the team genuinely persistent. Without it, every session starts from zero. With it, the team picks up where it left off.

## The workflow

```
User request
    │
    ▼
  Atlas (analyses and routes)
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
                          Merlin researches the role
                               │
                               ▼
                          Merlin delivers Hire Brief
                               │
                               ▼
                          Nolan designs the agent
                               │
                               ▼
                          New agent added to roster
                               │
                               ▼
                          Atlas delegates the original task
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
│   └── journals/        # Per-agent durable insights
│       ├── [agent1]/
│       └── [agent2]/
├── Team Knowledge/      # Operational knowledge (Layer 4)
│   ├── tasks/           # open/, in-progress/, done/, cancelled/
│   ├── SOPs/            # Standard Operating Procedures
│   └── Workstreams/     # Multi-agent orchestration flows
├── Session Logs/        # Structured session summaries
│   └── INDEX.md
├── CLAUDE.md            # Atlas's system prompt (Claude Code)
└── .claude/agents/      # Agent definition files (Claude Code)
```

## How agents communicate

Agents do not talk to each other directly. All communication flows through Atlas or through the folder structure:

1. **Atlas delegates** a task to an agent
2. The agent **executes** and places output in the appropriate location
3. If the output needs further work by another agent, **Atlas routes** it forward
4. The user reviews output in **Team Inbox** and moves finished work to **Completed Work**

This hub-and-spoke model keeps things simple and auditable. You always know who did what.

## The roster

The roster (`Team/ROSTER.md`) is a living document maintained by Nolan. It lists every active agent with their role and status:

```markdown
# Team Roster

| Name   | Role                  | Status | Journal |
|--------|-----------------------|--------|---------|
| Merlin    | Senior Researcher     | Active | `journals/merlin/` |
| Nolan  | Head of AI Talent     | Active | `journals/nolan/` |
| Kai    | Technical Engineer    | Active | `journals/kai/` |
| [Your agents appear here as you build them]  |        |         |
```

The roster is the team's single source of truth. Atlas consults it before every delegation.
