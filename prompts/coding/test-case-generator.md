# Test Case Generator

> Give it a function, get the cases worth writing — grouped by intent, not framework boilerplate.

**Category:** Coding
**Best for:** Any capable language model
**Difficulty:** Beginner
**Output:** Grouped list of test cases with a one-line "why" each

## When to use it

You're about to write tests for a function and want to know *which* tests
to write before you touch a framework. The output is the checklist — what
to cover and why — not the test code itself, because the cases are the
hard part and the syntax is the easy part.

Best on a single function or small unit. On a whole module it degenerates
into "test the happy path, test errors" — useless.

## Variables to fill in

| Placeholder | What goes there |
|---|---|
| `[LANGUAGE]` | e.g. Python 3.12, TypeScript — only so the cases use the right vocabulary |
| `[PASTE CODE]` | The function or unit under test |

## The prompt

````
List the test cases worth writing for this [LANGUAGE] function.

Rules:
- Group them under three headings:
  "Should work" — normal inputs, including the ones that look edge-y
    but are legal.
  "Should fail" — invalid inputs, and what "fail" means here
    (exception, error return, rejected promise).
  "Should not explode" — inputs the function might accept but that
    stress it: empty, huge, null-adjacent, concurrent, malformed.
- One line per case: the input, the expected behavior, why it matters.
- Order cases inside each group by which bug you'd most regret missing.
- If a case depends on behavior the signature doesn't reveal (does it
  throw? return null? mutate?), ask me before listing it — don't guess.
- No test code. No setup, no assertions, no framework. Cases only.
- Cap it at the cases that earn their place. If you can cover two cases
  with one input, merge them.

Code:
[PASTE CODE]
````

## Example

**Input:**

> Language: Python 3.12
>
> ```python
> def discount(price, coupon):
>     if coupon == "HALF":
>         return price * 0.5
>     return price
> ```

**Output:**

> **Should work**
> - `discount(100, "HALF")` → 50.0 — the only real coupon path.
> - `discount(100, "NOPE")` → 100 — unknown coupons are silently ignored;
>   worth pinning whether that's intended.
>
> **Should fail**
> - Nothing should fail — every input returns a number. That itself is
>   worth a comment: `discount(-50, "HALF")` → -25.0 is "valid" per the
>   code but probably not per the business.
>
> **Should not explode**
> - `discount(0, "HALF")` → 0.0 — free item, harmless.
> - `discount(1e308, "HALF")` → inf — float overflow, unlikely but real.
>
> *Question the prompt would ask first if needed: should an unknown
> coupon raise or pass through? The code passes through — flag it.*

## Notes

- **"Should not explode" is the bucket models skip without the heading.**
  Empty strings, zero, negatives, unicode, `float('nan')` — that's where
  production bugs live.
- **The "ask before guessing" line matters more than it looks.** Whether
  a function throws or returns None changes half the cases; guessing
  produces confident, wrong lists.
- **"Cases only, no code" is deliberate.** Once it writes assertions it
  stops thinking about coverage. Generate the list first, then follow up
  with *"Write these in pytest."*
- **If it returns 30 cases, it's padding.** Ask: *"Which five would you
  keep if you could only keep five?"* — those are your tests.

## Follow-up prompts

- "Write these in [FRAMEWORK], grouped the same way."
- "Which of these would property-based testing cover better than
  examples?"
- "Which five cases would you keep if you could only keep five?"

## Version

- Added: 2026-10-14
- Last updated: 2026-10-14
- Changes: initial version
