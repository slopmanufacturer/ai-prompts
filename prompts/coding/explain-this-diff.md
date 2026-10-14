# Explain This Diff

> Paste a git diff, get a plain-English walkthrough of what changed and what could break.

**Category:** Coding
**Best for:** Any capable language model — bigger diffs need bigger context windows
**Difficulty:** Beginner
**Output:** Walkthrough of intent, plus a "what could break" list

## When to use it

You're reading a diff you didn't write — a teammate's PR, a dependency
bump, your own commit from three months ago — and you want the story, not
line-by-line narration.

It separates "what changed" (usually obvious from the diff) from "why it
matters and what it touches" (the part you actually need). Works on any
`git diff`, `git show`, or PR patch. Don't paste a whole release — one
commit or one PR at a time.

## Variables to fill in

| Placeholder | What goes there |
|---|---|
| `[CONTEXT]` | One line: what this code is for, or "no context" — honesty beats guessing |
| `[PASTE DIFF]` | The raw diff output, hunks and all |

## The prompt

````
Explain this diff to me.

Context: [CONTEXT]

Rules:
- Start with one sentence: what this change is trying to do.
- Then walk through the diff grouped by PURPOSE, not by file order.
  "Renames X everywhere" is one item even across six files.
- Flag anything the diff changes but doesn't explain: a renamed variable
  whose callers might not know, a default that flipped, a deleted
  code path that something else could still call.
- End with "What could break:" — a short list of concrete risks,
  each with the line that causes it. "Looks safe" is a valid answer.
- If a hunk is truncated or depends on code I didn't paste, say so
  instead of guessing.

Diff:
[PASTE DIFF]
````

## Example

**Input:**

> Context: express API for a booking app
> Diff (excerpt):
>
> ```
> -  const nights = Math.round((checkout - checkin) / 86400000);
> +  const nights = Math.ceil((checkout - checkin) / 86400000);
> ```
> plus a test file renaming `sameDayReturnsZero` to `sameDayReturnsOne`.

**Output:**

> *What it's trying to do: count a same-day stay as one night instead of
> zero.*
>
> *By purpose: (1) the calculation switched `round` to `ceil` — any stay
> under half a day now bills a full night; (2) the test was renamed to
> match the new expectation.*
>
> *What could break: stays of 0 nights were previously free — if
> `nights === 0` was a guard elsewhere (e.g. a minimum-stay check or a
> divide-by-nights), that path is now unreachable. Check anything that
> special-cased zero.*

## Notes

- **Grouped-by-purpose is what separates this from reading the diff
  yourself.** A rename across 8 files is one fact, not eight.
- **Give it context when you have it.** "No context" is acceptable — the
  prompt forbids guessing — but one line of context roughly halves the
  "can't tell" flags.
- **The "what could break" list is where it earns its place.** That's the
  part reviewers actually need and diffs never show.
- **Huge diffs dilute it.** Past a few hundred lines the walkthrough
  flattens to file-level summary — split by commit or by directory.

## Follow-up prompts

- "Which of these risks should I actually write a test for?"
- "Draft the PR description for this diff."
- "What did the author probably intend vs what the code actually does?"

## Version

- Added: 2026-10-14
- Last updated: 2026-10-14
- Changes: initial version
