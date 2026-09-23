# Matevž Kovačič

I build and experiment with AI systems that do **iterative technical research**: forming hypotheses, writing implementations, running experiments, analyzing failures, and optimizing against external evaluators.

My current project is [Active Model](https://github.com/matevz-kovacic/active-model), an experimental research system built around that loop.

## Selected results

### 🥇 NVIDIA SOL-ExecBench — #1 on two B200 kernels

Two independent **#1 results on NVIDIA's official SOL-ExecBench leaderboards**, evaluated on NVIDIA B200 hardware.

#### Kernel 049 — #1 on B200

Active Model first optimized **SOL-ExecBench kernel 049** and independently produced two candidate kernels whose measured performance would have placed them **#2 on the public leaderboard at the time**. I did not publish either result.

The remaining gap was difficult: the existing #1 was a strong solution that the initial campaign could not crack. I therefore added an external reasoning loop around Active Model.

I repeatedly pasted the current best Active Model solution and its measurements into **ChatGPT, using Astra at maximum reasoning effort**, and asked for new candidate architectures, variations, and optimization directions. I then passed those proposals back into **Active Model**, which converted them into actual kernel implementations, ran them on B200, measured them, analyzed the results, and continued the search.

The loop was repeated several times:

> **Active Model kernel → B200 measurements → ChatGPT/Astra research proposals → Active Model implementation and experimentation → new best kernel**

That iterative model-to-model research loop eventually broke through the existing #1 and produced the kernel that now holds **#1 on NVIDIA's official B200 leaderboard**.

[Leaderboard](https://research.nvidia.com/benchmarks/sol-execbench/leaderboard/kernel/49/B200) · [Full campaign writeup](https://github.com/matevz-kovacic/active-model/tree/main/sol-execbench-049/README.md)

**Autonomy boundary.** Active Model independently reached approximately #2-level performance before external steering. Throughout the subsequent campaign, Active Model remained the implementation and experimental engine: it produced the actual kernels, executed the benchmarks, interpreted measurements, and incorporated successful ideas. ChatGPT/Astra was used between rounds as an external research adviser to propose new directions from the current solution and measured evidence. I orchestrated the exchange between the two systems.

The implementation is currently withheld while the benchmark remains competitive; the leaderboard result is NVIDIA's measurement.

#### Kernel 094 — #1 on B200 — reached, lost, retaken

Active Model holds **#1 on NVIDIA SOL-ExecBench kernel 094 (`time_decay_exponential_stabilization`)** with a **0.999092 SOL score** on NVIDIA B200, ahead of submissions from SF Tensor, doubleAI and Databricks.

[Leaderboard](https://research.nvidia.com/benchmarks/sol-execbench/leaderboard/kernel/94/B200) · [Full campaign writeup](https://github.com/matevz-kovacic/active-model/blob/main/sol-execbench-094/README.md)

**Autonomy boundary.** Active Model produced every implementation, experiment, measurement and attribution in this campaign. A human research lead set strategy and, after the first measured round, named specific techniques to try. The model implemented and adjudicated 13 such proposals against its own measurements — adopting 3 and refuting 10 with identified mechanisms — and independently found the largest single discrepancy of the campaign: a reproducibility discrepancy inherited from prior work, traced to its underlying mechanism.

> **The first 4 autonomous hours reached a locally measured ≈#8; model-generated engineering under human research direction reached #1.**

The first #1 (0.998647) was overtaken days later by another participant at 0.999005. A second campaign, started from the current kernel with the first campaign's work as read-only input, produced on its own a substantially different kernel architecture that overcame a limitation the first campaign had treated as fundamental and retook the lead on its first official measurement, and three rounds of written review widened the margin to **+87 ppm** over the participant who had overtaken it: 43 B200 rentals, 12.2 GPU-hours, $45, reproduced across four official evaluations. While the benchmark remains contested, the techniques are withheld; the result is NVIDIA's measurement.

## Production systems optimization

* **llama.cpp** — [PR #27478](https://github.com/ggml-org/llama.cpp/pull/27478) *(open)*: "ggml : speed up batch-1 CPU decode, align large allocations". Up to **+15.29%** end-to-end token-generation throughput on Ryzen 7 9700X (attention change alone +10.67%) and **+9.22%** on Neoverse-N1, measured on Qwen3-30B-A3B Q4_K_M at 8192-token context.
* **zstd** — three optimization PRs on encode/decode hot paths submitted upstream: [#4729](https://github.com/facebook/zstd/pull/4729) · [#4732](https://github.com/facebook/zstd/pull/4732) · [#4733](https://github.com/facebook/zstd/pull/4733). Includes a decompression-hot-loop optimization removing a loop-carried memory dependency, improving decode throughput by **+2.7–3.4%** with GCC and **+5.5–9.3%** with Clang on Zen 5, with the same direction on Intel Raptor Lake.

* **dav1d** — two AV1 decoder optimizations contributed upstream. [!1967 *refmvs: collapse runs of identical temporal MVs*](https://code.videolan.org/videolan/dav1d/-/merge_requests/1967), **merged September 23, 2026**: **+0.5–0.8%** overall decode performance across x86-64 and AArch64, up to **+2.96%** on favorable content. [!1968 *mc: avg_direct for full-pel compound blocks*](https://code.videolan.org/videolan/dav1d/-/merge_requests/1968), submitted upstream: **+0.9–2.8%** decode performance depending on architecture and existing SIMD coverage. Both preserve bit-identical decoded output.

## Algorithmic and mathematical results

* Solved the English perfect **10-square**, a problem open for more than 120 years — [repository](https://github.com/matevz-kovacic/word-square) · [problem history](https://en.wikipedia.org/wiki/Word_square).
* Improved published **Google DeepMind AlphaEvolve** results on packing problems using the published verifier.
* New best-known numerical results in circle packing and spherical codes (S⁵, N=86 and N=98, registered with spherical-codes.org).
* Improved the published primal for the 13,659-bus European Pegase AC optimal-power-flow benchmark; accepted into MINLPLib.

## Biomedical work

* **WA** — [phenotype-driven gene prioritization](https://github.com/matevz-kovacic/WA): a Bayesian diagnostic model that ranks candidate disease genes from patient phenotypes alone, using the Human Phenotype Ontology. Preprint included in the repository.

## What I am investigating

> **How far can frontier models go when given a real objective, an evaluator, tools, compute, and enough freedom to conduct experiments?**

Interests: **autonomous research · AI for systems · model self-improvement · GPU/CPU optimization · LLM training and inference · algorithm discovery · verifier-guided search**

I am also interested in applying the same verifier-guided search approach to **rare-disease diagnostics and drug discovery** — problem classes with concrete objectives, external validation, and search spaces far too large to explore by hand.

I am open to **research-engineering and research roles at frontier-model labs** where this kind of work is relevant.

## Contact

[matevz.celje@gmail.com](mailto:matevz.celje@gmail.com)
