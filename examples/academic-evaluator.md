# Example: Academic Evaluator

This is an anonymised example of a domain specialist built using Agent Orchestra. It demonstrates how to create an agent for expert assessment work.

---

## The need

A university researcher serving on appointment committees needed to evaluate multiple candidates for academic positions. Each evaluation required reading a full dossier (CV, publications, research statement, teaching portfolio), applying institutional criteria, and producing a structured report.

## How it was built

**User:** "Atlas, I need someone who can evaluate academic hiring applications."

**Merlin's research** identified that expert academic evaluators:
- Calibrate expectations to career stage (junior vs senior appointments)
- Evaluate artistic/practice-based research on its own terms, not through traditional scholarly lenses
- Produce reports in formal institutional register
- Flag ambiguities rather than forcing false verdicts
- Distinguish between "meets criteria" and "excels"

**Nolan designed** an agent with:
- **Persona:** "A seasoned academic with 25+ years on appointment committees — precise, fair, and written in the authoritative register of institutional review. Never editorialises; assesses."
- **Guardrails:** Does not fabricate credentials. Does not make hiring decisions (produces assessments; the decision belongs to the institution). Does not apply inappropriate standards.

## Key design decisions

1. **Model tier:** Top tier — evaluation requires nuanced judgement
2. **Tools:** Read-only — the evaluator reads materials but does not write to external systems
3. **Output format:** Structured report matching institutional conventions
4. **Guardrail philosophy:** The agent assesses, it does not decide. The distinction matters.

## What made it effective

- The persona of "25+ years on panels" consistently produced output with appropriate calibration — neither too harsh on junior candidates nor too lenient on senior ones
- The explicit guardrail against fabricating credentials prevented hallucination of publication records
- The structured output format meant reports could be submitted directly to committees without reformatting
