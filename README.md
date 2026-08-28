# Matevž Kovačič

Software engineer and researcher building [**Active Model**](https://github.com/matevz-kovacic/active-model) — an autonomous research system for optimization, algorithmic search, and systems-performance problems.

Active Model starts from a task, evaluator, and verification criteria, then investigates the problem, forms and tests hypotheses, implements candidates, and verifies results.

## Systems optimization

Recent work applies Active Model to mature, heavily optimized production software.

* **llama.cpp — [PR #27478](https://github.com/ggml-org/llama.cpp/pull/27478)**
  Reworked batch-1 CPU flash-attention decode and large-allocation handling. On **Qwen3-30B-A3B Q4_K_M at 8192-token context**, end-to-end token-generation throughput improves **+15.29% on AMD Zen 5** and **+9.22% on ARM Neoverse-N1**. The attention optimization alone contributes **+10.67%** and **+7.43%**.

* **zstd — three optimization PRs submitted upstream**
  [#4729](https://github.com/facebook/zstd/pull/4729) · [#4732](https://github.com/facebook/zstd/pull/4732) · [#4733](https://github.com/facebook/zstd/pull/4733)
  Includes a decompression-hot-loop optimization removing a loop-carried memory dependency, improving decode throughput by **+2.7–3.4% with GCC and +5.5–9.3% with Clang on Zen 5**, with the same direction on Intel Raptor Lake.

* **dav1d — two AV1 decoder optimizations submitted upstream**
  [!1968](https://code.videolan.org/videolan/dav1d/-/merge_requests/1968) · [!1967](https://code.videolan.org/videolan/dav1d/-/merge_requests/1967)
  The first removes an unnecessary compound-prediction scratch-buffer round trip: **+0.97%** whole-decoder throughput on Intel Raptor Lake, **+1.73%** on ARM Neoverse-N1, and up to **+2.79%** on the SSE2 dispatch path, where the kernels it deletes are slowest. The second is an exact transformation removing **77.5% of redundant temporal-MV candidate processing**, worth **+0.68%** on Raptor Lake and **+0.78%** on Neoverse-N1. Every figure is a 12-stream geometric mean against an A/A noise floor measured on that machine. Both are bit-exact against upstream output and pass **240/240 AOMedia AV1 conformance vectors**; both pipelines pass VideoLAN CI.

  
  

## Mathematical and computational results

* **Solved the English perfect 10-square problem**, open for more than 120 years.
  [Code and result](https://github.com/matevz-kovacic/word-square) · [History](https://en.wikipedia.org/wiki/Word_square)

* **Improved on Google DeepMind AlphaEvolve results on two packing problems**, verified using AlphaEvolve’s published verifier:

  * 32 variable-radius circles in a unit square
  * 21 variable-radius circles in a perimeter-4 rectangle

* Produced additional best-known results in **circle packing and spherical codes**, and a large-scale **AC optimal-power-flow** result accepted into MINLPLib.

## Active Model

[**Active Model**](https://github.com/matevz-kovacic/active-model) explores whether frontier models can operate as autonomous computational researchers rather than only as coding assistants.

Its core principle is simple:

> **Use externally checkable objectives, explicit verification, and repeated hypothesis → implementation → measurement loops to search for real improvements.**

Current work spans mathematical optimization, algorithm discovery, and performance engineering in production C/C++ software.

## Interests

AI-assisted systems optimization · inference performance · autonomous research systems · program analysis · combinatorial and numerical optimization · scientific discovery

I am interested in **research-engineering roles, collaborations, and technology-transfer opportunities** involving autonomous optimization, high-performance software, and AI-for-systems.

## Contact

[matevz.celje@gmail.com](mailto:matevz.celje@gmail.com)


