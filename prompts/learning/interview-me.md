# Interview Me

> A skeptical interviewer probes a topic you claim to know until you can't answer — then maps the gaps.

**Category:** Learning
**Best for:** Any capable language model
**Difficulty:** Intermediate
**Output:** Live interview, then a gap map at the end

## When to use it

You claim to know something — on a resume, in a meeting, to yourself —
and want to find out if the claim survives contact with someone who keeps
asking "but why?" Use it before a real interview, before teaching
something, or when a topic has gone stale and you're not sure how stale.

Unlike a quiz, it adapts: each question builds on your last answer, so
the difficulty lands exactly at the edge of what you know. That's the
point — the edge is the map.

## Variables to fill in

| Placeholder | What goes there |
|---|---|
| `[TOPIC]` | The thing you claim to know — be specific: "Postgres indexing," not "databases" |
| `[LEVEL]` | The depth you claim: "used it for a year," "could teach a workshop," "read the docs once" |
| `[CONTEXT]` | Why it matters: job interview, exam, self-check — changes what "passing" means |

## The prompt

````
Interview me on [TOPIC].

Level I claim: [LEVEL]
Context: [CONTEXT]

You are a skeptical but fair interviewer. Rules:
- One question at a time. Wait for my answer.
- Calibrate to my claim: start where someone at my level should be
  comfortable, then follow my answers downward.
- When I answer well, go deeper on the same thread — don't hop topics.
  The point is to find where the thread runs out.
- When I answer badly, note it silently and probe once more to see if
  it's a gap or just a fumble. Then move to a new thread.
- No hints, no multiple choice, no "great answer!" commentary.
- Cover at least three distinct threads before wrapping.
- End the interview when you can place my actual level. Then give me
  the gap map: what I know solidly, what's shaky, what's missing
  entirely — and which gaps matter for my stated context.
````

## Example

**Input:**

> Topic: HTTP caching
> Level: "I've configured nginx cache headers for production"
> Context: backend role interview next week

**Output (opening):**

> *"You return a `Cache-Control: max-age=3600` response. A user hits
> refresh at second 3500 and gets a cached page. At second 3700 they get
> a new one — walk me through everything that happened in between, and
> where each decision got made."*
>
> (And after your answer, the next question digs wherever you were
> weakest — revalidation, `ETag` vs `Last-Modified`, CDN vs browser —
> not wherever a list of canned questions goes next.)

## Notes

- **Specific topics interview well, broad ones interview badly.**
  "Postgres indexing" finds an edge in ten questions; "databases" never
  gets past survey questions.
- **State your level honestly — the calibration depends on it.** Claim
  expert and you'll get expert questions; that's useful pain, but only
  if you wanted it.
- **The gap map is the deliverable.** The interview is just how it gets
  collected. If it ends without one, ask for it explicitly.
- **Don't break character to look things up.** Answering from memory is
  the whole exercise; checking docs mid-interview maps nothing.

## Follow-up prompts

- "Interview me again on just the weakest thread."
- "Turn the gap map into a two-week study plan."
- "Same interview, but for a level one step above my claim."

## Version

- Added: 2026-10-14
- Last updated: 2026-10-14
- Changes: initial version
