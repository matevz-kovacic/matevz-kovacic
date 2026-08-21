# Matevž Kovačič

Software engineer and researcher building **[Active Model](https://github.com/matevz-kovacic/active-model)** — an autonomous research system for difficult optimization, algorithmic search, and systems-performance problems.

Active Model starts from a task, evaluator, and verification criteria, then autonomously investigates the problem, forms and tests hypotheses, implements candidates, and verifies results.

## Systems optimization

Recent Active Model work targets mature, heavily optimized open-source software.

* **llama.cpp — [ggml-org/llama.cpp#27478](https://github.com/ggml-org/llama.cpp/pull/27478), submitted upstream**
  Reworked batch-1 CPU flash-attention decode and large-allocation handling. On **Qwen3-30B-A3B Q4_K_M at 8192-token context**, measured end-to-end token-generation throughput improves **+15.29% on AMD Zen 5** and **+9.22% on ARM Neoverse-N1**. The attention optimization alone contributes **+10.67%** and **+7.43%**, respectively.

* **zstd — three optimization PRs submitted upstream**

  * [facebook/zstd#4729](https://github.com/facebook/zstd/pull/4729) — submitted, under review
  * [facebook/zstd#4732](https://github.com/facebook/zstd/pull/4732) — submitted, under review
  * [facebook/zstd#4733](https://github.com/facebook/zstd/pull/4733) — removes a loop-carried memory dependency from the decompression hot loop by keeping repeat-offset state in registers. Measured decode-throughput improvement is **+2.7–3.4% with GCC and +5.5–9.3% with Clang on Zen 5**, with the same direction of improvement on Intel Raptor Lake.

* **dav1d (VideoLAN / FFmpeg / Alliance for Open Media) — two AV1 decoder optimizations prepared for upstream submission.** One eliminates an unnecessary compound-prediction scratch-buffer round trip, reaching **+2.79% whole-decoder throughput on x86** and **+1.73% on real ARM/Neoverse-N1 hardware**, while removing **6–8% of decoder cache references** on representative streams. A second exact transformation removes **77.5% of redundant temporal-MV candidate processing**, measuring about **+0.5–0.8%** whole-decoder improvement across x86 and ARM. Both are validated against **240/240 AOMedia AV1 conformance vectors**.

## Mathematical and computational results

* **Solved the English perfect 10-square problem, open for more than 120 years**, producing the first proper English 10-square.
  [Code and result](https://github.com/matevz-kovacic/word-square) · [History of the problem](https://en.wikipedia.org/wiki/Word_square)

* **Improved on results reported by Google DeepMind’s AlphaEvolve on two packing problems**, with both new best-known solutions verified using **AlphaEvolve’s own published verifier**:

  * 32 variable-radius circles in a unit square
  * 21 variable-radius circles in a perimeter-4 rectangle
    [Verified Active Model results](https://github.com/matevz-kovacic/active-model)

* Produced additional best-known numerical results in **circle packing and spherical codes**, and a large-scale **AC optimal-power-flow** result accepted into MINLPLib.

## Active Model

**[Active Model](https://github.com/matevz-kovacic/active-model)** explores whether frontier models can function as autonomous computational researchers rather than only as coding assistants.

The system is built around externally checkable objectives: exact verifiers where possible, reproducible benchmarks for systems work, and explicit acceptance criteria.

Current experiments span mathematical optimization, algorithm discovery, and performance engineering in production C/C++ software.

## Interests

Frontier-model research engineering · autonomous scientific discovery · inference and systems optimization · program analysis · combinatorial and numerical optimization · foundational software

I am interested in research-engineering roles and collaborations involving autonomous research systems, model-driven scientific discovery, and high-performance software.

## Contact

📫 **[matevz.celje@gmail.com](mailto:matevz.celje@gmail.com)**


