# Example: Scholarly Writer

This is an anonymised example of a domain specialist built using Agent Orchestra. It demonstrates how to create an agent for sustained academic writing.

---

## The need

A researcher needed to write a scholarly monograph drawing on multiple primary sources (PDF documents, structured notes, analytical essays). The writing needed to maintain a consistent academic voice across chapters, cross-reference sources accurately, and produce dense, analytical prose — not summaries.

## How it was built

**Merlin's research** identified that excellent scholarly writers:
- Expand and deepen rather than summarise and condense
- Maintain a consistent voice across hundreds of pages
- Cross-reference sources meticulously, preserving citation chains
- Distinguish between their own analytical claims and source material
- Write in a specific register — neither journalistic nor flatly academic

**Nolan designed** an agent with:
- **Persona:** "A scholar-writer operating at the intersection of [field] and critical theory. Writes dense, erudite, analytically precise prose. Does not summarise; expands and deepens."
- **Key method:** Numbered markdown files define the book's architecture. The agent reads them in sequence as the compositional skeleton, then cross-references PDF sources for verification and enrichment.
- **Guardrails:** Does not invent facts or claims not traceable to provided sources. Does not condense. Does not change the structural sequence without authorisation.

## Key design decisions

1. **Model tier:** Top tier — scholarly writing requires the highest reasoning capability
2. **Source hierarchy:** Markdown files define structure; PDFs provide verification and expansion material. The agent knows which is which.
3. **Style template:** The agent was given examples of the user's own published prose as a style reference — not to imitate, but to match register and density.
4. **Language constraint:** British English only (matching the user's publishing conventions).

## What made it effective

- The instruction "does not summarise; expands and deepens" was the single most important design decision. Without it, the agent consistently compressed material. With it, the agent produced genuinely analytical prose.
- The source hierarchy prevented the agent from treating all inputs equally — structured notes drove the architecture, while PDFs enriched the content.
- The persona of "scholar-writer" (not "assistant") produced output that read as authored, not generated.
