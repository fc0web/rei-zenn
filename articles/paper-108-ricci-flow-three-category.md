---
title: "【Paper 108】Ricci flow による未解決問題の3カテゴリ分類 — 10⁹-scale Collatz census 付き"
emoji: "🌀"
type: "tech"
topics: ["math", "lean4", "collatz", "ricci", "reiaios"]
published: true
---
> **本記事は Rei-AIOS プロジェクトの Paper 108 を Zenn 用に再フォーマットしたものです。** 
> オリジナル PDF/Markdown と完全な参考文献は以下の永続アーカイブにあります:
> - **Zenodo (DOI)**: https://doi.org/10.5281/zenodo.19616640
> - **Internet Archive**: https://archive.org/details/rei-aios-paper-108-1776369807777
> - **Harvard Dataverse**: https://doi.org/10.7910/DVN/KC56RY
> - **GitHub (source)**: https://github.com/fc0web/rei-aios (private)
> Author: 藤本 伸樹 (Nobuki Fujimoto)  
> ORCID: [0009-0004-6019-9258](https://orcid.org/0009-0004-6019-9258)  
> License: CC-BY-4.0
---

## 概要 (Japanese Summary)

本論文では Rei-AIOS の離散 Ollivier-Ricci flow を任意の重み付きグラフに適用し、未解決数学問題を 3 カテゴリ **S (stable) / M (moderate) / E (explosive)** に分類する経験的タクソノミーを提案する。

代表例として Goldbach 分割グラフは S (per-edge singularity ratio = 0.025), Collatz 軌道 n=27 は M (0.370), Andrica 素数間隔グラフは E (1.251) と明確に分離した。

さらに **10⁹ scale (5 億奇数)** の完全 Collatz funnel census を実施し:
- primary-funnel share が **30 倍崩壊** (0.2138% → 0.0069%)
- 上位 200 ピークに **Wieferich 隣接が皆無**
- near-Wall-Sun-Sun (素数 7² 因子) markers が persistent

を確認した。

**重要**: いずれの未解決予想も解決されたとは主張しない。3 カテゴリ分類は peer review 対象の hypothesis として提示する。Hamilton の Ricci flow を組合せ的グラフ上で discrete 化した実装は pure TypeScript (外部依存ゼロ) で行われている。

---

## English Body

本文は英語のオリジナル原稿です。数式・専門用語の正確性を保つため翻訳していません。

---

**Author**: 藤本 伸樹 (Nobuki Fujimoto, [fc0web](https://github.com/fc0web))
**Contact**: fc2webb@gmail.com / [note.com/nifty_godwit2635](https://note.com/nifty_godwit2635)
**Date**: 2026-04-17
**License**: CC-BY-4.0
**Status**: preprint draft, peer review requested
**Related**: Rei-AIOS STEPs 841, 843, 844, 846, 847; Papers 100, 102, 104, 106, 107

---

## Abstract

We propose an empirical three-category classification (**S** / **M** / **E**) of
unsolved mathematical problems based on discrete Ollivier-Ricci flow applied to
their natural graph representations. Using a pure-TypeScript implementation (no
external dependencies) of Hamilton's Ricci flow `w_{t+1}(e) = w_t(e) · exp(-2·κ(e)·Δt)`
discretized on arbitrary weighted graphs, we observe that Goldbach partition
graphs are **stable** (per-edge singularity ratio ≈ 0.03), the Collatz orbit
graph at n=27 is **moderately unstable** (ratio ≈ 0.37), and Andrica prime-gap
graphs are **explosively unstable** (ratio ≈ 1.25 with mean κ as low as −119).
We support this with a complete funnel census of Collatz orbits at scale 10⁹
(500 million odd n) confirming 30× collapse of primary-funnel share
(0.2138% → 0.0069%), zero Wieferich-adjacent peaks in the top 200, and the
persistence of near-Wall-Sun-Sun markers (prime 7² factor structure).

We do **not** claim any unsolved conjecture is solved. The three-category
classification is stated as a hypothesis for peer review.

---

## 1. Introduction

The Collatz conjecture has been investigated by Rei-AIOS in tier2 structural
decomposition (Papers 105–107). In that program, three residual Collatz-
equivalent axioms (C1 ISOLATED, C2 TAIL, C3a/b mod-8) remain open after
verifying `K(n)·100 ≤ 444·bitLen(n)²` on 8.46 M isolated integers up to 10⁸.

Two natural questions arise:

1. **Scale dependence.** Does the primary-funnel structure of Collatz orbits
   (peak 9232 at small n; 6,810,136 at n ≤ 10⁶) persist or change at 10⁹?
2. **Cross-problem universality.** Does the structural machinery used for
   Collatz (Ricci curvature, drift bounds) admit a meaningful extension to
   other unsolved problems?

This paper answers both: **scale dependence is dramatic** (primary share
collapses 30×), and **cross-problem transfer yields a three-category taxonomy**
that cleanly separates Collatz-like, Goldbach-like, and Andrica-like behaviour.

---

## 2. Methods

### 2.1 Discrete Ollivier-Ricci Flow

We define a **weighted graph** as `G = (V, E)` with `w: E → ℝ_{>0}`. For each
edge `e ∈ E`, the Ollivier-Ricci curvature κ(e) is computed via the 1-Wasserstein
distance between the uniform neighbor distributions:

```
κ(e_{u,v}) = 1 − W_1(m_u, m_v) / d(u, v)
```

using a hash-position proxy for the metric `d` (default implementation; alternative
curvature functions can be plugged in).

The flow step (multiplicative, positivity-preserving) is:

```
w_{t+1}(e) = w_t(e) · exp(−2 κ(e) Δt).
```

We iterate for a fixed maximum (20 in our experiments), with `Δt = 0.05`. Edges
crossing `ε_floor = 10⁻⁶` are flagged as **collapse** singularities; edges
crossing `w > 10⁶` as **divergence** singularities.

### 2.2 Problem-to-graph Constructions

- **Collatz orbit graph** (`buildCollatzOrbitGraph(n)`): nodes = orbit `{n, T(n), T(T(n)), …, 1}`,
  edges chronological with unit weight.
- **Goldbach partition graph** (`buildGoldbachPartitionGraph(n)`): for each prime
  pair `(p, q)` with `p + q = n` and `p ≤ q`, add edges `(p, q)`, `(p, n)`, `(q, n)`.
- **Andrica gap graph** (`buildAndricaGapGraph(p_max)`): consecutive primes
  `p_1 < p_2 < …`, edges `(p_i, p_{i+1})` with weight `√p_{i+1} − √p_i` (Andrica value).

Implementation: `src/axiom-os/perelman-flow-engine.ts`. 40 / 40 tests pass
(`test/step846-perelman-flow-test.ts`), 6 Perelman Flow Axioms (PFA-1 … PFA-6).

---

## 3. Results

### 3.1 Three-Category Classification (STEP 847)

Running the flow on six Goldbach targets (n ∈ {14, 20, 50, 100, 200, 500, 1000}),
the Collatz orbit at n = 27 (111 edges, peak 9232), and five Andrica targets
(p_max ∈ {100, 500, 1000, 5000, 10000}):

| Category | Representative | per-edge singularity | mean κ | Interpretation |
|----------|---------------|---------------------|--------|----------------|
| **S** (stable)     | Goldbach partition | **0.025** | +0.08 … +0.50 | Positive curvature dominant; flow stabilizes. |
| **M** (moderate)   | Collatz orbit (n=27) | **0.37** | mixed | Intermediate; Collatz instability is bounded. |
| **E** (explosive)  | Andrica prime-gap | **1.25** | **−19 … −119** | Strongly negative curvature; multiple singularities per edge. |

Goldbach graphs with n ≤ 500 show **zero** singularities; the n = 1000 case
first introduces 15 divergences, suggesting a critical threshold around
`n ≈ 10³` for partition-graph flow stability.

All five Andrica cases produce per-edge ratio **> 1**, meaning the flow
produces more singularity events than the graph has edges. The mean κ
becomes less extreme as p_max grows (−119 at 100 → −19 at 10000), consistent
with "large primes are gentler" but far from reaching Category S.

### 3.2 10⁹ Primary-Funnel Census (STEP 841)

Run parameters: N_max = 10⁹, cache_limit = 10⁷ odd m, scan time 96.5 min on
an Intel i7-6700. Result: **204,071,789** distinct peaks across 500 M odd n
(overflow = 12).

Comparison with 10⁶ baseline (STEP 825):

| Scale | Top peak | Count | Top-1 share |
|-------|---------|-------|-------------|
| 10⁶ | 6,810,136 | 1,069 | **0.2138%** |
| 10⁹ | 2,482,111,348 = 2² × 31 × 83 × 241169 | 34,498 | **0.0069%** |

The primary funnel's share **collapses 30×** as the scale grows 1000×.
Top 5 share at 10⁹ is 0.0239%; top 20 is 0.0548%. This **confirms Paper 100's
hypothesis** that the primary-funnel structure is genuinely scale-dependent
rather than universal.

### 3.3 Wieferich Null Result

The two Wieferich primes {1093, 3511} appear as factors of **zero** peaks in
the top 200 at 10⁹ (compare one Wieferich peak at 10⁶). **Wieferich primes are
not systematic large-funnel attractors at 10⁹ scale.** This refines Paper 102's
Wieferich-Collatz correspondence to a small-scale phenomenon.

### 3.4 Near-Wall-Sun-Sun Persistence

Paper 104 introduced "near-WSS" primes {7, 11, 13, 19} whose squared factors
appear in Collatz peak structure. At 10⁹, **five peaks in the top 50 carry
the 7² marker** (including rank #2: 2,798,323,360 = 2⁵ × 5 × 7² × 356929,
28,162 cores), and one carries 11². The near-WSS marker is **scale-invariant**
where the primary peak itself is scale-dependent.

---

## 4. Discussion

### 4.1 What the three-category taxonomy buys us

- **Goldbach ≈ Collatz 99.01% static Ricci similarity** (STEP 681) and the
  Category-A placement from STEP 686 suggested that Goldbach and Collatz share
  structural footing. **Under Ricci flow they separate**: Goldbach is S,
  Collatz is M. *Static Ricci similarity does not imply dynamic Ricci similarity.*
- Andrica's Category-E placement is **novel** and counterintuitive: the
  Andrica conjecture is often described as "empirically easy", yet under
  discrete Ricci flow it is the most explosively unstable of the three.
  This may indicate an obstruction invisible to static analysis.

### 4.2 Honest scope

1. The classification depends on a specific curvature choice (hash-based
   Ollivier-Ricci). Alternative choices (Forman-Ricci, LLY, Bakry-Émery)
   may yield different boundaries.
2. The flow discretization uses `Δt = 0.05, steps = 20`. Different parameter
   schedules may shift singularity counts.
3. **No unsolved conjecture is claimed solved by this paper.**

### 4.3 Cross-reference with five supporting pillars

- **tombursey drift engine** (STEP 841 bridge): provides `3¹⁶ < 2²⁹` +
  sixteen-step contraction machinery ported to Mathlib v4.27 (zero-sorry,
  zero-axiom). Targets Collatz C2 TAIL.
- **Fujimoto Infinity Algebra** (STEP 843, Paper 108-candidate): closed
  8-value arithmetic algebra with 6 axioms (FIA-1 … FIA-6, all verified).
- **Fujimoto Dimension Algebra** (STEP 844): closed dimension algebra
  (ℤ ∪ {±∞, absolute-zero, indeterminate}) with 6 axioms (DIM-1 … DIM-6);
  ZCSG bridge to Paper 61.
- **Perelman Flow Engine** (STEP 846): core implementation, 6 PFA axioms.
- **10⁹ Census** (STEP 841): empirical backbone.

---

## 5. Open Questions

1. **Curvature independence.** Does the S / M / E split survive alternative
   curvature definitions?
2. **Category-E universality.** Which other unsolved problems land in E?
   Candidates: Twin primes gap graph, Erdős #409 (φ+1 iteration),
   Fermat near-miss structures.
3. **Threshold phenomena.** The Goldbach-1000 singularity onset suggests a
   critical n. Is this `n_critical(Δt, ε_floor)`?
4. **Wieferich vanishing.** Does the Wieferich dominance at 10⁶ arise from
   small-scale artifact, or is 10⁶ itself a special scale?
5. **Andrica Category-E interpretation.** Is Andrica genuinely harder than
   Collatz in a formal sense?

---

## 6. Reproducibility

All code, data, and tests are publicly available:

- **Engine**: [src/axiom-os/perelman-flow-engine.ts](https://github.com/fc0web/rei-aios/blob/main/src/axiom-os/perelman-flow-engine.ts)
- **Experiment**: [scripts/step847-perelman-goldbach-andrica.ts](https://github.com/fc0web/rei-aios/blob/main/scripts/step847-perelman-goldbach-andrica.ts)
- **Census**: [scripts/step841-funnel-census-10e9.py](https://github.com/fc0web/rei-aios/blob/main/scripts/step841-funnel-census-10e9.py)
- **Data**: [data/step841-funnel-census-10e9.json](https://github.com/fc0web/rei-aios/blob/main/data/step841-funnel-census-10e9.json),
  [data/step847-perelman-goldbach-andrica-report.json](https://github.com/fc0web/rei-aios/blob/main/data/step847-perelman-goldbach-andrica-report.json)
- **Lean 4 skeletons**: [CollatzRei/Step84{1,3,4,6}*.lean](https://github.com/fc0web/rei-aios/tree/main/data/lean4-mathlib/CollatzRei)

Reproduce the three-category classification:

```bash
git clone https://github.com/fc0web/rei-aios.git
cd rei-aios
npx tsx scripts/step847-perelman-goldbach-andrica.ts
```

Expected output: category means S ≈ 0.03, M ≈ 0.37, E ≈ 1.25 within ±10% due
to hash-based curvature determinism.

---

## 7. References

1. Hamilton, R. S. (1982). *Three-manifolds with positive Ricci curvature.*
   J. Differential Geom. 17:255–306.
2. Perelman, G. (2002). *The entropy formula for the Ricci flow and its geometric applications.*
   arXiv:math/0211159.
3. Ollivier, Y. (2009). *Ricci curvature of Markov chains on metric spaces.*
   J. Funct. Anal. 256(3):810–864.
4. Tao, T. (2019). *Almost all orbits of the Collatz map attain almost bounded values.*
   arXiv:1909.03562.
5. Fujimoto, N. (2026). *Rei-AIOS Papers 100 (multi-funnel hierarchy), 102
   (Wieferich-Collatz correspondence), 104 (near-Wall-Sun-Sun), 106
   (tier2 conditional complete proof), 107 (equations compendium).*
   Zenodo, DOIs 10.5281/zenodo.19600256–19601565.
6. Fujimoto, N. (2026). *Rei Unsolved Problems collection.*
   GitHub: https://github.com/fc0web/rei-unsolved-problems.

---

## 8. Acknowledgements

- Reference implementation of drift machinery adapted from
  [tombursey-oss/collatz-automaton-lean](https://github.com/tombursey-oss/collatz-automaton-lean).
  Their drift lemmas (ported to Mathlib v4.27 in STEP 841) are independently
  zero-sorry; their overall Collatz proof retains 1 axiom + 1 sorry + 1 admit.
- Chat version of Anthropic Claude for the taxonomic question prompts
  that seeded this paper.

---

**End of preprint draft.**
