# Example: Domain Specialist

This is an anonymised example of a domain specialist built using Agent Orchestra. It demonstrates how to create an agent with deep expertise in a single subject area.

---

## The need

A practitioner needed an agent with comprehensive knowledge of a specific historical figure's complete body of work — not just biographical facts, but the underlying systems, methods, and philosophical frameworks that drove the work. The agent needed to both analyse existing works and generate new work using the same methods.

## How it was built

**Merlin's research** identified that deep domain specialists:
- Work from the inside of their subject's thinking, not from external descriptions
- Distinguish between surface imitation and structural understanding
- Can articulate every decision using the subject's own terminology
- Know the complete catalogue and can trace relationships across works
- Recognise the limits of their knowledge and state when evidence is lacking

**Nolan designed** an agent with:
- **Persona:** "Both a deep specialist in and an active practitioner drawing on the complete language, techniques, and oeuvre of [subject]. Scholarly and precise, speaks with the authority of someone who has internalised a complete catalogue and its underlying systems."
- **Source documents:** Glossaries of the subject's terminology, analytical texts, the subject's own writings, and a primary scholarly reference designated as the authoritative text.
- **Dual function:** Both analysis (explaining existing works) and generation (creating new work using the subject's methods).
- **Guardrails:** Works strictly within the subject's documented logic. Does not invent systems or import foreign techniques. Does not speculate beyond documented evidence. Defers to the user as the primary authority.

## Key design decisions

1. **Model tier:** Top tier — deep domain expertise requires maximum reasoning capability
2. **Glossaries as operational vocabulary:** The agent was given structured glossaries of the subject's terminology, organised both alphabetically and by domain. These served as the agent's working vocabulary for all decisions.
3. **Source hierarchy:** The user's own published scholarship was designated as the primary authority. The agent could draw on other sources but could not contradict the user's analysis without documentary evidence.
4. **Generation guardrails:** The agent could generate new work using the subject's methods, but every creative decision had to be articulable in the subject's own terms. No "inspiration from" — only "application of".

## What made it effective

- The glossaries transformed a general-purpose model into a genuine specialist. Instead of using approximate language, the agent used precise terminology consistently.
- The dual analysis/generation function made the agent useful for both understanding and creating — it could explain a technique AND then apply it.
- The guardrail "does not speculate beyond documented evidence" prevented the agent from filling gaps with plausible-sounding but unsupported claims — a critical requirement for scholarly work.
- Designating the user's own scholarship as the primary authority created a productive dynamic: the agent was deeply knowledgeable but fundamentally deferential to the user's expertise.
