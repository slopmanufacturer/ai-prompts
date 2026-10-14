# Email to Action Items

> Forward a long thread, get who needs what from whom by when — and which parts you can ignore.

**Category:** Productivity
**Best for:** Anything with a long context window — threads get big
**Difficulty:** Beginner
**Output:** Action items by owner, open questions, and an ignore list

## When to use it

You've been CC'd into a 40-message thread, or you come back from three
days offline to find a novel in your inbox. You don't want a summary —
you want to know if you owe anyone anything and what can be safely
unread.

The two features that make it better than "summarize this thread": items
are sorted by *who owes whom* (not chronology), and the ignore list names
the chunks you can skip guilt-free.

## Variables to fill in

| Placeholder | What goes there |
|---|---|
| `[ME]` | Your name/email as it appears in the thread — so "my" items are actually yours |
| `[PASTE THREAD]` | The full thread, oldest to newest if you can manage it |

## The prompt

````
Extract what matters from this email thread. I am [ME].

Rules:
- Action items first, grouped by owner: "I owe", "Others owe", plus
  each item's deadline if one was stated. No deadline stated = "no
  deadline" — do not invent one.
- An item only counts if someone actually committed or was directly
  asked. "It would be nice if" is not an action item.
- Open questions: asked but never answered in the thread.
- Resolved: questions that were answered — one line each, so I can
  skip re-reading for them.
- Ignore list: the sub-threads and messages I can safely not read
  (social side-chatter, resolved tangents, FYI-only messages).
- Flag anything addressed directly to me that isn't an action item —
  questions, decisions waiting on me.
- If the thread is out of order or truncated, say which parts you're
  working from.

Thread:
[PASTE THREAD]
````

## Example

**Input:**

> Me: Dana
> Thread: 31-message chain about the Q3 launch, marketing + eng + legal CC'd

**Output (trimmed):**

> **I owe**
> - Confirm the launch date with legal — asked of you by Marta, no
>   deadline stated.
>
> **Others owe**
> - Sam (eng): staging link for the landing page, promised Friday.
>
> **Open questions**
> - Whether the discount code works in the EU store — raised twice,
>   never answered.
>
> **Resolved**
> - The webinar moved to Oct 22 (decided in Marta's Tuesday reply).
>
> **Ignore**
> - Messages 18–26: catering debate for the launch party. Nothing
>   actionable.

## Notes

- **Fill in `[ME]` or it can't separate "I owe" from "others owe"** —
  the most important split in the output.
- **"No deadline stated" is deliberate.** Models love to infer "ASAP" or
  "by Friday" from tone; invented deadlines create real commitments.
- **The ignore list is the feature you'll miss most when it's gone.** A
  summary still makes you read everything; this tells you what to skip.
- **Forwards and attachments get weird.** If the thread contains quoted
  nesting from forwards, expect some owner confusion — check the "I owe"
  list against the thread before acting on it.

## Follow-up prompts

- "Draft my reply covering the 'I owe' items and the open questions."
- "Which items in 'others owe' should I actually chase, and which are
  someone else's problem?"
- "Rewrite this as a 3-line Slack status update for my team."

## Version

- Added: 2026-10-14
- Last updated: 2026-10-14
- Changes: initial version
