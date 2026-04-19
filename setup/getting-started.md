# Getting Started

This guide walks you through setting up Agent Orchestra from scratch. In 15 minutes, you'll have a working team with an orchestrator, a researcher, a talent manager, and an engineer — ready to build your own specialists.

## Step 1: Create your project directory

Create a folder for your project (or use an existing one):

```bash
mkdir my-project
cd my-project
```

## Step 2: Set up the folder structure

```bash
mkdir -p "Owner's Inbox" "Team Inbox" "Completed Work" "Team"
```

| Folder | Purpose |
|---|---|
| `Owner's Inbox` | You drop files and requests here |
| `Team Inbox` | Agents deliver output here for your review |
| `Completed Work` | Finished deliverables (one subfolder per task) |
| `Team` | Agent profiles and roster |

## Step 3: Install the core team

### For Claude Code:

```bash
# Create the agents directory
mkdir -p .claude/agents

# Copy the core agent files
cp path/to/agent-orchestra/core/pax.md .claude/agents/pax.md
cp path/to/agent-orchestra/core/nolan.md .claude/agents/nolan.md
cp path/to/agent-orchestra/core/kai.md .claude/agents/kai.md

# Set up Larry as the orchestrator
cp path/to/agent-orchestra/core/larry.md CLAUDE.md
```

### For other platforms:

Copy the content of `core/larry.md` into your platform's system prompt. Then adapt the agent definition files to your platform's format (see [`platform-adaptation.md`](platform-adaptation.md)).

## Step 4: Create the initial roster

Create `Team/ROSTER.md`:

```markdown
# Team Roster

| Name   | Role                  | Status |
|--------|-----------------------|--------|
| PAX    | Senior Researcher     | Active |
| Nolan  | Head of AI Talent     | Active |
| KAI    | Technical Engineer    | Active |

---
*Maintained by Nolan.*
```

Also copy the core agent profiles into `Team/` so Larry can reference them:

```bash
cp path/to/agent-orchestra/core/pax.md Team/PAX.md
cp path/to/agent-orchestra/core/nolan.md Team/NOLAN.md
cp path/to/agent-orchestra/core/kai.md Team/KAI.md
```

## Step 5: Test the system

Open your LLM agent platform in your project directory and try:

**Test 1 — Basic routing:**
> "Larry, what's the current team roster?"

Larry should check `Team/ROSTER.md` and report back.

**Test 2 — Delegation:**
> "Larry, I need PAX to research what makes an excellent copy editor."

Larry should route to PAX. PAX should return a structured research brief.

**Test 3 — The full hiring pipeline:**
> "Larry, I need a copy editor on the team."

Larry should:
1. Route to PAX for a Hire Brief
2. Pass PAX's brief to Nolan
3. Nolan should create the agent profile in `Team/`
4. Nolan should update the roster

## Step 6: Build your first custom agent

You have two paths:

### Path A: Let the system hire (recommended)
Tell Larry what you need. The PAX → Nolan pipeline will design the agent for you.

### Path B: Build manually
Copy `templates/agent-template.md`, fill it in, and save it to both `Team/[NAME].md` and `.claude/agents/[name].md` (or your platform's equivalent). Update `Team/ROSTER.md`.

## You're ready

Your team is operational. As you work, you'll discover new capabilities you need — and the system will grow to meet them.
