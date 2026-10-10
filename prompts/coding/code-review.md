# Senior Code Reviewer

> Paste your code, get a review from someone who's been doing this for a while.

**Category:** Coding
**Best for:** ChatGPT, Claude, Grok, DeepSeek, Kimi, MiniMax, Qwen — anything with a decent context window
**Difficulty:** Beginner
**Output:** Structured issue list with severities and fixes

## When to use it

You wrote something and want a second pair of eyes before you commit it. Maybe you don't have a colleague free, maybe you just want a fast pass before a PR. Either way, this gets you a real review instead of "looks good to me."

It works best on a single function or file. Don't paste your whole codebase in — the review gets shallow fast.

## Variables to fill in

| Placeholder | What goes there |
|---|---|
| `[LANGUAGE]` | e.g. Python 3.12, TypeScript 5, Go 1.22 |
| `[ONE LINE]` | What the code is supposed to do |
| `[WHERE IT RUNS]` | Server, CLI, browser, embedded, etc. |
| `[PASTE CODE HERE]` | The code itself |

## The prompt

```
You are a senior software engineer with 15 years of experience reviewing
code that ships to production. Review the code below.

Context:
- Language: [LANGUAGE]
- What it's supposed to do: [ONE LINE]
- Where it runs: [WHERE IT RUNS]

If any of the above is missing, or the code is truncated or incomplete,
ask for it before reviewing. Do not guess.

Review in this order. Only include a section if you found something.

1. Correctness — bugs, edge cases, off-by-one errors, error handling
2. Security — injection, input validation, secrets handling, unsafe defaults
3. Readability — naming, structure, comments only where they earn their place
4. Performance — only if there's a real concern. No micro-optimization.

For each issue:
- Severity: Critical / Major / Minor
- Location: line number or snippet
- Problem: what's wrong and why it matters
- Fix: concrete code, not "consider refactoring"

Rules:
- Be direct. Skip the praise.
- Don't rewrite the whole thing unless asked.
- If the code is fine, say so in one line and stop.
- End with the single change that matters most.

Code:
[PASTE CODE HERE]
```

## Example

**Input:**

```
Language: Python 3.12
Does: Reads a text file and returns a word frequency dict
Runs: CLI tool, filename comes from argv

def wordfreq(path):
    f = open(path)
    text = f.read()
    f.close()
    words = text.split()
    counts = {}
    for w in words:
        if w in counts:
            counts[w] = counts[w] + 1
        else:
            counts[w] = 1
    return counts
```

**Output:**

> **Critical** — `open(path)` has no `encoding`. Breaks on Windows and any non-UTF-8 locale. Fix: `open(path, encoding="utf-8")`.
>
> **Major** — `path` comes from `argv` with no validation. `../../etc/passwd` reads fine. Fix: resolve the path and check it against an allowed base directory.
>
> **Minor** — Twelve lines reimplement `collections.Counter`. Fix: `return Counter(text.split())`.
>
> Rest is fine. Biggest win: pin the encoding.

## Notes

- The "skip the praise" line matters. Without it, most models open with three paragraphs of compliments before saying anything useful.
- Smaller chunks get better reviews. One function at a time beats a whole file.
- Always fill in the context block. Reviews without "what it's supposed to do" are guesswork.
- If it's being too nice, add: *"Assume I'm shipping this to production tomorrow. What would break?"* That shifts the tone fast.
- Run it twice. Second pass on the fixed code catches whatever the first fix broke.

## Follow-up prompts

- "Now review it as if I'm shipping tomorrow. What breaks?"
- "Rewrite only the Critical issues. Don't touch anything else."
- "Write tests for the edge cases you flagged."

## Version

- Added: 2026-10-09
- Last updated: 2026-10-09
- Changes: fixed typos, added context block and severity levels to the prompt, added follow-up prompts and variables table, expanded example
