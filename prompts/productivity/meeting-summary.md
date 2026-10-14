# Meeting Summarizer

> Turns a messy transcript into decisions and action items.

**Category:** Productivity
**Best for:** Anything with a long context window — transcripts get big fast
**Difficulty:** Beginner
**Output:** Decisions made, action items with owners, open questions

## When to use it

You have a transcript or rough notes from a meeting and need the version
you'd actually send to people: who committed to what, what was decided,
and what got parked.

It works on raw transcripts (with or without speaker labels), voice-memo
dumps, or your own chaotic notes. It does not work on "give me the vibe of
this meeting" — it extracts, it doesn't interpret.

## Variables to fill in

| Placeholder | What goes there |
|---|---|
| `[MEETING TYPE]` | e.g. sprint planning, client check-in, interview debrief — it changes what counts as a decision |
| `[PASTE TRANSCRIPT]` | The raw transcript or notes. Speaker labels help but aren't required |

## The prompt

```
Summarize this [MEETING TYPE] transcript.

Rules:
- Decisions first. Only things the group actually agreed on — if it was
  floated and dropped, it goes under "Discussed, not decided."
- Action items as a list: owner, task, deadline if one was said. If no
  owner was named, write "owner: unassigned" — do not guess.
- Open questions: things raised but not resolved.
- Keep each line short enough to paste into a tracker. No filler like
  "the team discussed the importance of."
- If a section would be empty, write "None."
- If the transcript is truncated or garbled in places, flag the spots
  you're unsure about rather than smoothing them over.

Format:

## Decisions
## Action items
## Discussed, not decided
## Open questions
## Unclear in transcript

Transcript:
[PASTE TRANSCRIPT]
```

## Example

**Input:**

> Meeting type: weekly engineering sync
> Transcript: 40-minute recording export, auto-transcribed, no labels

**Output (trimmed):**

> **Decisions**
> - Ship the settings redesign behind a flag on Monday, not Thursday.
>
> **Action items**
> - owner: Priya — flip the flag config in staging before Friday
> - owner: unassigned — write the rollback doc
>
> **Open questions**
> - Whether the legacy dashboard stays reachable after the cutover.
>
> **Unclear in transcript**
> - A name near the 12-minute mark was garbled — the reviewer
>   assignment may be wrong.

## Notes

- The "unassigned" rule is the important one. Left alone, models
  confidently assign tasks to whoever spoke most.
- "Discussed, not decided" catches a real failure mode: transcripts are
  full of ideas that sound like commitments and weren't.
- Long meetings (90+ min) degrade. Split the transcript at agenda items
  and run it per section if the summary starts dropping items.
- It's extraction, not minutes. For a polished send-out, follow up with
  *"Rewrite this as a three-paragraph email to the team."*

## Follow-up prompts

- "Rewrite this as an email to the team. Keep the action items verbatim."
- "Which action items have no owner? Draft a message assigning them."
- "What should have been decided in this meeting but wasn't?"

## Version

- Added: 2026-10-14
- Last updated: 2026-10-14
- Changes: initial version
