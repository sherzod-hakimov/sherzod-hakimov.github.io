---
title: "Digital Sovereignty in EU — The AI Landscape"
collection: blogposts
date: 2026-08-02
permalink: /blog/2026/digital-sovereignty-eu/
excerpt: "We evaluated 9 LLMs as agents playing dialogue games across all 24 official EU languages plus six others — 108,000 episodes in total. In every single EU language, both commercial models beat every open-weight model."
header:
  teaser: "/images/blog/digital-sovereignty-2026-08-cover.png"
---

> Every person may write to the institutions of the Union in one of the languages of the Treaties and must have an answer in the same language.
> — *EU Charter of Fundamental Rights, Art. 41(4)*

As AI systems are being deployed in different services around the globe, we want to *investigate* whether current popular LLMs are capable of delivering adequate performance for **certain language capabilities across all 24 languages of the European Union** 🇪🇺.

## Why this evaluation?

Most multilingual benchmarks start from an English multiple-choice test, translate it into other languages and score the answers. This measures knowledge recall through a translation layer, not the ability to use a language. **The real use of LLMs is dialogic**: sustained, goal-directed, with each turn depending on what the model just said and what the user requested.

So we evaluated LLMs as **agents playing dialogue games in self-play** — the model has to follow the rules, track the state, and reach a goal, and it is scored programmatically on whether it did. No gold answers, nothing to leak, and the game mechanics are language-agnostic, so the same benchmark ports to a new language by localising prompt and word-list files rather than authoring a new test.

In our multilingual benchmarking project we tested **9 models · 30 languages · 14 tasks (multi-turn dialogue games) · ~108,000 episodes.** All 24 official EU languages plus Arabic, Chinese, Russian, Serbian, Turkish and Ukrainian. To our knowledge this is the largest multi-turn, interactive evaluation of LLMs across languages published so far — earlier versions of this benchmark covered three languages (mainly English, partially German and Italian). The models were chosen by recency, multilingual capability and good performance overall across other benchmarks.

This gives us 108k episodes of models playing conversational games in different languages, with different success rates. We also look at the amount of web data available for the languages we tested, and available economic data on the regions that they serve. Here is what we found.

## What we found

**1. There are two tiers, and the distance between them is wide.** In every single one of the 24 official EU languages, both commercial models score above *every* open-weight model. Not on average — in all 24. The gap runs from 5.6 points in Greek to 35.8 in Irish, averaging 16 points.

![Best commercial model vs best open-weight model, per EU language](/images/blog/digital-sovereignty-2026-08-cover.png)

**2. Parity is achievable, but the open-weight models don't deliver.** Even though Maltese has roughly four orders of magnitude less public web text than English, GPT-5.4 scores 92.0 in Maltese and 91.8 in English. Irish, Estonian and Latvian look much the same. These languages are not intrinsically harder — they are under-served by open-weight models. It seems like *commercial model providers have cracked the code of training data for specific languages*.

![Available web data vs performance](/images/blog/digital-sovereignty-2026-08-webdata.png)

*Available web data vs. performance. The web data values are taken from the HPLT-v3 and FineWeb datasets.*

**3. Open models track the data; closed models do not.** For all seven open-weight models, performance follows both the crawled text available in a language and its economic weight. For the two commercial systems, that correlation is essentially zero. Whatever closes the gap is not in the public crawl.

**4. Speakers of smaller languages pay twice.** Tokenisers split Finnish, Maltese and Estonian into roughly twice as many tokens per word as English, and APIs bill per token. Pooled across models, the median non-English language **costs 31% more to run and scores 10% lower**. Equal access to the same model, at the same price, still buys unequal service.

![Performance and cost per language, relative to English](/images/blog/digital-sovereignty-2026-08-cost.png)

*Performance vs. cost across languages in comparison to English.*

**5. Scale is not the answer.** The 675B-parameter Mistral-Large-3 averages 40.5 across the 30 languages — below the far smaller Gemma-4 and Qwen3.6. Throwing parameters at the problem has not worked; targeted language resources are a different lever.

![Model scale vs EU-24 average performance](/images/blog/digital-sovereignty-2026-08-scale.png)

*Average performance across all tasks and languages.*

**6. Chinese models are not the answer either.** The open-weight models from other regions understandably don't value all EU-24 languages equally: the Chinese models we tested are good at Chinese and English, mixed on other languages.

## What needs to happen

- **Fund language resources, not just models.** The gap is a data gap, and the market will not close it: the languages that need the most work have the smallest open web data to use as the training source. Public broadcast archives, parliamentary records and digitised national collections are assets Europe already owns.
- **Make tokeniser coverage a procurement criterion.** Vocabulary allocation is a design decision that directly sets the price a citizen pays per sentence. It is measurable, and it should be specified.
- **Evaluate interactively, and across the whole EU-24.** A model that scores well on translated multiple-choice questions in five large languages tells you very little about what a citizen in Malta or Ireland will experience.
- **Be honest about the trade-off.** Today the systems that serve the EU's smaller languages well are closed and non-European. Sovereignty means either accepting that dependence or investing in resources beyond the open web — but not pretending the choice is not there.

---

**arXiv preprint of the study:** [https://arxiv.org/abs/2608.01395](https://arxiv.org/abs/2608.01395)

**Leaderboard:** [clembench.github.io/leaderboard.html](https://clembench.github.io/leaderboard.html)

**Source code:** [github.com/clembench/multilingual](https://github.com/clembench/multilingual)

**Current model runs & results:** [github.com/clembench/clembench-multilingual-runs](https://github.com/clembench/clembench-multilingual-runs)
