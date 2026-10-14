# Regex Explainer + Builder

> Describe what to match in plain words with examples — get the regex, the breakdown, and what it won't match.

**Category:** Coding
**Best for:** Any capable language model
**Difficulty:** Beginner
**Output:** The regex, a capture-group walkthrough, and a non-matches list

## When to use it

You need a regex you can actually defend in review — not one you copied
from a forum and hope works. The examples do the constraining: three
strings it must match and two it must not teach the model more than three
paragraphs of description.

Two modes in one prompt: describe what you want and get a regex, or paste
a regex and get it explained. Both end with the "won't match" list, which
is the part everyone forgets to check.

## Variables to fill in

| Placeholder | What goes there |
|---|---|
| `[WHAT TO MATCH]` | Plain-English description, or "explain this regex:" + the pattern |
| `[SHOULD MATCH]` | 2–4 real example strings that must match |
| `[SHOULD NOT MATCH]` | 1–3 near-miss strings that must not |
| `[FLAVOR]` | Python `re`, JavaScript, PCRE, `grep -E` — syntax differs, so say which |

## The prompt

````
Work on this regex task.

Flavor: [FLAVOR]
Goal: [WHAT TO MATCH]

Must match:
[SHOULD MATCH]

Must not match:
[SHOULD NOT MATCH]

Rules:
- Give the simplest pattern that satisfies the examples — not the most
  general one.
- Then a walkthrough: each token or group, one line, plain words.
- Then "Won't match:" — the realistic inputs your pattern rejects that
  I didn't list. This is where the surprises live.
- Flag every assumption baked into the pattern (anchored? case?
  unicode? greedy?) in one line each.
- If my "must" and "must not" examples conflict, say so and ask —
  don't silently pick one.
- If explaining an existing regex: same walkthrough, plus anything the
  pattern matches that the author probably didn't intend.
````

## Example

**Input:**

> Flavor: JavaScript
> Goal: extract the version number from strings like `app-1.2.3.tar.gz`
> Must match: `app-1.2.3.tar.gz`, `tool-0.10.0.tar.gz`, `x-2.0.tar.gz`
> Must not match: `app-beta.tar.gz`, `1.2.3.tar.gz` (no name prefix)

**Output (trimmed):**

> Pattern: `/^[a-z]+-(\d+\.\d+\.\d+)\.tar\.gz$/`
>
> - `^` — anchored to string start
> - `[a-z]+-` — the name prefix, lowercase letters only, then a dash
> - `(\d+\.\d+\.\d+)` — capture group 1: three dot-separated numbers
> - `\.tar\.gz$` — literal suffix, anchored to end
>
> *Won't match: names with digits or underscores (`app2-1.0.0.tar.gz`),
> versions with suffixes like `1.2.3-rc1` — flag if those are real
> inputs.*
>
> *Assumptions: case-sensitive; package names are lowercase-only; always
> exactly three version components.*

## Notes

- **The "must not match" examples are non-negotiable.** Without them you
  get a pattern that matches your examples and half the internet.
- **Flavor changes the answer.** `\d` in JavaScript is `[0-9]`; in Python
  it matches unicode digits. Always fill it in.
- **Read the "Won't match" list before you ship.** It surfaces the
  assumptions you forgot to state — that's the real deliverable.
- **Don't use generated regex for anything security-adjacent** (input
  validation against injection, sanitizing HTML). Get a reviewed library
  for that; a regex that "looks right" is how validators fail.

## Follow-up prompts

- "Make it handle the won't-match cases for [specific input]."
- "Rewrite it as a verbose/commented pattern for the codebase."
- "Is this vulnerable to catastrophic backtracking?"

## Version

- Added: 2026-10-14
- Last updated: 2026-10-14
- Changes: initial version
