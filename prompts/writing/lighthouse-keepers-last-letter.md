# The Lighthouse Keeper's Last Letter

> A detailed epistolary prompt for writing a story told entirely through a letter addressed to a decommissioned lighthouse.

**Category:** Writing / Fiction
**Best for:** Claude, GPT-5, Qwen3 Max
**Difficulty:** Advanced

## When to use it

You want to practice a specific, constrained form: the epistolary story. Not a story *with* letters in it — a story that *is* a letter. One voice, one recipient, one continuous act of address.

This prompt is built around a very particular scene: a lighthouse keeper's final night before automation takes over. He writes to the lighthouse itself. The form is tight enough to force discipline, and the emotional stakes are built into the premise without needing explanation.

Use it when you want to work on voice, sensory precision, and emotional arc inside a container. It's not for plot-heavy writing. It's for the kind of writing where nothing "happens" except a person speaking to something that can't answer.

The original version of this prompt came out of a creative writing benchmark on Hugging Face and has been used to compare model outputs side by side[reference:0]. It works because it has hard requirements — five senses, a memory, a metaphor, an emotional shift, a reframing final line — that give you something concrete to aim at and something concrete to evaluate.

## The prompt

Write a short story (600–900 words) in the form of a letter written by a
lighthouse keeper on the night their lighthouse is being decommissioned and
replaced by an automated system. The letter should be addressed to the
lighthouse itself.

Your story must incorporate the following elements:

    At least one vivid sensory detail for each of the five senses (sight,
    sound, smell, taste, touch). These should be woven into the letter
    naturally, not listed.

    A specific memory from the keeper's past that is triggered by something
    happening in the present moment.

    A metaphor or extended metaphor that connects the lighthouse's light to
    something deeper about human connection or purpose.

    An emotional arc — the letter should not remain at the same emotional
    pitch throughout. It should shift at least once in a meaningful way.

    A final line that recontextualizes or reframes something mentioned
    earlier in the letter.

Write the full letter as your response.

Avoid purple prose. Avoid clichés about the sea, solitude, or lighthouses.
Write naturally, as a specific person would write.
text


## Example

**Input:**
> The prompt above, sent to Claude.

**Output (excerpt):**
> *Dear Old Tower,*
>
> *Tonight I am writing to you by the last human lamp you will ever hold on my watch. Outside your lantern room, the sea is a black cloth shaken hard — every wave catching a tear of moonlight, every crest stitching and unstitching itself as it runs toward the rocks. Through the salt-frosted panes, your beam still turns, slow and faithful, sweeping the horizon like a hand searching for another hand in the dark.*
>
> *The new automated unit waits below in its crate. A neat cylinder of metal and wires that doesn't smell of anything at all. It has no opinion about the weather. It will not learn the particular groaning sound you make when the wind comes from the northeast. It will not know that I have been talking to you for eleven years.*

The opening lines come from a GPT-5.2 response to this prompt, which scored well on adherence to the sensory and metaphor requirements[reference:1].

## Notes

- **The five senses requirement is the hard part.** Most models default to sight and sound. Smell, taste, and touch are where the writing gets specific. If the output lists them mechanically, push back: *"The senses should feel like they belong to this person, not a checklist."*

- **The metaphor requirement is doing more work than it looks.** It forces the writer to decide what the light *means* to the keeper, which is really a question about what the keeper's job has meant. That's the emotional core.

- **The "addressed to the lighthouse" constraint is what makes it interesting.** If the keeper wrote to his mother, it would be a standard epistolary story. Writing to the lighthouse turns the recipient into a character — one that can't speak, which makes the keeper's voice louder.

- **Word count matters.** 600–900 words is tight. It forces economy. If the output runs long, the sensory details are probably being over-explained.

- **The original benchmark prompt included a Scottish, working-class keeper writing to his mother**[reference:2]. The "addressed to the lighthouse" version is a later variant from a separate benchmark task[reference:3]. Both work. The lighthouse version is slightly more constrained and slightly more interesting for voice work.

## Version

- Added: 2026-10-09
- Last updated: 2026-10-09
