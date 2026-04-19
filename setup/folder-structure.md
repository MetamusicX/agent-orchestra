# Folder Structure

Agent Orchestra uses a simple folder structure to manage workflow. No databases, no project management tools — just folders and files.

## The layout

```
your-project/
├── Owner's Inbox/           # Your requests and input files
├── Team Inbox/              # Agent output for your review
├── Completed Work/          # Finished deliverables
│   ├── [Task Name 1]/
│   ├── [Task Name 2]/
│   └── ...
├── Team/                    # Agent profiles
│   ├── ROSTER.md
│   ├── Merlin.md
│   ├── NOLAN.md
│   ├── Kai.md
│   └── [Your agents].md
├── CLAUDE.md                # Atlas (orchestrator system prompt)
└── .claude/agents/          # Agent definition files
    ├── merlin.md
    ├── nolan.md
    ├── kai.md
    └── [your-agents].md
```

## How each folder works

### Owner's Inbox

This is where you place files, documents, or notes for the team to work on. Think of it as your desk — you drop things here when you want something done.

**Rules:**
- Only you and Atlas can see this folder
- Placing a file here does NOT automatically trigger work — you must explicitly ask Atlas
- Once Atlas has routed the work, the source material stays here until the task is complete

### Team Inbox

This is where agents deliver their output for your review. When an agent completes a task, the deliverable lands here.

**Rules:**
- You review everything in Team Inbox before it moves to Completed Work
- If you want revisions, tell Atlas — he'll route the feedback to the right agent
- Nothing leaves Team Inbox without your approval

### Completed Work

Finished deliverables. Each completed task gets its own subfolder with a clear name.

**Rules:**
- Atlas moves output here only when you've approved it
- Subfolder names should be descriptive: `Grant Proposal Review - April 2026/`, not `task-47/`
- This is the archive — once something is here, it's done

### Team

Agent profiles and the roster. This is Atlas's reference when deciding who handles what.

**Rules:**
- Nolan maintains this folder
- Every active agent has a profile here
- `ROSTER.md` is the single source of truth for team composition
- When a new agent is hired, Nolan places the profile here and updates the roster

## Why folders, not a database?

- **Transparency:** You can see everything by browsing your file system
- **Portability:** Works on any platform, any operating system
- **Simplicity:** No schema to maintain, no queries to write
- **Version control:** Works naturally with git if you want history

The folder structure is a suggestion, not a requirement. If your workflow needs different folders, adapt it. The key principle is: separate input (Owner's Inbox), output for review (Team Inbox), finished work (Completed Work), and team definitions (Team).
