# Getting Started

This guide walks you through setting up Zissa Agent Orchestra from scratch. In 15 minutes, you'll have a working team with an orchestrator, a researcher, a talent manager, and an engineer — ready to build your own specialists.

## Step 1: Create your project directory

Create a folder for your project (or use an existing one):

```bash
mkdir my-project
cd my-project
```

## Step 2: Set up the folder structure

```bash
mkdir -p "Owner's Inbox" "Team Inbox" "Completed Work" "Team" "Team/journals"
mkdir -p "Team Knowledge/tasks/open" "Team Knowledge/tasks/in-progress"
mkdir -p "Team Knowledge/tasks/done" "Team Knowledge/tasks/cancelled"
mkdir -p "Team Knowledge/SOPs" "Team Knowledge/Workstreams"
mkdir -p "Session Logs"
```

| Folder | Purpose |
|---|---|
| `Owner's Inbox` | You drop files and requests here |
| `Team Inbox` | Agents deliver output here for your review |
| `Completed Work` | Finished deliverables (one subfolder per task) |
| `Team` | Agent profiles and roster |
| `Team Knowledge` | Tasks, SOPs, and workstreams |
| `Session Logs` | Structured session summaries |

## Step 3: Install the core team

### For Claude Code:

```bash
# Create the agents directory
mkdir -p .claude/agents

# Copy the core agent files
cp path/to/zissa-agent-orchestra/core/merlin.md .claude/agents/merlin.md
cp path/to/zissa-agent-orchestra/core/nolan.md .claude/agents/nolan.md
cp path/to/zissa-agent-orchestra/core/kai.md .claude/agents/kai.md

# Set up Atlas as the orchestrator
cp path/to/zissa-agent-orchestra/core/atlas.md CLAUDE.md
```

### For other platforms:

Copy the content of `core/atlas.md` into your platform's system prompt. Then adapt the agent definition files to your platform's format (see [`platform-adaptation.md`](platform-adaptation.md)).

## Step 4: Create the initial roster

Create `Team/ROSTER.md`:

```markdown
# Team Roster

| Name   | Role                  | Status |
|--------|-----------------------|--------|
| Merlin    | Senior Researcher     | Active |
| Nolan  | Head of AI Talent     | Active |
| Kai    | Technical Engineer    | Active |

---
*Maintained by Nolan.*
```

Also copy the core agent profiles into `Team/` and create their journal directories:

```bash
cp path/to/zissa-agent-orchestra/core/merlin.md Team/Merlin.md
cp path/to/zissa-agent-orchestra/core/nolan.md Team/NOLAN.md
cp path/to/zissa-agent-orchestra/core/kai.md Team/Kai.md

# Create journal directories for each core agent
mkdir -p Team/journals/merlin Team/journals/nolan Team/journals/kai
```

Create the Session Logs index:

```bash
cat > "Session Logs/INDEX.md" << 'EOF'
# Session Logs

| Date | Agents | Summary | Tasks |
|------|--------|---------|-------|
EOF
```

## Step 5: Test the system

Open your LLM agent platform in your project directory and try:

**Test 1 — Basic routing:**
> "Atlas, what's the current team roster?"

Atlas should check `Team/ROSTER.md` and report back.

**Test 2 — Delegation:**
> "Atlas, I need Merlin to research what makes an excellent copy editor."

Atlas should route to Merlin. Merlin should return a structured research brief.

**Test 3 — The full hiring pipeline:**
> "Atlas, I need a copy editor on the team."

Atlas should:
1. Route to Merlin for a Hire Brief
2. Pass Merlin's brief to Nolan
3. Nolan should create the agent profile in `Team/`
4. Nolan should update the roster

## Step 6: Test the persistence layer

**Test 4 — Task Walker:**
> "Atlas, what's open?"

Atlas should walk `Team Knowledge/tasks/open/` and `Team Knowledge/tasks/in-progress/` and report that nothing is queued yet.

**Test 5 — Session close:**
> "Close session"

Atlas should write a session log to `Session Logs/`, update `INDEX.md`, and confirm.

## Step 7: Build your first custom agent

You have two paths:

### Path A: Let the system hire (recommended)
Tell Atlas what you need. The Merlin → Nolan pipeline will design the agent for you.

### Path B: Build manually
Copy `templates/agent-template.md`, fill it in, and save it to both `Team/[NAME].md` and `.claude/agents/[name].md` (or your platform's equivalent). Update `Team/ROSTER.md`.

## You're ready

Your team is operational. As you work, you'll discover new capabilities you need — and the system will grow to meet them.
