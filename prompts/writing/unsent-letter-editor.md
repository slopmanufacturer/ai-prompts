# Unsent Letter Editor

> Paste the heated version, get back the one that costs you nothing.

**Category:** Writing / Editing
**Best for:** Any capable language model
**Difficulty:** Beginner
**Output:** A rewrite that keeps your point and drops the price of sending it

## When to use it

You wrote the email/Slack message angry and it shows. You still need to
say the thing — you just can't send *that*. This keeps your actual
complaint, request, or boundary intact while stripping the parts you'd
pay for later.

It is not a tone-polishing pass. It assumes your point deserves to
survive and your heat doesn't. Don't use it when you're wrong on the
facts — no edit fixes that.

## Variables to fill in

| Placeholder | What goes there |
|---|---|
| `[RELATIONSHIP]` | Who gets it and the stakes: "my manager," "a client I can't lose," "a stranger who was rude first" |
| `[PASTE MESSAGE]` | The draft you're afraid to send |

## The prompt

````
Rewrite this message so I can send it.

Recipient and stakes: [RELATIONSHIP]

Rules:
- Keep every factual claim and every concrete ask. Those are the
  message; the heat is not.
- Remove: accusations of motive ("you clearly don't care"),
  scorekeeping ("this is the third time"), sarcasm, ALL CAPS, and
  anything written to make me feel better rather than them act.
- Replace "you did X" framing with "X happened" or "I need Y" — same
  facts, no finger.
- Keep it shorter than the original. Angry drafts are always too long.
- Do NOT add apologies I didn't write. If I wasn't sorry, the rewrite
  isn't either.
- End by listing what you cut and what kept it professional: one line
  each, so I can check you kept my point.

Draft:
[PASTE MESSAGE]
````

## Example

**Input:**

> Relationship: my manager, who I like, but this is the third blown deadline
> Draft:
>
> *"I need to flag AGAIN that the data export was supposed to land
> Monday and it's now Thursday and once again I'm the one explaining to
> the client why YOUR team's pipeline didn't run. This is the THIRD time
> this quarter. I genuinely don't understand how this keeps happening
> unless nobody is watching the job at all."*

**Output (trimmed):**

> *"The data export that was due Monday hasn't landed — it's Thursday.
> This is the third missed deadline this quarter, and each time I'm the
> one explaining it to the client. What needs to change so the pipeline
> either runs on schedule or fails loudly enough that we catch it before
> they do?"*
>
> Cut: "AGAIN," "YOUR team," "I genuinely don't understand... unless
> nobody is watching" (motive accusation). Kept: the fact, the pattern
> (third time — that's data, not scorekeeping when it names the count),
> the ask — now pointed at a fix instead of blame.

## Notes

- **"Keep the facts, cut the heat" works because anger is usually
  formatting.** The substance ("third time this quarter") is almost
  always sendable; the delivery isn't.
- **"Third time" survives — and should.** A count is a fact; "AGAIN" is
  a jab. Good outputs keep the count and drop the caps.
- **Check the apology line.** Left alone, models add "I'm sorry for my
  tone" or soften asks you meant to keep hard. The no-added-apologies
  rule exists for that.
- **Still don't send it in the first five minutes.** Use the output as
  tomorrow's draft, not tonight's reply — the prompt fixes the text, not
  the timing.

## Follow-up prompts

- "Make it firmer — I still need them to feel the stakes."
- "Now the version where I'm asking for a specific commitment."
- "What will they most likely push back on?"

## Version

- Added: 2026-10-14
- Last updated: 2026-10-14
- Changes: initial version
