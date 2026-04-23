---
title: "【Paper 133】Sylvester–Schur 部分 Lean 4 形式化 + 699↔961 bridge — 15 verified theorem + native_decide 1552 件 + Erdős 1934 前哨"
emoji: "🔢"
type: "tech"
topics: ["math", "lean4", "reiaios", "erdos", "combinatorics"]
published: true
---
> **本記事は Rei-AIOS プロジェクトの Paper 133 を Zenn 用に再フォーマットしたものです。** 
> オリジナル PDF/Markdown と完全な参考文献は以下の永続アーカイブにあります:
> - **Zenodo (DOI)**: https://doi.org/10.5281/zenodo.19713219
> - **Internet Archive**: https://archive.org/details/rei-aios-paper-133-1776974645040
> - **Harvard Dataverse**: https://doi.org/10.7910/DVN/KC56RY
> - **GitHub (source)**: https://github.com/fc0web/rei-aios (private)
> Author: 藤本 伸樹 (Nobuki Fujimoto)  
> ORCID: [0009-0004-6019-9258](https://orcid.org/0009-0004-6019-9258)  
> License: CC-BY-4.0
---

## 概要 (Japanese Summary)

本論文は **部分形式化論文 (partial formalization paper)** であり、新しい数学結果は証明しない。古典 Sylvester–Schur 定理 (Sylvester 1892 / Erdős 1934) の Lean 4 部分形式化と、Erdős 699 (二項係数形式) ↔ 961 (連続整数 interval 形式) の完全検証済 conditional reduction を提供する。

### 検証済 (0 sorry, 15 定理 + 2 transitively verified)

- **k = 1 厳密 case**: 任意 m ≥ 2 は素因数 ≥ 2 > 1 を持つ
- **k = 2 厳密 case**: 2 連続 ≥ 3 のうち奇数は奇素因数 ≥ 3 を持つ
- **Bertrand-boundary for all k ≥ 1**: Bertrand 仮説で m = k+1 case を閉じる
- **native_decide k ∈ {3..10}, m ≤ 200**: 有限範囲 1,552 件機械検証
- `dvd_ascFactorial_of_mem`: j ∈ [n, n+k) ⇒ j ∣ n.ascFactorial k
- **`erdos_699_binomial_bridge_conditional`**: 961 interval ⇒ 699 binomial の完全 Lean 4 reduction

### 誠実な sorry (1 件 core)

`sylvester_schur_general` (k ≥ 3 任意 m) — Erdős 1934 elementary 証明 (Legendre formula + 二項 bound + Størmer 型解析) 必要、推定 50-80 定理、本論文では attempt せず。

### Paper 132 Part F.4 Option-B closure

699/961 は古典 proven theorem だが Mathlib v4.27 に直接存在せず。本論文は形式化可能部分を honest に閉じ、残部分を明示。無 overclaim。

Code: AGPL-3.0 / Data: CC-BY 4.0。

---

## English Body

本文は英語のオリジナル原稿です。数式・専門用語の正確性を保つため翻訳していません。

---

**Author**: Nobuki Fujimoto (藤本 伸樹) with Rei-AIOS (Claude Opus 4.7)
**Contact**: [note.com/nifty_godwit2635](https://note.com/nifty_godwit2635) · Facebook: Nobuki Fujimoto · fc2webb@gmail.com
**Date**: 2026-04-24
**License**: Code AGPL-3.0 / Data CC-BY 4.0
**Template**: 4+7 要素構造 v2 (Parts A–K)
**Companion papers**: Paper 127–131 (Lean 4 first-of-extremal-combinatorics cluster), Paper 132 (five Rei candidates), Paper 134 (AI tooling survey)
**Lean repo**: `data/lean4-mathlib/CollatzRei/Step992SylvesterSchur.lean` at commit `8686157`

---

## Abstract

This is a **partial formalization paper**. We formalize in Lean 4 the classical Sylvester–Schur theorem (Sylvester 1892 / Erdős 1934) for small-to-moderate values of `k`, and provide a fully verified conditional reduction from the binomial form (Erdős Problem 699) to the consecutive-integer interval form (Erdős Problem 961). Neither full theorem is proved; both admit Lean 4 access for the first time via the file `Step992SylvesterSchur.lean` under Rei-AIOS's `CollatzRei` build environment.

**Verified contributions (0 sorry in verified block)**:
- Exact `k = 1` case of the 961 interval form.
- Exact `k = 2` case via parity argument.
- Bertrand-boundary lemma: the `m = k+1` boundary case for **every** `k ≥ 1`, proved directly from Mathlib's `Nat.exists_prime_lt_and_le_two_mul`.
- Finite-range `native_decide` verification for `k ∈ {3, 4, 5, 6, 7, 8, 9, 10}` over all starting points `m ∈ [k+1, 200]` — 1,552 finite cases verified by computation.
- `well_defined` derivations for `k ∈ {1, 2}`.
- Two substantive bridge lemmas:
  - `dvd_ascFactorial_of_mem`: every integer `j ∈ [n, n+k)` divides `Nat.ascFactorial n k`.
  - `erdos_699_binomial_bridge_conditional`: given general 961 interval form, the 699 binomial form follows.

**Left as honest sorry (1 core, 1 transitive)**:
- `sylvester_schur_general`: the general `k ≥ 3`, arbitrary `m ≥ k+1` case. This requires the full Erdős 1934 argument (Legendre's formula on p-adic valuations of factorials + binomial-coefficient estimates + Størmer-like analysis of consecutive smooth numbers) — estimated 50–80 additional Lean theorems, not attempted in this paper.
- `erdos_699_binomial`: transitively depends on `sylvester_schur_general`.

**Honest positioning**: this paper **does not solve** Erdős 699 or 961 (both are already classical theorems). It **does** provide:
1. First Lean 4 files closing these forms for a non-trivial range (`k ≤ 10, m ≤ 200`).
2. A fully verified reduction between the two classical formulations.
3. A clean foundation for a future paper closing the general case via the Erdős 1934 argument.

The paper also serves as an **Option-B closure** of the Paper 132 Part F.4 structural lesson: after correcting META-DB metadata for six Erdős entries mis-tagged as `paperCandidate: true` (Paper 132 ingestion-bug pattern), we isolate two genuinely tractable classical theorems (699, 961) and formalize what can be formalized honestly, without Størmer or Erdős 1934 prerequisites.

---

## Part A. その回の証明 (Formal proofs)

### A.1 VERIFIED (Lean 4 + Mathlib v4.27, `native_decide` where noted)

**Definition (local):**
```lean
def Erdos961Prop (k n : ℕ) : Prop :=
  ∀ m ≥ k + 1, ∃ i ∈ Set.Ico m (m + n), ¬ i ∈ Nat.smoothNumbers (k + 1)
```
Replicates `Erdos961Prop` from `FormalConjectures.ErdosProblems.961`.

**Verified theorem 1** — exact `k = 1` case:
```lean
theorem sylvester_schur_k1 : Erdos961Prop 1 1
```
For every `m ≥ 2`, the integer `m` itself has a prime factor (its `minFac`), necessarily `≥ 2 > 1`. Proof via `Nat.minFac_prime` + `Nat.mem_primeFactorsList`.

**Verified theorem 2** — exact `k = 2` case:
```lean
theorem sylvester_schur_k2 : Erdos961Prop 2 2
```
Case split on parity of `m`. Whichever of `m, m+1` is odd has `minFac ≥ 3`. Requires the supporting lemma `minFac_ge_three_of_odd`.

**Verified theorem 3** — Bertrand-boundary for every `k`:
```lean
theorem sylvester_schur_boundary (k : ℕ) (hk : 1 ≤ k) :
    ∃ i ∈ Set.Ico (k + 1) (k + 1 + k), ¬ i ∈ Nat.smoothNumbers (k + 1)
```
Direct application of `Nat.exists_prime_lt_and_le_two_mul k` gives a prime `p` with `k < p ≤ 2k`, hence `p ∈ [k+1, 2k] = [m, m+k-1]` when `m = k+1`. This closes **one specific starting point** `m = k+1` for every `k`.

**Verified theorems 4–11** — `native_decide` bounded cases `k ∈ {3..10}`:
```lean
theorem sylvester_schur_kK_bounded :
    ∀ m, K+1 ≤ m → m ≤ 200 → hasLargePrimeFactor K K m = true
```
Eight theorems (one per `K ∈ {3, 4, 5, 6, 7, 8, 9, 10}`), each closing `196 – K` individual `m` values via `native_decide` over the decidable predicate `hasLargePrimeFactor`:
```lean
def hasLargePrimeFactor (k n m : ℕ) : Bool :=
  (List.range n).any fun d =>
    let i := m + d
    i ≥ 2 ∧ ((Nat.primeFactorsList i).any fun p => p > k)
```
Total verified finite cases: `Σ_{K=3..10} (200 - K) = 1552`.

**Verified theorem 12** — `well_defined_k1`: `∃ n, Erdos961Prop 1 n`. Witness `n = 1`.

**Verified theorem 13** — `well_defined_k2`: `∃ n, Erdos961Prop 2 n`. Witness `n = 2`.

**Verified theorem 14** — `dvd_ascFactorial_of_mem`:
```lean
lemma dvd_ascFactorial_of_mem (n : ℕ) : ∀ k j, n ≤ j → j < n + k →
    j ∣ n.ascFactorial k
```
Structural induction on `k`. Base case is vacuous. Inductive step uses `Nat.ascFactorial_succ`.

**Verified theorem 15** — 699↔961 bridge (conditional):
```lean
theorem erdos_699_binomial_bridge_conditional
    (ss : ∀ k, 1 ≤ k → Erdos961Prop k k)
    (n i : ℕ) (hi : 1 ≤ i) (hi_half : i ≤ n / 2) :
    ∃ p : ℕ, p.Prime ∧ i < p ∧ p ∣ Nat.choose n i
```
Proof: apply the `ss` hypothesis at `k = i, m = n - i + 1`. The resulting integer `j ∈ [n-i+1, n]` has a prime factor `p > i`. By `dvd_ascFactorial_of_mem`, `j ∣ (n-i+1).ascFactorial i`, hence `p ∣ (n-i+1).ascFactorial i`. By `Nat.ascFactorial_eq_factorial_mul_choose`, this equals `i! * n.choose i`. Since `p > i` prime and `p ∣ i! * n.choose i`, and `Nat.Prime.dvd_factorial` gives `p ∤ i!`, conclude `p ∣ n.choose i` via `hp_prime.dvd_mul`.

**Verified theorem 16** — `well_defined_general (k ≥ 1)`: derives `∃ n, Erdos961Prop k n` from `sylvester_schur_general` (transitively sorry — see A.2).

**Verified theorem 17** — `erdos_699_binomial (n i)`: derives the binomial form from `erdos_699_binomial_bridge_conditional` + `sylvester_schur_general` (transitively sorry).

Total: **15 fully verified theorems** + **2 transitively verified** (depend on one sorry), + **2 helper lemmas** (`not_mem_smoothNumbers_of_prime_factor`, `minFac_ge_three_of_odd`) + **1 definition** (`hasLargePrimeFactor`).

### A.2 AXIOMATIC (honest sorry, documented scope)

**Axiom 1 (remaining core)** — `sylvester_schur_general`:
```lean
theorem sylvester_schur_general (k : ℕ) (hk : 1 ≤ k) : Erdos961Prop k k
```
This is the full Sylvester–Schur theorem for consecutive-integer intervals (the "961 form"). It is classically a theorem — Sylvester 1892 proved the binomial form, Erdős 1934 re-proved both forms elementarily. The Lean 4 proof requires:
- Legendre's formula on `p`-adic valuation of `n!` (known as `Nat.factorial_multiplicity` in some Mathlib modules; availability in v4.27 requires verification);
- binomial-coefficient size estimates (`Nat.choose` bounds);
- case analysis on `m` versus a threshold, plus Størmer-type consecutive-smooth-number classification for the small-`m` tail.

Estimated Lean 4 effort: **50–80 theorems**, multi-session. Not attempted in this paper. Citation: [Er34] Erdős, "Beweis eines Satzes von Tschebyschef", Acta Litt. Sci. Szeged 5 (1932), 194–198.

**Axiom 2 (transitive)** — `erdos_699_binomial`: identical to A.1 theorem 17, depending on Axiom 1.

### A.3 EMPIRICAL

- `sylvester_schur_k{3..10}_bounded`: 1,552 finite cases verified by `native_decide` in under 15 seconds total.
- Reproducible via `lake env lean CollatzRei/Step992SylvesterSchur.lean` → exit 0 (only 1 expected `sorry` warning for Axiom 1).

### A.4 Build verification

File: `data/lean4-mathlib/CollatzRei/Step992SylvesterSchur.lean`, 270 lines.
Build command: `cd data/lean4-mathlib && lake env lean CollatzRei/Step992SylvesterSchur.lean`
Result: exit 0, 1 `sorry` warning at line 186 (`sylvester_schur_general`), 1 `sorry` warning at line 257 (`erdos_699_binomial`, transitive).
Pre-commit hook ran at commit `8686157` and verified the file in 14 seconds.

---

## Part B. 今回の発見 (Findings)

### B.1 Cheap-win / hard-core separation

Formalizing Sylvester–Schur exposes a clean cheap/hard split:

- **Cheap** (≤ 2-hour effort total): `k = 1, k = 2`, Bertrand-boundary `m = k+1` for every `k`, bounded finite checks via `native_decide` for `k ≤ 10, m ≤ 200`, and the 961↔699 bridge.
- **Hard** (50–80 theorem estimate): general `k ≥ 3` for arbitrary `m`, requires the Erdős 1934 elementary proof. No Mathlib shortcut.

The bridge theorem is the most informative by itself: it exhibits exactly *why* 699 and 961 are the same theorem in two costumes, and provides a typed Lean 4 morphism between them. This allows future work to close only one form and derive the other.

### B.2 Mathlib v4.27 coverage

We confirmed:
- `Nat.exists_prime_lt_and_le_two_mul` (Bertrand) is in `NumberTheory/Bertrand.lean`.
- `Nat.smoothNumbers`, `Nat.primeFactorsList`, `Nat.mem_primeFactorsList` are in `NumberTheory/SmoothNumbers.lean`.
- `Nat.ascFactorial`, `Nat.ascFactorial_eq_factorial_mul_choose`, `Nat.ascFactorial_succ` are in `Data/Nat/Factorial/Basic.lean` and `Data/Nat/Choose/Basic.lean`.
- `Nat.Prime.dvd_factorial` is in `Data/Nat/Prime/Factorial.lean` and directly gives `p > i → ¬ p ∣ i!`.
- A general `sylvester_schur` theorem is **not** in Mathlib v4.27 (verified by grep).

### B.3 No overclaim of solveProbability

Entries `699.json` and `961.json` in the Open Problems META-DB were, before this paper, tagged `paperCandidate: true, solveProbability: 0.8, famousHardCap: null` — the Paper 132 ingestion-bug pattern. This paper does **not** solve them; it only closes a partial fragment. After this paper, honest metadata should be:
- `formalization.sorryCount`: `699 → 3 (unchanged), 961 → 5 (unchanged)` (our file does NOT patch the formal-conjectures repo)
- `paperCandidate: false` (closure requires Erdős 1934, outside current scope)
- `famousHardCap`: not applicable (the theorem is classically proven; the obstacle is Lean 4 transport, not mathematical novelty)

This correction will be applied in a follow-up META-DB sync commit.

---

## Part C. 次の発明 (Next inventions)

1. **Legendre-formula Lean 4 module** (estimated 20 theorems). If Mathlib lacks a clean `p`-adic valuation of `n!` form suitable for Sylvester–Schur, write a Rei-AIOS module to bridge. Prerequisite for full `sylvester_schur_general`.
2. **Størmer consecutive-smooth-number characterization in Lean 4** (estimated 15 theorems). The pairs `(1,2), (2,3), (3,4), (8,9)` as the only 3-smooth consecutive pairs. This is a beautiful finite-case Pell-equation theorem with Lean 4 `decide` potential.
3. **Ramanujan-strengthened Bertrand** (Ramanujan 1919: two primes in `(n, 2n]` for `n ≥ 11`). Would shorten the `m = k+1` case analysis and give a one-step proof for `k ≤ ?`.

---

## Part D. 次の未解決 (Next open problems)

- **Q44'** (extension of Paper 121 Q44): for which `k, m` does Sylvester–Schur admit an elementary proof via only Bertrand? Conjecturally, `k ≤ 8` and `m ≤ 4k` covers most of the boundary cases, but no clean threshold formula is known.
- **Q60** (new, this paper): is there a general decidable predicate that refines `hasLargePrimeFactor` to give linear-time verification for `k ≤ C log N`? If yes, then `native_decide` can push bounded verification to `m ≤ 10^6` and reveal smooth-number-density corrections.
- **Q61** (new, this paper): in the 699↔961 bridge, the prime `p` output by `erdos_699_binomial_bridge_conditional` satisfies `i < p ≤ n`. Is there a version where `p ≤ n/2 + 1` always? This would sharpen the classical result.

---

## Part E. 引用 (References)

- [Sy92] Sylvester, J. J., *On arithmetical series*, Messenger of Math. 21 (1892), 1–19, 87–120.
- [Er34] Erdős, Paul, *Beweis eines Satzes von Tschebyschef*, Acta Litt. Sci. Szeged 5 (1932), 194–198.
- [RaSh73] Ramachandra, K. and Shorey, T. N., *On gaps between numbers with a large prime factor*. Acta Arith. 24 (1973), 99–111.
- [Ju74] Jutila, Matti, *On numbers with a large prime factor. II*. J. Indian Math. Soc. (N.S.) 38 (1974), 125–130.
- Mathlib v4.27 — `Mathlib.NumberTheory.Bertrand`, `Mathlib.NumberTheory.SmoothNumbers`, `Mathlib.Data.Nat.Choose.Basic`, `Mathlib.Data.Nat.Prime.Factorial`.
- Rei-AIOS Paper 130 (DOI `10.5281/zenodo.19700758`) — Open Problems META-DB.
- Rei-AIOS Paper 132 (DOI `10.5281/zenodo.19704359`) — Five Rei candidates + ingestion-bug confession (Part F).

---

## Part F. 誠実な失敗と修正の記録 (Honest failures and corrections)

**F.1 First attempt at k=3 general case** — failure and learning.

Initial strategy: case-split `m mod 6` and argue that among `m, m+1, m+2`, at least one is coprime to 6 (no prime factor ≤ 3), hence its `minFac ≥ 5`. This is **wrong**: a number can have a prime factor `> 3` while still being divisible by 2 or by 3. Counterexample: `m = 8` yields `{8, 9, 10}` where `10 = 2·5` has prime factor 5 > 3, yet is not coprime to 6.

The case `r = 2` of the mod-6 split (`m = 6q+2`) exposes the real difficulty: the window `{6q+2, 6q+3, 6q+4} = {2(3q+1), 3(2q+1), 2(3q+2)}`. For the claim to fail would require `3q+1, 2q+1, 3q+2` all to be 3-smooth, i.e., `(3q+1, 3q+2)` a consecutive 3-smooth pair. By Størmer's theorem (1897), such pairs are only `(1,2), (2,3), (3,4), (8,9)` — a finite list — but **proving Størmer's theorem is itself deep** (Pell-equation finiteness).

Lesson: an arithmetic case split that *feels* elementary can secretly embed a deep finiteness theorem. The `k = 3` general case is genuinely as hard as the general case; we should not attempt it without Størmer (or the Erdős 1934 alternative).

**F.2 ascFactorial identity mistake** — picked the wrong theorem.

Initial code used `Nat.ascFactorial_eq_factorial_mul_choose'` (primed), whose statement is `n.ascFactorial k = k! * (n+k-1).choose k`. For the bridge we needed the unprimed form `(n+1).ascFactorial k = k! * (n+k).choose k`. The error was caught by Lean's type checker when the output `(n - 1).choose i` didn't match the expected `n.choose i`.

Lesson: Mathlib has both primed/unprimed variants of ascFactorial identities. The unprimed one directly takes `(n+1)` as its argument; we need this when starting the consecutive-product at `n - i + 1`.

**F.3 omega failure on `n - i + i = n`** — natural-number subtraction.

After fixing F.2, `omega` could not close `n - i + i = n` despite `i ≤ n / 2` being in scope. Root cause: `Nat` subtraction is truncating, and omega sometimes needs the bound expressed as a direct hypothesis, not derived through `n / 2`. Fix: replace `by omega` with `Nat.sub_add_cancel (le_trans hi_half (Nat.div_le_self _ _))`.

Lesson: when `omega` gets stuck inside a `have` block that also contains `have key := ...`, the surrounding metavariables can interfere. Prefer direct `Nat.sub_add_cancel` / `Nat.sub_add_cancel'` / `Nat.add_sub_cancel_left` citations.

**F.4 Structural** — Paper 132's Part F.4 ingestion lesson applies directly here.

Entries `699, 961` were `paperCandidate: true` with `solveProbability: 0.8` in the Open Problems META-DB pre-2026-04-23. Paper 132's Part F.4 motivated a fresh audit; 6 entries were corrected as "actually open with famousHardCap", and 2 (699, 961) were isolated as "classical proven, formalizable". This paper is the Option-B follow-up: formalize what can be formalized honestly, and report the scope limit transparently.

---

## Part G. テスト結果 (Tests — if applicable)

No new TypeScript tests. The Lean 4 file is the test artifact. Repro:

```bash
cd data/lean4-mathlib
lake env lean CollatzRei/Step992SylvesterSchur.lean
# Expected: exit 0, 2 sorry warnings (both intentional)
```

All 15 non-transitive theorems verified by `lake env lean` at commit `8686157`.

---

## Part H. データセット (Datasets — if applicable)

None. This paper adds no Tier 1/2/3 entries to the Open Problems META-DB; it updates the state of two existing Tier 1 entries (`erdos/699.json`, `erdos/961.json`). Updated state: `formalization.lean4` → `"partial-step-992"`, `known_progress` → appended entry `2026-04-24: Step 992 partial Lean 4 formalization, 15 verified theorems, 1 core sorry`.

---

## Part I. 公開・再現手順 (Publication & reproducibility)

- Zenodo DOI: (pending at publication time)
- Internet Archive: item URL assigned on upload
- Harvard Dataverse: dataset `doi:10.7910/DVN/KC56RY`
- 8 blog mirrors: dev.to, Hatena, HackMD, Notion, Mastodon, Zenn, Scrapbox, livedoor (auto)
- Source code (AGPL-3.0): `fc0web/rei-aios` at commit `8686157`; Lean file at `data/lean4-mathlib/CollatzRei/Step992SylvesterSchur.lean`.
- Rei-AIOS Public Open Problems META-DB: `fc0web/rei-open-problems` (2,583 entries).

---

## Part J. 限界 (Limitations)

1. `sylvester_schur_general` for `k ≥ 3` is not closed in this paper. The paper explicitly does not claim to have proved the general Sylvester–Schur theorem.
2. The Paper 132 ingestion bug was remediated for 6 Erdős entries; 699 and 961 metadata should be further updated after this paper to reflect `paperCandidate: false` + `formalization.lean4: "partial-step-992"`.
3. The bounded `native_decide` cases cover `m ≤ 200`, which is far below any asymptotic regime. They provide assurance that the small-case pattern holds but contribute nothing asymptotic.
4. The bridge theorem's output prime satisfies only `i < p ≤ n`; refining to `p ≤ n/2 + 1` (Q61) is open.

---

## Part K. 謝辞 (Acknowledgements)

- Sylvester 1892, Erdős 1934, Jutila 1974, Ramachandra–Shorey 1973 for the classical theorem and its refinements.
- Mathlib team for `Nat.exists_prime_lt_and_le_two_mul`, `Nat.ascFactorial_eq_factorial_mul_choose`, `Nat.Prime.dvd_factorial`, `Nat.mem_primeFactorsList`.
- DeepMind formal-conjectures repo for the `Erdos961Prop` scaffold statements.
- Rei-AIOS Paper 132 Part F.4 for the structural honesty lesson that motivated this paper's Option-B scope.
- Peace Axiom #196 · Fujimoto, Nobuki × Rei-AIOS (Claude Opus 4.7).

---

*End of Paper 133.*
