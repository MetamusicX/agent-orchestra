# Example: SOP — Meeting Transcript Extraction

An anonymised example of a Standard Operating Procedure, showing how a repeatable analytical process is formalised.

---

```yaml
---
id: SOP-003
title: "Meeting transcript extraction"
owner: "meeting-analyst"
frequency: on-demand
inputs: [transcript file (.txt or .pdf)]
outputs: [structured extraction (.md)]
output-location: "Deliverables/meeting-extractions/"
last-executed: 2026-04-18
version: 2
---
```

# SOP-003: Meeting Transcript Extraction

## Purpose
Extract structured, searchable content from raw meeting transcripts so that ideas, references, and open threads are preserved and findable.

## Trigger
User provides a file path to a meeting transcript and requests extraction. Atlas delegates to meeting-analyst with this SOP reference.

## Prerequisites
- Transcript file exists at the provided path and is readable.
- The meeting-analyst agent is available and has read access to the source folder.

## Steps
1. Receive the transcript file path from Atlas.
2. Read the full transcript. Note the date, approximate duration, and participants (if identifiable from context).
3. Extract the following sections:
   - **Key topics**: The 3-7 substantive subjects discussed. One line each.
   - **Ideas and proposals**: Any new ideas, suggestions, or proposals raised. Attribute where possible.
   - **References**: Books, papers, people, or projects mentioned. Include enough context to be searchable.
   - **Decisions**: Anything explicitly agreed or decided.
   - **Open threads**: Questions left unanswered, items deferred, follow-ups mentioned.
4. Save the extraction to `Deliverables/meeting-extractions/YYYY-MM-DD-meeting.md` using the meeting date.
5. If any open threads relate to existing tasks, note the TASK-NNN reference in the extraction.

## Output specification
- Markdown file with YAML frontmatter (date, source-file, participants).
- Five sections as listed above. No section should exceed 200 words.
- Filename: `YYYY-MM-DD-meeting.md` based on the meeting date, not the extraction date.

## Completion criteria
- Extraction file exists at the correct path.
- All five sections are present and populated (or explicitly marked "None").
- No fabricated content — everything traces to the transcript.

## Known issues
- Transcripts before September 2025 use a different speaker-label format (initials instead of full names). Check the format before assuming participant identity. (Source: journal entry 2025-11-03)
- Some transcripts include pre-meeting small talk. Exclude from extraction unless substantive topics emerge.
