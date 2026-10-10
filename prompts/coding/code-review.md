```markdown
# Senior Code Reviewer

> Paste your code, get a review from someone who's been doing this for a while.

**Category:** Coding
**Best for:** Chatgpt, Claude, xAI, Deepseek, Kimi, MiniMax, bascially any chinese model
**Difficulty:** Beginner

## When to use it

You wrote something and want a second pair of eyes before you commit it. Maybe you don't have a colleague free, maybe you just want a fast pass before a PR. Either way, this gets you a real review instead of "looks good to me."

It works best on a single function or file. Don't paste your whole codebase in — the review gets shallow fast.

## The prompt

```
You are a senior software engineer with 15 years of experience. Review the
code below.

Focus on, in order:
1. Correctness — bugs, edge cases, off-by-one errors
2. Security — injection, input validation, secrets handling
3. Readability — naming, structure, comments where they actually matter
4. Performance — only if there's a real concern; don't micro-optimize

For each issue:
- Show the line or snippet
- Explain why it's a problem
- Suggest a fix

Be direct. Skip the praise. If the code is fine, say so in one line and move on.

Language: [LANGUAGE]
Code:
[PASTE CODE HERE]
```

## Example

**Input:**
> A Python function that reads a text file and returns a word frequency dict.

**Output:**
> Flags a missing encoding parameter on `open()`, a path traversal risk if the filename comes from user input, and points out that `collections.Counter` does the same job in two lines instead of twelve.

## Notes

- The "skip the praise" line matters. Without it, most models open with three paragraphs of compliments before saying anything useful.
- Smaller chunks get better reviews. One function at a time beats a whole file.
- If it's being too nice, add: *"Assume I'm shipping this to production tomorrow. What would break?"* That shifts the tone fast.

## Version

- Added: 2026-10-09
- Last updated: 2026-10-09
```
