# Feynman Loop

> You explain it back; it finds the exact point your explanation breaks and asks a question aimed there.

**Category:** Learning
**Best for:** Any capable language model
**Difficulty:** Intermediate
**Output:** One probing question per round, until your explanation survives

## When to use it

You think you understand something — enough to use it, maybe enough to
talk about it — and you want to know if that's real. Reading it back to
yourself proves nothing; explaining it to a skeptic does.

This is the Feynman technique with the workload flipped: instead of you
guessing where you're fuzzy, the model finds the seam in your explanation
and pulls on it. Use it before interviews, exams, talks, or shipping an
opinion you'll have to defend.

## Variables to fill in

| Placeholder | What goes there |
|---|---|
| `[TOPIC]` | What you'll be explaining |
| `[MY EXPLANATION]` | Your explanation, written like you'd say it — don't polish it first |

## The prompt

````
I'm going to explain [TOPIC] to you. Your job is to test whether I
actually understand it.

My explanation:
[MY EXPLANATION]

Rules — this is a loop:
- Find the single weakest point in my explanation: a place I used a
  word without defining it, skipped a step, gave an analogy that
  doesn't map, or stated something true-but-hollow.
- Ask me ONE question that exposes that point. Not a trivia question —
  a question I can only answer if I actually understand the thing.
- Wait for my answer. Then find the next weak point and ask again.
- If my answer is right, say so in one line and move on — no lectures.
- If my answer is wrong or hand-wavy, don't correct me. Ask a smaller
  question aimed at the gap.
- After each round, keep a running note of what I've proven I
  understand vs what I haven't.
- When my explanation survives three rounds with nothing left to
  attack, say so, summarize the strongest version of my own argument
  back to me, and stop.
````

## Example

**Input:**

> Topic: why the sky is blue
> My explanation: "Sunlight has all the colors and air scatters the blue
> one more, so we see blue."

**Output (first question):**

> *"You said air scatters blue 'more' — more than what, and why blue
> rather than violet, which scatters even more?"*
>
> (You answer — maybe well, maybe revealing that "scatters more" was a
> phrase you memorized rather than understood. The next question aims at
> whichever it was.)

## Notes

- **Don't polish your explanation first.** The fuzzier your starting
  version, the better the questions. You're trying to locate your actual
  model, not your best performance of one.
- **"One question per round" is the mechanism.** A list of ten questions
  lets you answer the easy eight and skip the one that would have broken
  you.
- **The wrong-answer rule matters.** Being told you're wrong teaches the
  fact; being asked a smaller question teaches the structure. If it just
  corrects you, restate the rule.
- **Know when to stop the loop.** Past five or six rounds you're probing
  terminology, not understanding — the returns drop fast.

## Follow-up prompts

- "Give me the three-round version of this for a different topic: [TOPIC]."
- "Now ask me the questions a hostile expert would ask."
- "Based on what I proved, what should I read next?"

## Version

- Added: 2026-10-14
- Last updated: 2026-10-14
- Changes: initial version
