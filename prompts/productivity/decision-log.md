# Decision Log

> Paste a rambling pros/cons brainstorm, get back a structured decision you can defend.

**Category:** Productivity
**Best for:** Any capable language model
**Difficulty:** Intermediate
**Output:** The real question, the options, regret analysis, and a recommendation with confidence

## When to use it

You've been going back and forth on a decision — in your head, in notes,
in a Slack message to yourself — and the thinking has stopped producing
anything new. The notes have everything; they just don't have a shape.

This forces the shape: what you're *actually* deciding (often not what
you started with), what the real options are, what you'd regret in each,
and a call with a stated confidence so you can revisit it later honestly.

## Variables to fill in

| Placeholder | What goes there |
|---|---|
| `[DEADLINE]` | When you must decide by — "no deadline" is fine, but say it |
| `[PASTE NOTES]` | The rambling — voice notes, bullet dumps, half-formed pros/cons, all of it |

## The prompt

````
Turn my notes into a decision.

Deadline: [DEADLINE]

Rules:
- First, state the actual decision in one sentence — what I'm really
  choosing between, which may not be the question I think I'm asking.
  If my notes contain two different decisions tangled together, say so
  and split them.
- List the real options. Only ones I could actually choose — delete
  options I already ruled out and straw men I'm not seriously
  considering.
- For each option: the best case, the worst case, and what I'd regret
  if I picked it. Regret is the useful column — pros/cons are usually
  already in my notes.
- Name what I'm missing: the information whose absence is actually
  blocking the decision, if anything. If the notes already contain
  everything needed, say "you have enough — decide."
- Give a recommendation with a confidence level (low/medium/high) and
  the one assumption it depends on most.
- Keep it under 300 words. A decision log I have to scroll is a
  decision avoided.

My notes:
[PASTE NOTES]
````

## Example

**Input:**

> Deadline: Friday
> Notes: "contract role vs full-time offer. contract pays more/mo.
> fte has equity + health insurance. contract could go perm later maybe?
> also manager at fte seems great but boring product. keep going back
> and forth. rent is due lol. dad says take stability"

**Output (trimmed):**

> *The actual decision: optimizing for income now vs compounding
> benefits + stability — the product-boredom worry is a separate
> decision (role fit) tangled into this one.*
>
> *Options: (1) Contract — best case: higher pay, converts perm; worst:
> ends in 6 months mid-market; regret: gave up equity + insurance for a
> maybe. (2) FTE — best case: stability, good manager, equity upside;
> worst: bored within a year; regret: took the "dad option" and
> stagnated.*
>
> *Missing info: whether "could go perm" is a real path or a courtesy —
> one question to the contract recruiter answers it. Recommendation:
> FTE, medium confidence — depends most on how much the contract's perm
> conversion is actually worth.*

## Notes

- **The "actual decision" line is the whole product.** Half of hard
  decisions are hard because they're two decisions pretending to be one.
- **The regret column beats pros/cons.** Pros/cons restate what you
  already listed; "what you'd regret" surfaces what you're afraid of —
  usually the real blocker.
- **"You have enough — decide" is a valid output.** If it says that and
  you still can't move, the blocker isn't information — it's the regret
  column. Read it again.
- **Don't give it a decision you've already made.** It will happily
  structure your rationalization; the output feels like clarity and
  isn't.

## Follow-up prompts

- "Stress-test the recommendation: argue for the losing option."
- "What would have to be true in 6 months for this to have been wrong?"
- "Turn this into a message to [person] explaining my choice."

## Version

- Added: 2026-10-14
- Last updated: 2026-10-14
- Changes: initial version
