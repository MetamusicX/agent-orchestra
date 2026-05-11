# Team Knowledge Structure

This guide explains how to set up the Team Knowledge folder, agent journals, and session logs — the persistence layer that lets your team pick up where it left off across sessions.

## Why this exists

Between sessions, an LLM forgets everything. Tasks, journals, and session logs compensate for this by making the team's operational state and accumulated learning persistent as plain markdown files.

## What to create

### Team Knowledge folder

```
Team Knowledge/
├── tasks/
│   ├── open/           # Work waiting to be picked up
│   ├── in-progress/    # Work currently being done
│   ├── done/           # Completed work (archived by YYYY/MM/)
│   └── cancelled/      # Cancelled work (archived by YYYY/MM/)
├── SOPs/               # Standard Operating Procedures
└── Workstreams/        # Multi-agent orchestration flows
```

Create the initial date folders under `done/` and `cancelled/` for the current year and month.

### Agent journals

```
Team/
├── [existing agent profiles]
└── journals/
    ├── [agent-1-name]/
    ├── [agent-2-name]/
    └── ...
```

Create one subdirectory per active agent. Use lowercase names matching the agent profile filenames.

### Session Logs

```
Session Logs/
└── INDEX.md
```

The INDEX.md file is a table tracking all session logs:

```markdown
| Date | Agents | Summary | Tasks |
|------|--------|---------|-------|
```

## How it connects to Atlas

After creating the folder structure, add the following sections to your CLAUDE.md (Atlas prompt):

1. **Task Walker** — Atlas walks `tasks/open/` and `tasks/in-progress/` at session start
2. **Session Logging** — Atlas writes a session log on session close
3. **SOP/Workstream Awareness** — Atlas references SOPs when delegating and follows workstream handoff protocols
4. **Agent Journals** — Atlas checks journals before delegating and writes entries for durable insights

See `core/atlas.md` for the complete sections to add.

## Writing your first SOP

Start by codifying a workflow your team already performs regularly:

1. Identify a recurring task (e.g., monthly report, regular evaluation, data extraction)
2. Open `templates/sop-template.md` for the structure
3. Fill in the steps based on what the agent already does (check the agent's profile for their procedure)
4. Save as `Team Knowledge/SOPs/SOP-001-short-name.md`

The best first SOP is the workflow you run most often — it's the one where consistency matters most.

## Writing your first Workstream

Look for a task that already involves two or more agents in sequence:

1. Open `templates/workstream-template.md`
2. Fill in the agents-and-roles table
3. Define the handoff protocol (what Atlas checks between steps)
4. Save as `Team Knowledge/Workstreams/WS-001-short-name.md`

## Growing the system

- **New SOPs** emerge naturally: when Atlas notices a recurring pattern, it suggests creating one
- **Journal entries** feed into SOPs: the "Known issues" section of an SOP is populated from agent journal entries
- **New task date folders** are created as needed: when a task is completed in a new month, Atlas creates the `done/YYYY/MM/` directory
- **Workstreams** are created when multi-agent sequences become established
