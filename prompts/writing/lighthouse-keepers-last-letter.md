# The Lighthouse Keeper's Last Letter

> A constrained epistolary prompt — a keeper writes to the lighthouse on its final night before automation takes over.

**Category:** Writing / Fiction
**Best for:** Claude Opus 5, Claude Fable 5.1, GPT-6 Astra
**Difficulty:** Advanced
**Output:** A complete short story, 600–900 words, in epistolary form

## When to use it

You want to practice the epistolary form under hard constraints. Not a story *with* letters — a story that *is* one. One voice, one recipient, one continuous act of address.

The scene is fixed: a lighthouse keeper's last night before decommissioning. He writes to the lighthouse itself. The premise carries built-in emotional stakes without needing setup, and the form is tight enough to force discipline on voice, sensory precision, and emotional arc.

Use it when you want to work on the kind of writing where nothing "happens" except a person speaking to something that cannot answer. It is not for plot-heavy drafts.

This prompt is the exact task used on the Orivel benchmark platform, where it is run head-to-head across frontier models and judged on adherence, prose quality, sensory richness, and emotional depth. A related version — a Scottish working-class keeper writing to his mother — appears in the EQ-Bench Creative Writing v3 dataset.

## The prompt

````
Write a short story (600–900 words) in the form of a letter written by a
lighthouse keeper on the night their lighthouse is being decommissioned and
replaced by an automated system. The letter should be addressed to the
lighthouse itself.

Your story must incorporate the following elements:

- At least one vivid sensory detail for each of the five senses (sight,
  sound, smell, taste, touch). These should be woven into the letter
  naturally, not listed.

- A specific memory from the keeper's past that is triggered by something
  happening in the present moment.

- A metaphor or extended metaphor that connects the lighthouse's light to
  something deeper about human connection or purpose.

- An emotional arc — the letter should not remain at the same emotional
  pitch throughout. It should shift at least once in a meaningful way.

- A final line that recontextualizes or reframes something mentioned
  earlier in the letter.

Write the full letter as your response.

Avoid purple prose. Avoid clichés about the sea, solitude, or lighthouses.
Write naturally, as a specific person would write.
````

## Example

**Input:**
> The prompt above, run on GPT-5.2 via the Orivel benchmark.

**Output (opening lines):**
> *Dear Old Tower,*
>
> *Tonight I am writing to you by the last human lamp you will ever hold on my watch. Outside your lantern room, the sea is a black cloth shaken hard — every wave catching a tear of moonlight, every crest stitching and unstitching itself as it runs toward the rocks. Through the salt-frosted panes, your beam still turns, slow and faithful, sweeping the horizon like a hand searching for another hand in the dark.*
>
> *The new automated unit waits below in its crate, a neat cylinder of metal and wires that doesn't smell of anything at all. It has no history in its seams. You do. I can hear you breathing.*

The full GPT-5.2 response continues through all five senses, a memory of a rescue fifteen years earlier, and a closing reframe. It was judged on the Orivel platform alongside Gemini 2.5 Flash-Lite, with scoring broken down across seven dimensions.

## Notes

**The five-senses requirement is where models fail first.** Most default to sight and sound and treat smell, taste, and touch as afterthoughts. If the output reads like a checklist — *"I smelled salt, I tasted brine"* — push back with: *"The senses should belong to this specific person, not a rubric."* The Orivel judging policy explicitly deducts for sensory details that are "listed mechanically" rather than woven in.

**The metaphor is doing more work than it looks.** It forces a decision about what the light *means* to the keeper, which is really a question about what his job has meant. That is the emotional core. Forced or incoherent metaphors are a known failure mode across models and are specifically penalized in EQ-Bench's longform rubric.

**The "addressed to the lighthouse" constraint is what makes it interesting.** If the keeper wrote to his mother, it becomes a standard epistolary story. Writing to the lighthouse turns the recipient into a silent character, which makes the keeper's voice louder. The EQ-Bench variant uses the mother as recipient and produces noticeably more conventional results.

**Word count matters more than it seems.** 600–900 words is tight enough to force economy. If the output runs long, the sensory details are probably being over-explained. Orivel deducts for significantly exceeding or falling short of the range.

**The "avoid clichés" line is not optional.** Without it, most models open with the same three images: a lonely light, a grey sea, a sighing wind. The line does not eliminate the clichés, but it reduces their density.

## Model compatibility

Benchmark context and model rankings live in [docs/lighthouse-model-compatibility.md](../../docs/lighthouse-model-compatibility.md) — kept separate so this file doesn't go stale with the leaderboards.

## Sources

The benchmark claims in the notes above are backed by the sources listed in [docs/lighthouse-model-compatibility.md](../../docs/lighthouse-model-compatibility.md#sources).

## Version

- Added: 2026-10-09
- Last updated: 2026-10-14
- Changes: moved the model-compatibility tables and sources to docs/ so they don't go stale inside the prompt; removed leftover footnote artifacts (stray spaces before periods); added the Output field. Earlier: fixed the code-fence problem with quadruple backticks, swapped old benchmark references for live links, added the Epoch AI caveat.
