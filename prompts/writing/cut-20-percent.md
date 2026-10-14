# Cut 20%

> Paste a draft, get it back shorter — deleted words, not rewritten ones.

**Category:** Writing / Editing
**Best for:** Any capable language model
**Difficulty:** Beginner
**Output:** The same piece ~20% shorter, plus a list of what was cut and why

## When to use it

Your draft is good but long. You don't want it "improved" — you want it
shorter without losing your voice or your points. The constraint is that
it *deletes*, never rewrites: every sentence that survives is one you
actually wrote.

Use it on emails, docs, blog posts, PR descriptions — anything where
nobody will read the long version. Don't use it when the piece is already
tight; cutting 20% of a lean draft removes muscle, not fat.

## Variables to fill in

| Placeholder | What goes there |
|---|---|
| `[PERCENT]` | How much to cut. 20 is the default; 10 is gentle, 40 is surgery |
| `[WHAT CAN'T BE CUT]` | e.g. "the pricing table," "the second anecdote" — your protected lines |
| `[PASTE DRAFT]` | The full text |

## The prompt

````
Cut this draft by [PERCENT]%.

Cannot be cut: [WHAT CAN'T BE CUT]

Rules:
- DELETE only. Do not rewrite, reword, merge, or "tighten" sentences.
  Every surviving sentence must be one I wrote, verbatim.
- Cut in this order: throat-clearing openings, hedges ("I think,"
  "it's worth noting"), duplicated points, examples after the second
  one, adjectives doing no work, conclusions that restate.
- If two sentences make the same point, keep the better one — cut the
  other entirely.
- Never cut the one sentence that carries the argument.
- After the cut text, list what you removed and why — one line each,
  grouped by the categories above.
- If you can't reach [PERCENT]% without cutting muscle, cut less and
  say so. A bad cut is worse than a short one.

Draft:
[PASTE DRAFT]
````

## Example

**Input:**

> Percent: 20
> Can't be cut: the refund policy details
> Draft (excerpt):
>
> *"I wanted to reach out regarding your recent order. It's worth noting
> that we've looked into this carefully. We investigated the issue you
> reported. Our team found that the package was marked delivered but the
> photo shows the wrong doorstep. We think it went to 14B instead of 14D.
> The refund policy is as follows: [...details...]. We're really sorry
> about this whole situation and we take it seriously. Again, we
> apologize for the inconvenience."*

**Output:**

> The cut version keeps: *"We investigated the issue you reported. Our
> team found that the package was marked delivered but the photo shows
> the wrong doorstep — it went to 14B instead of 14D. The refund policy
> is as follows: [...]. We're sorry about this and we're fixing it."*
>
> Cut list: "I wanted to reach out" (throat-clearing), "It's worth
> noting that we've looked into this carefully" (hedge announcing the
> next sentence), "We think it went" → merged into the doorstep finding,
> double apology collapsed to one.

## Notes

- **"Delete only, verbatim survivors" is what protects your voice.** The
  moment rewriting is allowed, the output sounds like the model, not you.
- **The cut list is half the value.** It teaches you what your padding
  looks like — after a few runs you'll write less of it.
- **Fill in "can't be cut" or it will cut the wrong thing.** Models
  reliably delete the specific detail and keep the vague summary — the
  opposite of good editing.
- **Watch for meaning drift on big cuts.** At 40%+, "delete only" gets
  hard to satisfy and the model will quietly start merging sentences —
  check the survivors are actually verbatim.

## Follow-up prompts

- "Show the cut version with strikethroughs on what you removed."
- "Cut another 10% — what's the next thing to go?"
- "Which cut was the hardest call and why?"

## Version

- Added: 2026-10-14
- Last updated: 2026-10-14
- Changes: initial version
