# Example: Task — Monthly Journal Report

An anonymised example of a task file, showing how Atlas delegates recurring analytical work.

---

```yaml
---
id: TASK-2026-012
title: "Produce monthly journal report for April 2026"
status: in-progress
assignee: "journal-analyst"
created: 2026-05-01
updated: 2026-05-02
sop: "SOP-001"
source: "user request"
---
```

# TASK-2026-012: Produce monthly journal report for April 2026

## Description
Analyse the April 2026 journal export and produce a structured monthly report following SOP-001. The report should cover patterns, people, wellbeing indicators, and unresolved threads.

## Input
- Journal export: `Source Materials/journals/2026-04-journal.pdf`
- Previous report for reference: `Deliverables/journal-reports/2026-03-report.md`

## Expected Output
- Structured report saved to `Deliverables/journal-reports/2026-04-report.md`
- Seven sections, total under 2,000 words
- Format must match the template defined in SOP-001

## Notes
- March report flagged two open threads (a stalled collaboration and a recurring scheduling conflict). Check whether April resolves either.
- The user noted that late April included travel — expect a shift in daily rhythm patterns.

## Log
- 2026-05-01: Created. Source: user request via session.
- 2026-05-01: Status changed to `in-progress`. Atlas delegated to journal-analyst with SOP-001 reference.
- 2026-05-02: Journal-analyst completed first read-through. Draft in progress. Updated timestamp.
