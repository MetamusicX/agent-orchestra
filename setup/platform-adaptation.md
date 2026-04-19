# Platform Adaptation Guide

Agent Orchestra is designed for Claude Code but the architecture is platform-agnostic. This guide explains how to adapt it to other LLM agent platforms.

## What stays the same across platforms

- The orchestrator pattern (Larry routes, never executes)
- Agent profiles (persona, responsibilities, guardrails)
- The hiring pipeline (PAX → Nolan)
- The folder structure (Owner's Inbox, Team Inbox, Completed Work, Team)
- The guardrail philosophy
- The collaboration model

## What changes across platforms

| Concept | What to adapt |
|---------|---------------|
| System prompt | Where and how the orchestrator prompt is loaded |
| Agent definitions | How sub-agents are configured and invoked |
| Model selection | Available models and their identifiers |
| Tool access | How agents access files, web, terminal |
| Agent invocation | How the orchestrator calls a sub-agent |

## Adaptation by platform

### OpenAI Codex

- **Orchestrator:** Use the system prompt or `AGENTS.md` file
- **Agent definitions:** Custom instructions or function definitions
- **Model tiers:** GPT-4o (top), GPT-4o-mini (mid), smaller models (light)
- **Key difference:** Function calling replaces Claude Code's agent tool

### Google Gemini

- **Orchestrator:** System instructions
- **Agent definitions:** Agent configuration files
- **Model tiers:** Gemini Pro (top), Gemini Flash (mid)
- **Key difference:** Tool use API differs from Claude Code's model

### Cursor Agent

- **Orchestrator:** `.cursorrules` or system prompt
- **Agent definitions:** Rules files or custom instructions
- **Key difference:** Tightly integrated with IDE; folder structure may need adaptation for editor-centric workflow

### Generic / API-based

If your platform supports:
1. A system prompt → use it for Larry
2. Multiple conversations or agents → use them for sub-agents
3. File access → the folder structure works as-is

If your platform does NOT support sub-agents natively, you can still use the pattern by:
- Keeping all agent profiles in a `Team/` folder
- Instructing the orchestrator (via system prompt) to read the relevant agent profile and adopt that persona when delegating
- This is less clean than native sub-agents but still effective

## Contributing platform guides

If you adapt Agent Orchestra to a new platform, consider contributing a detailed guide. Include:

1. How to set up the orchestrator
2. How to define and invoke sub-agents
3. Any platform-specific limitations or workarounds
4. Model tier mapping for that platform
