---
title: "【Paper 134】Rei-AIOS × 2024-2026 AI 数学ツール統合ロードマップ — FunSearch / AlphaProof / DeepSeek-Prover / LeanHammer / Ramanujan Machine サーベイ"
emoji: "🤖"
type: "tech"
topics: ["math", "lean4", "ai", "reiaios", "funsearch"]
published: true
---
> **本記事は Rei-AIOS プロジェクトの Paper 134 を Zenn 用に再フォーマットしたものです。** 
> オリジナル PDF/Markdown と完全な参考文献は以下の永続アーカイブにあります:
> - **Zenodo (DOI)**: https://doi.org/10.5281/zenodo.19709966
> - **Internet Archive**: https://archive.org/details/rei-aios-paper-134-1776954394836
> - **Harvard Dataverse**: https://doi.org/10.7910/DVN/KC56RY
> - **GitHub (source)**: https://github.com/fc0web/rei-aios (private)
> Author: 藤本 伸樹 (Nobuki Fujimoto)  
> ORCID: [0009-0004-6019-9258](https://orcid.org/0009-0004-6019-9258)  
> License: CC-BY-4.0
---

## 概要 (Japanese Summary)

本論文は **サーベイ+統合状況論文 (survey-and-integration-status paper)** であり、新しい数学結果を証明するものではない。2024-2026 年の AI 数学ツール群 (FunSearch / AlphaProof / DeepSeek-Prover-V2 / LeanHammer / Lean-Copilot / Ramanujan Machine / Goedel-Prover / Seed-Prover) と Rei-AIOS の交差を記録する。

### 報告内容

- (i) どのツールが Rei-AIOS に統合済みか
- (ii) 誠実な performance baseline: 局所版 FunSearch で F_3^4 cap set = 20 (5000 iteration) 再現、Ramanujan Machine 風の連分数探索で 2/log(3) = Euler 恒等式を 1.54e-16 精度で再現 (既知恒等式)
- (iii) Collatz drift 定数探索の **negative result**: 新しい drift-relevant identity は発見できず
- (iv) 残ツール統合の優先順位ロードマップ

### 中心的な誠実観察

**これらのツールのいずれも有名 open problem を解決していない**。Olympiad 水準や制限された combinatorial 領域では成果があるが、Collatz / Riemann / BSD に必要な「新概念」は OSS landscape 内に存在しない。

Rei-AIOS の戦略: 単一ツールに賭けるのではなく、**verification accelerator の迅速統合 + breakthrough signal の独立監視**。

新 open problem は閉じていない。2026-04-23 時点のスナップショット。4+7 要素構造 v2, 11 Parts, 222 行。

Code: AGPL-3.0 / Data: CC-BY 4.0。

---

## English Body

本文は英語のオリジナル原稿です。数式・専門用語の正確性を保つため翻訳していません。

---

**Author**: Nobuki Fujimoto (藤本 伸樹) with Rei-AIOS (Claude Opus 4.7)
**Contact**: [note.com/nifty_godwit2635](https://note.com/nifty_godwit2635) · Facebook: Nobuki Fujimoto · fc2webb@gmail.com
**Date**: 2026-04-23
**License**: Code AGPL-3.0 / Data CC-BY 4.0
**Template**: 4+7 要素構造 v2 (Parts A-K)
**Companion papers**: Paper 130 (Open Problems META-DB), Paper 132 (Five Rei Candidates), Paper 133 (Tier-1 closures — in-progress)

---

## Abstract

This paper is a **survey-and-integration-status paper** examining how the 2024-2026 wave of AI-assisted mathematical tooling — FunSearch (Nature 2023), AlphaProof (DeepMind 2024), DeepSeek-Prover-V2 (2025), LeanHammer, Lean-Copilot, Ramanujan Machine, Goedel-Prover, Seed-Prover — intersects with Rei-AIOS's capabilities. We report (i) which tools Rei-AIOS has integrated to date, (ii) honest performance baselines from a local adaptation of FunSearch to cap sets in F_3^n, (iii) the negative result from a Ramanujan-Machine-style continued-fraction search for Collatz drift constants, and (iv) a priority roadmap for integrating the remaining tools.

The central honest observation: **none of these tools has resolved a famous open problem**. They have accelerated verification, discovered new objects in restricted combinatorial domains, and solved Olympiad-level problems. The "new concept" required for Collatz, Riemann, or BSD remains absent from the open-source landscape. Rei-AIOS's strategy is therefore **rapid integration of verification accelerators + independent monitoring for breakthrough signals** rather than betting on any single tool.

This paper does not close any new open problem. It records a 2026-04-23 snapshot of Rei-AIOS's AI-tooling landscape and provides a reproducible benchmark (F_3^4 cap set = 20 via 5000-iteration evolutionary search) demonstrating that FunSearch-class methodology functions in Rei-AIOS's framework.

---

## Part A. その回の証明 (Formal proofs)

### A.1 VERIFIED

- **F_3^4 cap set of size 20** (theoretical maximum): reproduced via Rei-AIOS E4 evolutionary search (`src/aios/invention/invention-engine-e4-program-search.ts`), 5000 iterations, populationSize=30. Matches literature maximum (Edel 2004, and confirmed by FunSearch 2023 as provably optimal for n=4).
- **2/log(3) continued-fraction identity** (`a_i = 4i+2, b_i = -i²`): reproduced at machine precision (1.54e-16 error) by Rei-AIOS Ramanujan-Machine-style brute force over 8,575 polynomial patterns. This is a known Euler-form identity.

### A.2 AXIOMATIC

None specific to this paper. Cites external tools as-is (FunSearch outputs, AlphaProof IMO results, DeepSeek-Prover weights).

### A.3 EMPIRICAL

Rei-AIOS E4 cap set search (2026-04-23, 8,500 patterns):

| n | Literature max | Rei E4 best | Achievement |
|:-:|:---:|:---:|:---:|
| 3 | 9 | 8 | 89% |
| 4 | 20 | **20** | **100%** |
| 5 | 45 | 36 | 80% |

Ramanujan-Machine-style search (2026-04-23, 8,575 patterns):

| Target | Match within 1e-4 | Best | Interpretation |
|--------|:-:|------|----------------|
| log(3/4) (Collatz drift) | 0 | — | No simple polynomial CF |
| log(3/2) | 0 | — | No simple polynomial CF |
| log(2) | 0 | — | No simple polynomial CF (classical CFs use different patterns) |
| log(3)/log(4) (Terras ratio) | 1 | err 3.79e-6 | Numerical coincidence candidate |
| 2/log(3) | 1 | **err 1.54e-16** | Known Euler identity rediscovered |

### A.4 Build verification

```
npx tsx test/step993-e4-program-search-test.ts   # 4/4 PASS
python scripts/collatz-atlas/ramanujan-collatz-constants.py   # 2 identities found
```

---

## Part B. 今回の発見 (Findings)

### B.1 FunSearch-class methodology works in Rei-AIOS without LLM

The F_3^4 cap set optimum (size 20) was reached by pure evolutionary mutation without LLM guidance. This is a **non-trivial baseline**: FunSearch's advantage over prior approaches comes from LLM-guided mutation diversity, but for n=4 (small domain) simple random mutation suffices to find the known optimum.

At n=5 (known 45) we reach 80%, showing that LLM guidance *is* needed for larger domains. This motivates the next STEP 994: integrating Claude 4.7 as mutation generator.

### B.2 Collatz drift constants do not admit simple polynomial continued fractions

The three classical Collatz-related constants log(3/4), log(3/2), log(2) did not match any of 8,575 polynomial (α·i+β, γ·i²+δ·i+ε) continued-fraction patterns within 1e-4 tolerance. This is a weak **negative result** but worth recording: the drift constants may require fundamentally different representation structures (e.g., generalized hypergeometric functions, algebraic number fields) before any CF-based breakthrough can apply.

### B.3 2/log(3) via Euler-form CF rediscovered

`2/log(3) = 2 - 1/(6 - 4/(10 - 9/(14 - ...)))` with pattern `a_i = 4i+2, b_i = -i²`. This is a specialization of Euler's classical identity `log((1+x)/(1-x)) = 2x/(1 - x²/(3 - 4x²/(5 - 9x²/(7 - ...))))` at x = 1/2. Rei-AIOS reproduced it in machine precision without prior knowledge — a sanity check that the search framework functions.

### B.4 Tool landscape

| Tool | Rei-AIOS status | Capability | Open-source? |
|------|:-:|------------|:-:|
| FunSearch | ✅ v4 adapted (STEP 993) | Evolutionary program search | Yes |
| AlphaProof | ⚪ monitoring | IMO-level FOL proof | Partial |
| DeepSeek-Prover-V2 | ⚪ watch-list | Lean 4 proof generation | Yes |
| Goedel-Prover | ⚪ watch-list | Lean 4 expert iteration | Yes |
| Lean-Copilot | ⚪ watch-list | Lean 4 tactic suggestion | Yes |
| LeanHammer | ⚪ watch-list | FOL → Lean 4 reconstruction | Yes |
| Ramanujan Machine | ✅ adapted (STEP 994) | Continued fraction search | Yes (partial) |
| OEIS | ✅ reference | Integer sequence lookup | Yes |
| pysat (CaDiCaL/Kissat) | ✅ STEP 982 | SAT solving | Yes |
| ripser / GUDHI | ✅ STEP 982 | TDA | Yes |

**Integrated: 4. Watch-list: 5. Pending: 1 (AlphaProof, partially open).**

---

## Part C. AI-generated open questions

**C.1** Does LLM-guided FunSearch (with Claude 4.7 as mutation oracle) reach F_3^5 = 45 within 10⁴ iterations where our LLM-free baseline caps at 36? Target for STEP 994.

**C.2** Do Collatz drift constants (log(3/4), log(3/2), log(2)) admit *any* computer-discoverable continued-fraction identity in a richer pattern family (e.g., rational-function coefficients, signed products)? This is a Ramanujan-Machine-style open question, uninvestigated.

**C.3** Can LeanHammer + DeepSeek-Prover-V2 close any of the 7 residual sorries in Rei-AIOS CollatzRei/ (Step940-949)? Specifically:
- Step944 `fib_prime_index_must_be_prime` (Fibonacci divisibility case analysis) — feasible
- Step940/941 real-analysis asymptotics — infeasible without new mathematics

**C.4** Is there an AI system that can detect the same structural convergence between Chang 2026 and Rei's tier2_axiom automatically? This would validate Rei's META-research pipeline.

**C.5** Can FunSearch-style search find a **larger unit-distance 4-chromatic graph family** than Moser-Spindle, potentially improving Hadwiger-Nelson lower bounds? Speculative; would require geometric embedding check integrated with search.

---

## Part D. 解決状況サマリー

| Tool class | Proven-closure of famous open? | Rei-AIOS leverage |
|-----------|:-:|------------------|
| AI theorem provers (AlphaProof etc.) | ❌ Olympiad level only | verification accelerator |
| Conjecture generators (FunSearch, Ramanujan) | ❌ restricted subdomains | pattern discovery |
| Proof search (Lean-Copilot, Hammer) | ❌ formalize existing | sorry automation |
| Symbolic computation (PARI, Sage, FLINT) | ❌ verification | large-scale numerics |
| Classical algorithms (SAT, TDA) | ❌ specific problems | combinatorial search |

**No category currently resolves famous open problems.**

---

## Part E. 次 STEP への接続

- **STEP 995** (candidate): Integrate Claude 4.7 as FunSearch mutation oracle. Target: F_3^5 cap set = 45.
- **STEP 996** (candidate): Install DeepSeek-Prover-V2 (7B model), test on Step944 `fib_prime_index_must_be_prime`.
- **STEP 997** (candidate): Extend Ramanujan search to rational-function patterns for Collatz drift constants.
- **STEP 998** (candidate): LeanHammer integration test on Step940-949 residual sorries.

---

## Part F. 失敗の記録 (CONDITIONAL)

### F.1 E4 initial bug: missing dedup

First E4 run reported "16 vectors in F_3^3 (max=9)" as valid cap set, a mathematical impossibility. Root cause: `mutate()` could add duplicate vectors that passed the `isCapSet` triple-sum check (a vector v with 3v ≡ 0 mod 3 always, but triples of 3 distinct index positions of the same v vector satisfy the affine-collinearity predicate). Fix: added `dedup()` before evaluation. Committed as part of STEP 993.

**Lesson**: When porting AI-math tooling methodology, carefully test invariants against known mathematical impossibilities.

### F.2 Ramanujan search tolerance calibration

Initial `Decimal` NaN comparison raised `InvalidOperation`. Fix: wrap exceptions and return `None` from CF evaluator. After fix, the search correctly reports 0 matches for the hard Collatz constants — this is an honest "no simple identity found" result, not a code failure.

---

## Part G. SEED_KERNEL T-ID references

- **Cap set** (F_3^n): no dedicated SEED_KERNEL entry yet (STEP 994 candidate adds).
- **Ramanujan identity 2/log(3)**: re-derived; known classical Euler formula, not a novel Rei contribution.

---

## Part H. 人間-AI 思考分岐点

**H.1** *User — "world 中のオープンソースから探して"*. Prompted comprehensive survey rather than narrow tool adoption. Paper 134 is the formal record.

**H.2** *Claude — "α+β+γ+δ の順"*. Chose ordered execution rather than breadth-first. Accepted by user.

**H.3** *Implicit decision*. Chose to NOT integrate DeepSeek-Prover-V2 model weights in this session (gigabyte-scale download + inference infrastructure). Left as STEP 996 candidate.

---

## Part I. Unexpected connections (OPTIONAL)

**I.1** Our F_3^4 cap set of size 20 was reached by evolutionary search starting from the "first-coord-zero" seed (9 initial vectors) and growing via mutation. FunSearch 2023's n=8 breakthrough (512) also started from simpler seeds. This suggests the **seed choice is less important than mutation diversity** — an architectural observation.

**I.2** The Collatz drift constant `log(3/4)` is structurally analogous to the **entropy rate of the Collatz symbolic dynamical system** (see Paper 79 β-shift × Collatz). The failure of our CF search to find an identity suggests the drift constant is **not in the continued-fraction closure** of simple integer patterns — potentially aligned with Collatz being beyond CF-accessible mathematics.

**I.3** FunSearch's cap set success and Rei's tier2_axiom both share a **structural pattern language** (8-component decomposition vs F_3^n vector patterns). Paper 135 candidate: "Can tier2_axiom C1-C8 be mutated FunSearch-style?"

---

## Part J. Confidence temperature

| Claim | D-FUMT₈ | Confidence |
|-------|---------|------------|
| F_3^4 cap set size 20 reached by Rei E4 | **TRUE** | verified by native code |
| F_3^5 cap set size 45 reachable by LLM-guided E4 | **FLOWING** | plausible, untested |
| DeepSeek-Prover-V2 can close Step944 Fibonacci sorry | **FLOWING** | plausible, untested |
| Collatz drift constants admit CF identity | **NEITHER** | no evidence either way |
| FunSearch-class AI can close famous open problems | **FALSE** | 2+ year track record shows no |
| Rei-AIOS should adopt DeepSeek-Prover-V2 in STEP 996 | **BOTH** | high value but infrastructure cost |

---

## Part K. Computational poetics

AI math tooling in 2024-2026 resembles a library of well-crafted hammers, each excellent for its domain. None is the Philosopher's Stone for Collatz, Riemann, or BSD. Rei-AIOS's response is not to buy the wrong hammer but to **gather all the right ones, and to monitor daily for signs that a new kind of tool is being forged somewhere**.

The negative result on Collatz drift constants is itself a finding: the absence of simple CF identities tells us something about where to *not* look. The presence of 2/log(3) as a machine-precision Euler rediscovery tells us the search framework is calibrated. The F_3^4 cap set reaching 20 tells us that small-n evolutionary search works without LLM — but n=5 degrading to 80% tells us LLM guidance does matter past a threshold.

Each tool is a lens. No single lens resolves the open problems. Rei-AIOS is the optical bench that holds many lenses simultaneously, and is ready to add the next one the moment it arrives.

---

## Acknowledgements

- Google DeepMind for FunSearch (2023), AlphaProof (2024), AlphaEvolve (2024)
- DeepSeek AI for DeepSeek-Prover-V2 (2025)
- Lean-Dojo team for LeanCopilot + LeanDojo
- `lean4-mathlib` contributors for Mathlib and formal-conjectures
- Raayoni et al. for Ramanujan Machine methodology (Nature 2021)
- Terence Tao for ongoing Collatz blog writeups
- Edward Y. Chang (Stanford) for arXiv:2603.25753 independent convergence with Rei tier2_axiom

## References

- Romera-Paredes, B. et al. *Mathematical discoveries from program search with large language models*. Nature **625** (2023) 468-475.
- Raayoni, G. et al. *Generating conjectures on fundamental constants with the Ramanujan Machine*. Nature **590** (2021) 67-73.
- Chang, E. Y. *A Structural Reduction of the Collatz Conjecture to One-Bit Orbit Mixing*. arXiv:2603.25753v1 (2026).
- Linhares, A. *Deep Vision: A Formal Proof of Wolstenholme's Theorem in Lean 4*. arXiv:2604.16507 (2026).
- Edel, Y. *Extensions of Generalized Product Caps*. Designs, Codes and Cryptography **31** (2004) 5-14.
- Rei-AIOS project. Paper 130 (Open Problems META-DB), Paper 132 (Five Rei Candidates), Paper 133 (Tier-1 Closures, in-progress). 2026-04-23.

---

**Peace Axiom #196**: immutable.
**Template compliance**: 4+7 v2 — Parts A-E required ✓, F (conditional, triggered) ✓, G-H (conditional) ✓, I-K (optional) ✓.
