# Claude Code Configuration

This guide covers the specific setup for running Agent Orchestra with Claude Code.

## Key files

### CLAUDE.md — The orchestrator

`CLAUDE.md` is Claude Code's project-level system prompt. When you open Claude Code in a directory containing `CLAUDE.md`, its contents are automatically loaded as context.

Copy the contents of `core/larry.md` into your project's `CLAUDE.md`. This makes Larry the default orchestrator for every session in that project.

### .claude/agents/ — Agent definitions

Claude Code supports sub-agents defined as markdown files in `.claude/agents/`. Each file becomes an invocable agent with its own persona and instructions.

```
.claude/agents/
├── merlin.md
├── nolan.md
├── kai.md
└── [your-agents].md
```

Agent files use frontmatter to configure the agent:

```yaml
---
name: merlin
description: Senior Researcher. Use Merlin for deep research tasks and producing Hire Briefs.
model: claude-opus-4-6
tools: WebSearch, WebFetch, Read, Glob, Grep
---

[Agent profile content here]
```

### Frontmatter fields

| Field | Purpose | Example |
|-------|---------|---------|
| `name` | Agent identifier | `merlin` |
| `description` | When to use this agent (shown in agent selection) | `Senior Researcher. Use Merlin for deep research tasks.` |
| `model` | Which Claude model to use | `claude-opus-4-6`, `claude-sonnet-4-6`, `claude-haiku-4-5-20251001` |
| `tools` | Which tools the agent can access | `Read, Write, Edit, Bash, Glob, Grep, WebSearch, WebFetch` |

### Model options

| Model ID | Tier | Use for |
|----------|------|---------|
| `claude-opus-4-6` | Top | Complex reasoning, analysis, creative work |
| `claude-sonnet-4-6` | Mid | Technical tasks, code, structured output |
| `claude-haiku-4-5-20251001` | Light | Simple tasks, formatting, admin |

### Tool options

| Tool | What it does |
|------|-------------|
| `Read` | Read files |
| `Write` | Create new files |
| `Edit` | Modify existing files |
| `Bash` | Run terminal commands |
| `Glob` | Search for files by pattern |
| `Grep` | Search file contents |
| `WebSearch` | Search the web |
| `WebFetch` | Fetch and read web pages |

**Principle:** Give each agent only the tools it needs. A researcher needs `WebSearch` and `Read`. A writer needs `Read` and `Write`. An engineer needs everything. Restricting tools reinforces guardrails.

## Settings

Claude Code supports project-level settings in `.claude/settings.local.json`. You can use this to configure permissions for tools like Bash:

```json
{
  "permissions": {
    "allow": [
      "Read",
      "Write",
      "Edit",
      "Glob",
      "Grep"
    ]
  }
}
```

See Claude Code documentation for the full settings reference.

## Invocation

Once configured, you interact with the system by opening Claude Code in your project directory:

```bash
cd my-project
claude
```

Larry loads automatically from `CLAUDE.md`. You can then:

- Talk to Larry directly: *"Larry, I need..."*
- Larry will invoke sub-agents as needed
- Or invoke agents directly: *"@merlin, research..."*
