---
title: "Benchmarking the Most Recent Multimodal Language Models"
collection: blogposts
date: 2024-09-20
permalink: /blog/2024/benchmarking-multimodal-models/
excerpt: "We benchmarked the most recent Multimodal Language Models using our clembench framework across five dialogue games."
header:
  teaser: "/images/blog/multimodal-2024-09.jpg"
---

We benchmarked the most recent Multimodal Language Models using our clembench framework. The benchmark includes 5 dialogue games that evaluate:

1. negotiation & reasoning about an image
2. reference generation
3. map/graph navigation and spatial reasoning (this game has 3 versions)

**Findings:** commercial models are far ahead in "instruction following" (% of played episodes) and "task solving" (quality score).

- The best commercial model: **Claude-3.5** (80 clemscore)
- The best open model: **InternVL2-26B** (37 clemscore)

The leaderboard is here: [huggingface.co/spaces/colab-potsdam/clem-leaderboard](https://huggingface.co/spaces/colab-potsdam/clem-leaderboard)

The preprint is here: [arxiv.org/abs/2406.14035](https://arxiv.org/abs/2406.14035)

![Multimodal benchmark results](/images/blog/multimodal-2024-09.jpg)
