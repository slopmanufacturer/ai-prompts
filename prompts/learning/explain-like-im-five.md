# Explain Like I'm Five

> Breaks down a hard concept without dumbing it down.

**Category:** Learning
**Best for:** Any capable language model
**Difficulty:** Beginner
**Output:** A plain-language explanation, then a one-step-deeper version

## When to use it

You hit a concept you half-understand — enough to nod along, not enough to
explain to someone else. This gets you a real explanation instead of a
Wikipedia summary.

The "without dumbing it down" part is the point. Straight ELI5 prompts tend to
produce condescending answers with toy analogies that don't survive contact
with the real thing. This version asks for the accurate picture in simple
words, then offers the next layer when you're ready.

## Variables to fill in

| Placeholder | What goes there |
|---|---|
| `[CONCEPT]` | The thing you want explained — be specific. "How TLS handshake works" beats "networking" |
| `[WHAT I ALREADY KNOW]` | Your actual background, honestly stated. "I write Python but never touched crypto" helps more than a job title |

## The prompt

```
Explain [CONCEPT] to me.

What I already know: [WHAT I ALREADY KNOW]

Rules:
- Use plain words. If you need a technical term, define it the first
  time you use it.
- Give me the accurate version, not the version that's simple but wrong.
  If a common analogy misleads, say so and drop it.
- One concrete example. Real, not "imagine a factory."
- Keep it under 300 words.
- End with one question I can ask myself to check whether I understood.

Then, below a line that says "One level deeper:", give me the version
you'd tell a junior colleague — the mechanism, not just the metaphor.
```

## Example

**Input:**

> Concept: Why airplane wings generate lift
> Background: I know basic physics, no fluid dynamics

**Output (trimmed):**

> *The wing pushes air down. That's the whole trick — air goes down, the
> plane goes up, Newton's third law. The curved-top shape matters mainly
> because it steers a lot of air downward efficiently, not because air
> "has to travel farther" on top. That classic explanation is wrong: air
> parcels that split at the front of the wing do not rejoin at the back.*
>
> *Concrete check: a plane can fly upside down. If lift depended on the
> curved-top shape, that would be impossible.*
>
> *Ask yourself: can I explain why tilting a flat board in moving air
> produces lift?*
>
> *One level deeper: the wing's angle of attack deflects the airstream;
> circulation around the wing sets up a pressure difference, but the
> pressure story and the "pushing air down" story are the same physics
> viewed two ways — not competing theories.*

## Notes

- The "one level deeper" split is doing the real work. Most ELI5 answers
  stall at the metaphor; forcing a second pass gets you the mechanism.
- Fill in `[WHAT I ALREADY KNOW]` honestly. "Know nothing" is a fine answer —
  it stops the model from assuming vocabulary you don't have.
- If the analogy still misleads, reply: *"Where does that analogy break?"*
  Most models will correctly name the limits of the analogy they just gave.
- Fails on concepts that are mostly notation (category theory, tensor
  calculus). Simple words can't carry those — ask for a study plan instead.

## Follow-up prompts

- "Where does that analogy break?"
- "Give me three questions to test if I actually got it."
- "What's the most common misconception about this?"

## Version

- Added: 2026-10-14
- Last updated: 2026-10-14
- Changes: initial version
