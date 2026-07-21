---
layout: post
title:  "How do I know that ArtSlaw actually tells the truth?"
date:   2026-07-21 09:00:00 +0200
categories: [artslaw, ai, evals]
---

ArtSlaw is my AI exhibition guide, you paste a link, it researches the show via live web search and walks you through the artist and the works. Like any other LLM, it sounds truthful and gives you the impression, that every statement is correct. But that is exactly the problem with language models, they are confident even when they are wrong.

One problem that emerged often was a wrong number of works or misstated type of artworks in the exhibition. Another frequent error in testing was that both models repeatedly told me that Tracey Emin was made a Dame in 2019 or in 2013. Both years are wrong (it happened in 2024), but an uninformed user would never crosscheck these dates and take this information for granted.

### Building a judge

So I built an evaluation suite. After ArtSlaw gives a tour, another AI (a stronger model acting as a judge) takes every single factual claim in the answer and checks it against the exact evidence the model actually saw, so the exhibition page plus its own search results. A claim only counts as grounded if the evidence supports it. Memorized knowledge doesn't count, no matter how correct it might be. Relying on memorized knowledge with light models such as Haiku or Mistral Small is risky, as the models with less training tokens and parameters tend to hallucinate more. Even the flagship models hallucinate, which is a fundamental problem or feature with probabilistic token predictors like LLMs.

On top of that the suite checks the facts deterministically: 

- Does the model call the web search tool when it should?
- Does every tour follow the proposed structure?
- Does a German question get a German answer?
- How fast is the response generated?
- What does it cost?

The whole evaluation suite runs offline against recorded web fixtures and always for the same set of exhibitions to reduce fluctuation. So it can be re-run after any prompt or systematic change and be compared against the baseline. In the end a run gets percentage scores for each metric (to name a few: Groundedness of claims, Contradiction rate, latency, cost). If a change makes things worse, the run fails.

### The results

With this eval suite, I could finally measure the impact of prompt and other changes objectively. When I first measured groundedness, Claude was at 79% and Mistral at 69%. Meaning: in the worst case, almost one in three "facts" in a tour had no backing in the evidence. That was the starting point.

Then I iterated on the system prompt in three rounds, measuring after each one, which improved the results for Claude to 93% and Mistral to 76%. A big up for Claude, but Mistral was still well below the goal I have set of at least 90% groundedness, as Google's AI overview's groundedness is at 91% ([Cloro - AI Grounding][Cloro]).

I have already revised the system prompt three times, so another change needed to be done. I have discovered, that Mistral has not used web search as much as Claude, so it lacked good background information to process. I have thus forced the model to use web search in every run and also increased the amount of info that was being scraped from the webpages. 

These two levers have increased Mistral’s groundedness score to 91% with Claude’s staying constant. Mission accomplished. 91% is still not perfect, but the remaining “incorrect” statements are often subjective interpretations of the exhibition or remarks about its atmosphere. The LLM should continue to have some creative leeway in its responses so that they are creative and easy to read.

![Eval Runs](/assets/images/20260721_Eval_results.png)
Results of three eval runs of the eval suite of ArtSlaw. The results of Claude Haiku are shown in blue, Mistral Small in orange.

The final run judged around 400 claims per provider, three repeats per scenario (5 different exhibitions). Contradiction rate (claims that actively conflict with the evidence) is now at 0.2–0.3%. And the trade-off between my two providers is now visible in hard numbers: a Claude tour costs me about $0.012, a Mistral tour $0.0013 — nearly a tenth — while groundedness is only two points apart.

### Can I trust the judge?

I am using an AI to check an AI. The honest answer: not blindly. The judge is a stronger model than the ones it grades (Claude Sonnet 5 is strong and factful enough to do factchecking against a database of text), it sees the exact evidence, and I sanity-checked its verdicts by hand. It also costs more money, about $3 per full run. But it will make mistakes too. What I trust is the *direction*: when the score moves from 79 to 93 under the same judge, something real has improved.

The whole suite is open source now, together with the rest of ArtSlaw. I made the repository public this week. If you want to see how it works in detail, have a look at [the eval README on GitHub][Eval_Readme].

For me this was the moment ArtSlaw stopped feeling like a demo and started feeling like a product. Not because the answers got prettier, because I can finally prove they got better!

[Eval_Readme]: https://github.com/Febtwenty/artslaw/blob/main/server/evals/README.md
[Cloro]: https://cloro.dev/blog/ai-grounding-by-engine/