# Example: Journal Analyst

This is an anonymised example of a domain specialist built using Agent Orchestra. It demonstrates how to create an agent for personal data analysis.

---

## The need

A professional who keeps a daily journal (exported monthly as a PDF) wanted structured monthly reports that identified patterns, tracked people and activities, assessed wellbeing, and surfaced unresolved threads — without the time investment of doing the analysis manually.

## How it was built

**Merlin's research** identified that skilled personal analysts:
- Read for what lies beneath the surface, not just what is stated
- Maintain strict word economy — insight per word matters
- Address the subject directly ("you") rather than writing about them in third person
- Distinguish between reflecting and diagnosing — the former is helpful, the latter is overreach
- Identify patterns the subject may not notice themselves

**Nolan designed** an agent with:
- **Persona:** "A perceptive, psychologically literate reader who combines the attentiveness of a skilled life coach with the analytical discipline of a researcher. Calm, editorial, and direct. Never flatters, never pads, never cheerleads. Gives the user a clear mirror of their own month."
- **Output format:** Exactly seven sections, strict word limits per section, total report under 2,000 words.
- **Guardrails:** Does not invent information not present in the journal. Does not speculate about emotions not expressed. Does not offer unsolicited therapeutic advice. Does not pad sections to reach word count.

## Key design decisions

1. **Model tier:** Top tier — pattern recognition across long documents requires deep reasoning
2. **Strict output format:** Seven defined sections with word limits prevented the agent from producing unfocused summaries
3. **Tone constraint:** "Never flatters, never pads, never cheerleads" — this single instruction eliminated the sycophantic tendency common in AI output
4. **Privacy by design:** The agent reads journal exports but does not store, summarise, or transmit personal data beyond the report

## What made it effective

- The seven-section structure gave consistency across months, making it possible to compare reports over time
- The word limits forced density — every sentence had to carry information
- The "clear mirror" persona metaphor produced output that was useful rather than comfortable — the agent would note stress patterns and unresolved threads even when the journal entries themselves didn't explicitly flag them
