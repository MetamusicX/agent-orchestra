# Example: Workstream — Chapter Production

An anonymised example of a multi-agent workstream, showing how Atlas coordinates sequential handoffs between specialists.

---

```yaml
---
id: WS-002
title: "Book chapter production"
coordinator: atlas
agents: [domain-specialist, scholarly-writer]
frequency: per-chapter
status: active
version: 1
---
```

# WS-002: Book Chapter Production

## Purpose
Produce a complete book chapter by combining domain research with scholarly writing, coordinated through Atlas.

## Agents and roles

| Step | Agent | What they do | Input from | Output to |
|------|-------|-------------|------------|-----------|
| 1 | domain-specialist | Prepares source brief: reviews relevant PDFs, identifies key passages, organises material according to the chapter outline | User-provided chapter outline + source PDFs | `Working/chapter-briefs/ch-NN-brief.md` |
| 2 | scholarly-writer | Drafts the chapter using the source brief, cross-referencing original PDFs for verification and expansion | Step 1 output + source PDFs | `Deliverables/chapters/ch-NN-draft.md` |

## Trigger
User requests production of a specific chapter and provides or confirms the chapter outline and relevant source materials.

## Handoff protocol
1. Atlas creates a task for Step 1, delegating to domain-specialist with the chapter number, outline path, and source file paths.
2. When domain-specialist completes the source brief, Atlas verifies the file exists and contains the expected sections (key passages, thematic groupings, suggested structure notes).
3. Atlas then creates a task for Step 2, delegating to scholarly-writer with the source brief path and original PDF paths.
4. When scholarly-writer completes the draft, Atlas verifies word count is within expected range and all sections from the outline are present.
5. Atlas notifies the user that the draft is ready for review.

## Completion criteria
- Source brief exists at the expected path and covers all outline sections.
- Chapter draft exists at the expected path.
- Draft cross-references sources — no unsupported claims.
- User has been notified and can review.

## Related SOPs
- Domain-specialist follows their standard source-review procedure (no separate SOP yet — candidate for formalisation if the pattern stabilises).
- Scholarly-writer follows established writing conventions defined in their agent profile.
