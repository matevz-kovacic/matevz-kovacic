# Matevž Kovačič

I build and experiment with AI systems that do **iterative technical research**: forming hypotheses, writing implementations, running experiments, analyzing failures, and optimizing against external evaluators.

My current project is [Active Model](https://github.com/matevz-kovacic/active-model), an experimental research system built around that loop.

## Selected results

### 🥇 NVIDIA SOL-ExecBench — reached #1 on B200

Active Model reached **#1 on NVIDIA SOL-ExecBench kernel 094 (`time_decay_exponential_stabilization`)** with a **0.998564 SOL score** on NVIDIA B200, ahead of submissions from doubleAI, Databricks and SF Tensor.

[Leaderboard](https://research.nvidia.com/benchmarks/sol-execbench/leaderboard/kernel/94/B200) 

**Autonomy boundary.** Active Model produced every implementation, experiment, measurement and attribution in this campaign. A human research lead set strategy and, in the final optimization rounds, named specific techniques to try. The model implemented and adjudicated them against its own measurements — adopting three, refuting four others with identified mechanisms — and independently found both the largest single defect (a compiler-flag regression costing ~1.6× on the hot path) and the profiling result that explained the remaining gap.

> **Autonomous search reached ≈#8; model-generated engineering under human research direction reached #1.**

### modded-nanogpt — autonomous 8×H100 LLM-training optimization

[PR #358](https://github.com/KellerJordan/modded-nanogpt/pull/358) *(open)*

From a **single high-level prompt**, Active Model independently selected optimization targets, wrote the patches, and ran the experiments.

Result: **−0.729 s mean** versus the previous Track 1 implementation in paired same-machine measurements across two independent **8×H100** leases, clearing the measured noise floor by 6.0× and 8.7× (mean val loss 3.27886, p = 0.0014 over 20 runs).

This experiment is particularly useful to me because the optimization target is the training loop of an actual language model rather than a synthetic benchmark.

## Other systems work

* **llama.cpp** — [PR #27478](https://github.com/ggml-org/llama.cpp/pull/27478) *(open)*: "speed up batch-1 CPU decode, align large allocations" — up to **+15.29%** end-to-end token-generation throughput (Ryzen 7 9700X; +9.22% on Neoverse-N1).
* **zstd — three optimization PRs on encode/decode hot paths submitted upstream**
  [#4729](https://github.com/facebook/zstd/pull/4729) · [#4732](https://github.com/facebook/zstd/pull/4732) · [#4733](https://github.com/facebook/zstd/pull/4733)
  Includes a decompression-hot-loop optimization removing a loop-carried memory dependency, improving decode throughput by **+2.7–3.4% with GCC and +5.5–9.3% with Clang on Zen 5**, with the same direction on Intel Raptor Lake.
* **dav1d** — AV1 decoder optimization: [MR !1967](https://code.videolan.org/videolan/dav1d/-/merge_requests/1967) · [MR !1968](https://code.videolan.org/videolan/dav1d/-/merge_requests/1968).
* Additional low-level optimization experiments across CPU and GPU workloads.

## Algorithmic and mathematical results

* Solved the English perfect **10-square**, a problem open for more than 120 years — [repository](https://github.com/matevz-kovacic/word-square) · [problem history](https://en.wikipedia.org/wiki/Word_square).
* Improved published **Google DeepMind AlphaEvolve** results on packing problems using the published verifier.
* New best-known numerical results in circle packing and spherical codes (S⁵, N=86 and N=98, registered with spherical-codes.org).
* Improved the published primal for the 13,659-bus European Pegase AC optimal-power-flow benchmark; accepted into MINLPLib.

## What I am investigating

> **How far can frontier models go when given a real objective, an evaluator, tools, compute, and enough freedom to conduct experiments?**

Interests: **autonomous research · AI for systems · model self-improvement · GPU/CPU optimization · LLM training and inference · algorithm discovery · verifier-guided search**

I am open to **research-engineering and research roles at frontier-model labs** where this kind of work is relevant.

## Contact

[matevz.celje@gmail.com](mailto:matevz.celje@gmail.com)
