# Rubber Duck Debugger

> Paste your bug and what you've tried — it asks pointed questions one at a time instead of dumping fixes.

**Category:** Coding
**Best for:** Any capable language model
**Difficulty:** Beginner
**Output:** One question at a time, leading you to the bug yourself

## When to use it

You've been staring at a bug long enough that your eyes slide off it. You
don't want a fix handed to you — you want to *find* it, because you'll
actually learn something and the fix will stick.

This is the rubber-duck method with a duck that talks back. Use it when the
bug is somewhere in your understanding, not just in the code. Skip it when
you're on a deadline and just want the answer — use the code review prompt
for that.

## Variables to fill in

| Placeholder | What goes there |
|---|---|
| `[WHAT SHOULD HAPPEN]` | Expected behavior, in one sentence |
| `[WHAT ACTUALLY HAPPENS]` | Actual behavior — error text, wrong output, hang |
| `[WHAT I'VE TRIED]` | What you already ruled out — this stops the duck re-asking |
| `[PASTE CODE]` | The smallest code that still shows the bug |

## The prompt

````
You are a rubber duck that asks good questions. I'm debugging something
and I want to find the answer myself — your job is to guide me there.

The bug:
- Should happen: [WHAT SHOULD HAPPEN]
- Actually happens: [WHAT ACTUALLY HAPPENS]
- Already tried: [WHAT I'VE TRIED]

Code:
[PASTE CODE]

Rules:
- Ask me exactly ONE question per message. Wait for my answer.
- Ask the question that eliminates the most possibilities, not the
  easiest one.
- Start with assumptions, not code. "Are you sure X is what you think it
  is?" beats "try changing line 5."
- If my answer reveals the bug, don't celebrate — ask the question that
  makes ME say the bug out loud.
- Only if I'm genuinely stuck after three questions, give me a hint —
  a place to look, not the fix.
- When I find it, respond with one sentence naming what the real bug
  was, then stop.
````

## Example

**Input:**

> Should: function returns total with tax
> Actually: returns NaN
> Tried: checked the tax rate, it's 0.08
> Code: `const total = price + price * taxRate` where `price` comes from
> an input field

**Output (first question):**

> *"What is the type of `price` when it reaches that line?"*
>
> (You answer: "a string from the input." Next question: *"What does
> `'25' + '25' * 0.08` evaluate to, and why?"* — and now you've found
> it yourself: `price * taxRate` coerces fine, but `price +` concatenates.)

## Notes

- **The one-question rule is the whole thing.** Without it the model
  dumps a checklist and you're back to guessing which guess is right.
- **"Already tried" earns its keep.** Every thing you list is a question
  the duck won't waste a round on.
- **Paste less code than feels right.** A 20-line repro gets sharp
  questions; a 400-line file gets "have you tried logging?" Generic input
  gets generic questions.
- **It will occasionally guess the bug early and steer you toward a wrong
  answer.** If question three feels off-base, say so — the prompt lets it
  re-plan.

## Follow-up prompts

- "That wasn't it — ask me something else."
- "I found it. Now explain why my mental model was wrong."
- "What test would have caught this at write time?"

## Version

- Added: 2026-10-14
- Last updated: 2026-10-14
- Changes: initial version
