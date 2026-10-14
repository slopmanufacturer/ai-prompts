# Lighthouse Prompt — Model Compatibility

Benchmark context for
[The Lighthouse Keeper's Last Letter](../prompts/writing/lighthouse-keepers-last-letter.md).
Kept in a separate file so the prompt itself doesn't go stale with the
leaderboards.

Writing benchmarks shift fast. The rankings below are current as of late
2026, drawn from the two benchmarks that actually measure this kind of
constrained creative work: Lech Mazur's LLM Creative Story-Writing
Benchmark (pairwise Elo-style scoring across 56 models) and EQ-Bench's
Longform Creative Writing and Creative Writing v3 boards.

## Lech Mazur — short-story element integration

This benchmark tests exactly what this prompt demands: incorporating
mandatory elements into a short narrative. Top of the board as of the
current README:

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

Claude models dominate the top of this board. The benchmark notes that
some models fail to complete all 400 stories — Claude Opus 4.7 completed
347 of 400, while Opus 4.8 completed 399 of 400 — so the ranking only
reflects completed outputs.

## EQ-Bench — longform creative writing

EQ-Bench's longform board evaluates 14 dimensions including nuanced
characters, emotional engagement, and faithfulness to the prompt, with a
specific penalty for purple prose. On the Creative Writing v3 board,
Claude Opus 5 took the top spot at 2104.9 Elo on release, a 44-point
margin over Kimi K3. Claude Fable 5 tops the longform board at Elo 2189.

## What this means for the prompt

Two things matter here that a general leaderboard does not capture:

1. **Voice.** A letter written to a building lives or dies on whether the
   voice feels like a specific person. Claude models consistently score
   highest on "voice consistency and emotional nuance" in EQ-Bench's prose
   evaluation. GPT models are more reliable at hitting every structural
   requirement, but the result can feel assembled rather than felt.

2. **Instruction adherence under constraint.** The Lech Mazur benchmark is
   built around mandatory element integration — the same skill this prompt
   tests. Claude Opus 5 and Fable 5.1 lead there, with GPT-6 Astra close
   behind.

If you want to run a comparison for a portfolio piece, use three models:
one Claude (Opus 5 or Fable 5.1), one GPT (GPT-6 Astra or GPT-5.6 Sol),
and one open-weight model (GLM-5.3 or Kimi K3). The differences between
them are the lesson. Claude tends to produce the most distinctive voice;
GPT tends to hit every requirement cleanly; open-weight models sometimes
surprise with imagery but are less reliable on the emotional arc.

Note: the Lech Mazur benchmark has been flagged by Epoch AI for
versioning problems since it switched to pairwise scoring in April 2026 —
the leaderboard combines results from different evaluator panels without
full documentation, so treat the exact scores as directional rather than
precise.

## Sources

- **Orivel benchmark — the exact prompt and judging policy:** [orivel.net/en/tasks/66-the-last-letter-from-a-lighthouse-keeper](https://orivel.net/en/tasks/66-the-last-letter-from-a-lighthouse-keeper)
- **Lech Mazur — LLM Creative Story-Writing Benchmark (GitHub):** [github.com/lechmazur/writing](https://github.com/lechmazur/writing)
- **EQ-Bench Longform Creative Writing leaderboard:** [eqbench.com/creative_writing_longform.html](https://eqbench.com/creative_writing_longform.html)
- **EQ-Bench Creative Writing v3 dataset (Hugging Face) — related epistolary prompt:** [huggingface.co/datasets/Disya/eq-bench-creative-writing-v3](https://huggingface.co/datasets/Disya/eq-bench-creative-writing-v3)
- **Epoch AI benchmark review of Lech Mazur Writing (methodology caveats):** [epoch.ai/benchmarks/lech-mazur-writing/review](https://epoch.ai/benchmarks/lech-mazur-writing/review)

## Version

- Added: 2026-10-14 (extracted from the prompt file)
- Sources checked: 2026-10-09
