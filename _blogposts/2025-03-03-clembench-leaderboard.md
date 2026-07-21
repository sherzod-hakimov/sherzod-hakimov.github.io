---
title: "It is finally here! Clembench Leaderboard v2.0 is live 🎉"
collection: blogposts
date: 2025-03-03
permalink: /blog/2025/clembench-leaderboard/
excerpt: "We've put online the latest version of our LLM leaderboard, now based on version 2.0 of clembench — the longest-running game-based evaluation of agentic capabilities of LLMs."
header:
  teaser: "/images/blog/clembench-leaderboard-2025-03.jpg"
---

We've just put online the latest version of our LLM leaderboard, now based on version 2.0 of clembench ("the longest-running game-based evaluation of agentic capabilities of LLMs").

**Highlights ✨**

- even more games (total: 14): 20 questions, codenames, text adventure, map navigation are added to the old favourites wordle, taboo, reference game, drawing game etc.
- even more instances (total: 817)
- even for the games shared with the previous version (1.6), we generated new instances for 2.0, which means that data contamination is not an issue
- reasoning models added (o3-mini, claude-3.7, deepseek-r1)

**Reminder 📝**

- Our "clemscore" is a combination of how well the models follow the game instructions (% played) and how well the concluded game instances were played (quality score).
- We let the same model play both sides of the game (but independently, of course), and we judge the model by the combined performance.

**Settings for benchmarked models ⚙️**

- temp=0, max_new_tokens: 300
- Claude-3.7 reasoning budget: 4k
- Deepseek-r1: max_new_tokens limit is removed.
- API backends: OpenAI, Google, Anthropic, OpenRouter (for DeepSeek AI & Mistral AI models)
- Local backend: 2 Nvidia-A100 cluster for remaining open models using Hugging Face library

**Interesting Findings 💡**

- Added reasoning time gives models a slight edge, but not terribly much so (o3-mini and claude-3.7 sonnet at around 67, claude-3.5 sonnet and gpt-4o at around 62)
- Deepseek-r1 had problems in returning responses for all queries using OpenRouter
- Reasoning increased latency ⏳: o3-mini vs. gpt-4o => 7.7 vs. 0.9 seconds, claude-3.7 vs. claude-3.5 => 5.2 vs. 1.4 seconds; deepseek-r1 vs. deepseek v3 => 81.7 sec vs. 4.4 seconds
- The closed frontier models are still at the frontier 📈, but not terribly much so (with deepseek-v3 coming in at 53.3 and Llama-3.1-405B at 52.8, to GPT-4o's 60.5)
- Size doesn't matter that much anymore (with Llama-3.1-405B only 4 points above Qwen-2.5-72B and Llama-3.1-70B)
- The inventor of all of this, Google (Google DeepMind), still has some catching up to do: Gemini-2.0-flash still trailing OpenAI, Anthropic or even Meta Llama models.
- Europe 🇪🇺: Mistral models unfortunately are not comparable: huge margin between them and other commercial models. Even Llama-70B does much better.
- China 🇨🇳, on the other hand, comes in strongly: Deepseek is mentioned above; Alibaba's Qwen-Max is a new player that has caught up with the competition.

As before, this version will be active for a couple of months, and we will be adding new models as they appear.

On that note: we're happy to take sponsorship / accept 🤝 compute credit. This surely is getting expensive; cost 💸 : ~500 EUR to benchmark selected models.

Leaderboard: [huggingface.co/spaces/colab-potsdam/clem-leaderboard](https://huggingface.co/spaces/colab-potsdam/clem-leaderboard)

![Clembench Leaderboard v2.0](/images/blog/clembench-leaderboard-2025-03.jpg)
