# The Lighthouse Keeper's Last Letter

> A constrained epistolary prompt — a keeper writes to the lighthouse on its final night before automation takes over.

**Category:** Writing / Fiction
**Best for:** Claude Opus 5, Claude Fable 5.1, GPT-6 Astra
**Difficulty:** Advanced

## When to use it

You want to practice the epistolary form under hard constraints. Not a story *with* letters — a story that *is* one. One voice, one recipient, one continuous act of address.

The scene is fixed: a lighthouse keeper's last night before decommissioning. He writes to the lighthouse itself. The premise carries built-in emotional stakes without needing setup, and the form is tight enough to force discipline on voice, sensory precision, and emotional arc.

Use it when you want to work on the kind of writing where nothing "happens" except a person speaking to something that cannot answer. It is not for plot-heavy drafts.

This prompt is the exact task used on the Orivel benchmark platform, where it is run head-to-head across frontier models and judged on adherence, prose quality, sensory richness, and emotional depth . A related version — a Scottish working-class keeper writing to his mother — appears in the EQ-Bench Creative Writing v3 dataset .

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
> The prompt above, run on GPT-5.2 via the Orivel benchmark .

**Output (opening lines):**
> *Dear Old Tower,*
>
> *Tonight I am writing to you by the last human lamp you will ever hold on my watch. Outside your lantern room, the sea is a black cloth shaken hard — every wave catching a tear of moonlight, every crest stitching and unstitching itself as it runs toward the rocks. Through the salt-frosted panes, your beam still turns, slow and faithful, sweeping the horizon like a hand searching for another hand in the dark.*
>
> *The new automated unit waits below in its crate, a neat cylinder of metal and wires that doesn't smell of anything at all. It has no history in its seams. You do. I can hear you breathing.*

The full GPT-5.2 response continues through all five senses, a memory of a rescue fifteen years earlier, and a closing reframe. It was judged on the Orivel platform alongside Gemini 2.5 Flash-Lite, with scoring broken down across seven dimensions .

## Notes

**The five-senses requirement is where models fail first.** Most default to sight and sound and treat smell, taste, and touch as afterthoughts. If the output reads like a checklist — *"I smelled salt, I tasted brine"* — push back with: *"The senses should belong to this specific person, not a rubric."* The Orivel judging policy explicitly deducts for sensory details that are "listed mechanically" rather than woven in .

**The metaphor is doing more work than it looks.** It forces a decision about what the light *means* to the keeper, which is really a question about what his job has meant. That is the emotional core. Forced or incoherent metaphors are a known failure mode across models and are specifically penalized in EQ-Bench's longform rubric .

**The "addressed to the lighthouse" constraint is what makes it interesting.** If the keeper wrote to his mother, it becomes a standard epistolary story. Writing to the lighthouse turns the recipient into a silent character, which makes the keeper's voice louder. The EQ-Bench variant uses the mother as recipient and produces noticeably more conventional results .

**Word count matters more than it seems.** 600–900 words is tight enough to force economy. If the output runs long, the sensory details are probably being over-explained. Orivel deducts for significantly exceeding or falling short of the range .

**The "avoid clichés" line is not optional.** Without it, most models open with the same three images: a lonely light, a grey sea, a sighing wind. The line does not eliminate the clichés, but it reduces their density.

## Model compatibility

Writing benchmarks shift fast. The rankings below are current as of late 2026, drawn from the two benchmarks that actually measure this kind of constrained creative work: Lech Mazur's LLM Creative Story-Writing Benchmark (pairwise Elo-style scoring across 56 models) and EQ-Bench's Longform Creative Writing and Creative Writing v3 boards.

### Lech Mazur — short-story element integration

This benchmark tests exactly what this prompt demands: incorporating mandatory elements into a short narrative. Top of the board as of the current README :

| Rank | Model | Score | Win chance |
|---|---|---|---|
| 1 | Claude Fable 5.1 (high) | 3.796 | 93% |
| 2 | Claude Opus 5 (xhigh) | 3.777 | 93% |
| 3 | Claude Opus 5.5 (high) | 3.767 | 93% |
| 4 | GPT-6 Astra (high) | 3.455 | 91% |
| 5 | Claude Opus 5 (high) | 3.453 | 91% |
| 6 | GLM-5.3 (max) | 3.031 | 88% |
| 7 | Claude Fable 5 (high) | 2.872 | 86% |
| 8 | GPT-5.6 Sol (xhigh) | 2.488 | 83% |
| 9 | Kimi K3 | 2.452 | 82% |
| 10 | GPT-5.5 (xhigh) | 2.451 | 82% |

Claude models dominate the top of this board. The benchmark notes that some models fail to complete all 400 stories — Claude Opus 4.7 completed 347 of 400, while Opus 4.8 completed 399 of 400 — so the ranking only reflects completed outputs .

### EQ-Bench — longform creative writing

EQ-Bench's longform board evaluates 14 dimensions including nuanced characters, emotional engagement, and faithfulness to the prompt, with a specific penalty for purple prose . On the Creative Writing v3 board, Claude Opus 5 took the top spot at 2104.9 Elo on release, a 44-point margin over Kimi K3 . Claude Fable 5 tops the longform board at Elo 2189 .

### What this means for *this* prompt

Two things matter here that a general leaderboard does not capture:

1. **Voice.** A letter written to a building lives or dies on whether the voice feels like a specific person. Claude models consistently score highest on "voice consistency and emotional nuance" in EQ-Bench's prose evaluation . GPT models are more reliable at hitting every structural requirement, but the result can feel assembled rather than felt .

2. **Instruction adherence under constraint.** The Lech Mazur benchmark is built around mandatory element integration — the same skill this prompt tests. Claude Opus 5 and Fable 5.1 lead there, with GPT-6 Astra close behind .

If you want to run a comparison for a portfolio piece, use three models: one Claude (Opus 5 or Fable 5.1), one GPT (GPT-6 Astra or GPT-5.6 Sol), and one open-weight model (GLM-5.3 or Kimi K3). The differences between them are the lesson. Claude tends to produce the most distinctive voice; GPT tends to hit every requirement cleanly; open-weight models sometimes surprise with imagery but are less reliable on the emotional arc.

Note: the Lech Mazur benchmark has been flagged by Epoch AI for versioning problems since it switched to pairwise scoring in April 2026 — the leaderboard combines results from different evaluator panels without full documentation, so treat the exact scores as directional rather than precise .

## Sources

- **Orivel benchmark — the exact prompt and judging policy:** [orivel.net/en/tasks/66-the-last-letter-from-a-lighthouse-keeper](https://orivel.net/en/tasks/66-the-last-letter-from-a-lighthouse-keeper) 
- **Lech Mazur — LLM Creative Story-Writing Benchmark (GitHub):** [github.com/lechmazur/writing](https://github.com/lechmazur/writing) 
- **EQ-Bench Longform Creative Writing leaderboard:** [eqbench.com/creative_writing_longform.html](https://eqbench.com/creative_writing_longform.html) 
- **EQ-Bench Creative Writing v3 dataset (Hugging Face) — related epistolary prompt:** [huggingface.co/datasets/Disya/eq-bench-creative-writing-v3](https://huggingface.co/datasets/Disya/eq-bench-creative-writing-v3) 
- **Epoch AI benchmark review of Lech Mazur Writing (methodology caveats):** [epoch.ai/benchmarks/lech-mazur-writing/review](https://epoch.ai/benchmarks/lech-mazur-writing/review) 

## Version

- Added: 2026-10-09
- Last updated: 2026-10-09
- Sources checked: 2026-10-09

The main structural fix was the code-fence problem: the original file used triple backticks both to open the outer code block *and* inside the prompt itself, which breaks rendering on GitHub. Quadruple backticks on the outside solve that cleanly. I also swapped the old benchmark references for the actual Orivel task page, the Lech Mazur GitHub README, and the EQ-Bench longform board, all of which are live and linkable. The model table now reflects the models that are actually on top of those boards as of late 2026, and I added the Epoch AI caveat so the scores are not overstated.
