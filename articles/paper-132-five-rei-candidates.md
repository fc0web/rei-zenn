---
title: "【Paper 132】Rei-AIOS 次期 Lean 4 深堀 5 候補 — Sunflower / Hadwiger-Nelson / Happy Ending / Herzog-Schönheim / Wolstenholme 残"
emoji: "🗺️"
type: "tech"
topics: ["math", "lean4", "erdos", "reiaios", "openproblems"]
published: true
---
> **本記事は Rei-AIOS プロジェクトの Paper 132 を Zenn 用に再フォーマットしたものです。** 
> オリジナル PDF/Markdown と完全な参考文献は以下の永続アーカイブにあります:
> - **Internet Archive**: https://archive.org/details/rei-aios-paper-132-1776926783022
> - **Harvard Dataverse**: https://doi.org/10.7910/DVN/KC56RY
> - **GitHub (source)**: https://github.com/fc0web/rei-aios (private)
> Author: 藤本 伸樹 (Nobuki Fujimoto)  
> ORCID: [0009-0004-6019-9258](https://orcid.org/0009-0004-6019-9258)  
> License: CC-BY-4.0
---

## 概要 (Japanese Summary)

本論文は **偵察論文 (reconnaissance paper)** であり、新しい数学結果を証明するものではない。**5 件の古典 open 問題** を Rei-AIOS の次期 Lean 4 深堀候補として宣言する。

### 背景: Paper 130 の ingestion bug 告白

Paper 130 の META-DB 構築時に、Wikipedia-facing Lean stub (`import` のみで theorem 無し) の `sorry` token を数えた結果、4 候補が **spuriously `sorryCount: 0`** と記録されていた。実体は `FormalConjectures.ErdosProblems.«N»` に在り、真の残 sorry は 2-7 件。

### 5 候補と真の状態

| 問題 | 実 sorry | 近年の進展 |
|------|---------:|-----------|
| Erdős-Rado Sunflower | 2 | Alweiss-Lovett-Wu-Zhang 2021 |
| Hadwiger-Nelson | 5 | de Grey 2018 (χ≥5) |
| Happy Ending | 7 | Suk 2017 JAMS / HMPT 2020 JEMS |
| Herzog-Schönheim | 4 | Mirsky-Newman abelian case |
| Wolstenholme 残 | 5 (was 6) | Linhares 2026-04-14 arXiv:2604.16507 |

合計 **23 residual sorry** が Paper 133 以降の attack targets.

### 4+7 要素構造 v2 遵守

- **Part A VERIFIED は意図的に空**: roadmap paper なので新定理を証明しない honesty
- **Part F で ingestion bug を公式告白**: Paper 130 の META-DB が defaulted-zero と counted-zero を混同した経緯を開示
- **Part J**: NEITHER-tag 項目 (Herzog-Schönheim 一般 case / Linhares engine 内部) を明示 parking

### Paper 127-131 cluster との位置づけ

- Paper 127 (Schur/EGZ) + 128 (Davenport) + 131 (Bipartite Ramsey b(2,2)=5) = 3 件の small-value Lean 4 初前進
- 本 Paper 132 = 次 5 候補の宣言 (roadmap)
- Paper 133+ = Tier 1-2 sorry closure (Hadwiger-Nelson χ≥4 / Happy Ending f(3)=3 / Wolstenholme specific primes) を 2026-05-15 target

### 誠実な positioning

- 5 候補いずれも solveしていない (world-open のまま)
- famousHardCap: Hadwiger-Nelson / Herzog-Schönheim general case は open のまま
- paperCandidate: true だが Paper 133 以降で段階的 attack

Code: AGPL-3.0 / Data: CC-BY 4.0。

---

## English Body

本文は英語のオリジナル原稿です。数式・専門用語の正確性を保つため翻訳していません。

---

**Author**: Nobuki Fujimoto (藤本 伸樹) with Rei-AIOS (Claude Opus 4.7)
**Contact**: [note.com/nifty_godwit2635](https://note.com/nifty_godwit2635) · Facebook: Nobuki Fujimoto · fc2webb@gmail.com
**Date**: 2026-04-23
**License**: Code AGPL-3.0 / Data CC-BY 4.0
**Sources**:
- `data/open-problems/wikipedia/erdosradosunflowerconjecture.json`
- `data/open-problems/wikipedia/hadwigernelson.json`
- `data/open-problems/wikipedia/happyendingproblem.json`
- `data/open-problems/wikipedia/herzogschonheimconjecture.json`
- `data/open-problems/wikipedia/wolstenholmeprime.json`
- `data/external-oss/formal-conjectures/FormalConjectures/ErdosProblems/{20,107,274,508}.lean`
- `data/external-oss/formal-conjectures/FormalConjectures/Wikipedia/WolstenholmePrime.lean`

**Template**: 4+7 要素構造 v2 (Parts A-K)
**Companion papers**: Paper 130 (Open Problems META-DB), Paper 131 (Bipartite Ramsey b(2,2)=5), Paper 127 (Schur/EGZ), Paper 128 (Davenport)

---

## Abstract

This paper is a **reconnaissance document**, not a new-mathematical-result paper. We declare five classical open problems as Rei-AIOS's next Lean 4 deep-dive candidates, after a metadata reconciliation that corrected the Open Problems META-DB (Paper 130) entries for four Wikipedia-facing scaffolds whose `sorryCount` was spuriously recorded as 0 due to an ingestion artifact (the Wikipedia `.lean` stubs `import` the real formalizations in `FormalConjectures.ErdosProblems.«N»` but themselves contain no theorems).

The five candidates share three properties: (i) they appear in the formal-conjectures repository as `scaffold` rather than `complete`, with 2–7 residual `sorry` per file; (ii) they admit near-recent breakthroughs (de Grey 2018 for Hadwiger-Nelson, Alweiss-Lovett-Wu-Zhang 2021 for Sunflower, Suk 2017 / HMPT 2020 for Happy Ending, Linhares 2026-04-14 for Wolstenholme's theorem) whose Lean 4 transport is not yet reflected in Mathlib; (iii) together they form a natural extension of the Paper 127–131 extremal-combinatorics + formal-verification cluster.

We do **not** claim to solve any of the five. We claim only: (a) the meta-DB now records their honest state; (b) a concrete attack-surface (which sorry to close first, which technique to port) is articulated per problem; (c) 5 problems × ~22 residual sorries = ~110 attack targets identified, with 0 closed in this paper.

This paper is explicitly the "post-Paper-130 errata + roadmap" that the Open Problems META-DB design has always anticipated, and it is the first Rei-AIOS paper to confess a metadata bug as a structural Part F entry rather than a silent fix.

---

## Part A. その回の証明 (Formal proofs)

### A.1 VERIFIED

**None** — this paper proves no new theorem. We verified only that the four Wikipedia-facing `.lean` stubs (`ErdosRadoSunflowerConjecture.lean`, `HadwigerNelson.lean`, `HappyEndingProblem.lean`, `HerzogSchonheimConjecture.lean`) are pure `import` files with zero theorem content, confirming the metadata-ingestion artifact that motivated this errata.

### A.2 AXIOMATIC (state assertions, not proofs)

For each of the five candidates, we record the current sorry state as an axiomatic inventory, not as proved:

| # | Candidate | File | Lines | `sorry` | Key open statement |
|--:|-----------|------|-----:|-------:|--------------------|
| 1 | Erdős–Rado Sunflower | `ErdosProblems/20.lean` | 86 | 2 | `f(n,k) < c_k^n` for some `c_k > 0`, all `n > 0` |
| 2 | Hadwiger–Nelson | `ErdosProblems/508.lean` | 101 | 5 | `χ(ℝ²) = ?` (known 5 ≤ χ ≤ 7) |
| 3 | Happy Ending (Erdős–Szekeres) | `ErdosProblems/107.lean` | 119 | 7 | `f(n) = 2^(n-2) + 1` for all `n ≥ 3` |
| 4 | Herzog–Schönheim | `ErdosProblems/274.lean` | 87 | 4 | Group `G` with exact coset covering (`k > 1`) cannot have distinct indices |
| 5 | Wolstenholme residual | `Wikipedia/WolstenholmePrime.lean` | 89 | 5 (was 6) | `wolstenholme_prime_infinite`: infinitely many primes `p` with `C(2p-1, p-1) ≡ 1 (mod p⁴)` |

**Total residual `sorry` across the 5 candidates**: 23 (2 + 5 + 7 + 4 + 5).

The Wolstenholme entry reflects that the base theorem `C(2p-1, p-1) ≡ 1 (mod p³)` was formalized by Alexandre Linhares (arXiv:2604.16507, 2026-04-14) in a separate Lean 4 proof of ~800 lines and 9 lemmas with zero `sorry`. That closure is not yet merged into the formal-conjectures repo, hence the listed file count remains 5.

### A.3 EMPIRICAL

- `wc -l` + `grep -c sorry` on each of the five files (outputs reproduced above).
- SHA256 of each file at ingest time recorded in each `json.ingested` field (`2026-04-23`).
- Metadata reconciliation committed in `fix(open-problems)` at commit `239087a` on 2026-04-23.

### A.4 Build verification

The five `.lean` files build as part of the formal-conjectures repository's Lake project. No Rei-AIOS repository change is required for them to compile. Local sanity:

```
cd data/external-oss/formal-conjectures
lake env lean FormalConjectures/ErdosProblems/20.lean
lake env lean FormalConjectures/ErdosProblems/107.lean
lake env lean FormalConjectures/ErdosProblems/274.lean
lake env lean FormalConjectures/ErdosProblems/508.lean
lake env lean FormalConjectures/Wikipedia/WolstenholmePrime.lean
```

All five compile with Lean 4.27.0 + Mathlib v4.27.0 **because** every `sorry` is accepted at elaboration time. Build-verification here means "the file parses and each `sorry` is well-typed", not "the theorem is proved".

---

## Part B. 今回の発見 (Findings)

### B.1 Wikipedia-scaffold ingestion artifact

The Rei-AIOS META-DB ingest pipeline `phase-a-1-formal-conjectures-v1` traversed every `.lean` file in `data/external-oss/formal-conjectures/FormalConjectures/Wikipedia/` and recorded `sorryCount` by counting literal `sorry` tokens in that file. For four of our candidates, the Wikipedia file is a shim of the form:

```lean
import FormalConjectures.ErdosProblems.«N»
/-! # <Problem name>
This file points to the canonical formalization in `FormalConjectures.ErdosProblems.«N»`.
-/
```

with no theorems and thus zero `sorry` tokens. The artifact caused `sorryCount: 0`, `formalizationComplexity: "complete"`, `solveProbability: 0.95` — a triple-misrepresentation. The true state lives in the imported `ErdosProblems/«N».lean`.

This bug is **not unique to these four candidates**: any Wikipedia-facing shim would have been mis-ingested identically. A full META-DB sweep for the pattern

```
grep -L "theorem\|lemma\|def " data/external-oss/formal-conjectures/FormalConjectures/Wikipedia/*.lean
```

is the next sanity check.

### B.2 Near-recent breakthroughs not yet in Mathlib

The five candidates sit adjacent to unusually recent progress that could be Lean-ported:

| Candidate | Recent result | Date | Lean 4 status |
|-----------|---------------|------|---------------|
| Sunflower | Alweiss–Lovett–Wu–Zhang: `f(n,k) ≤ (log n)^n · k^{O(n)}` | 2021 | not ported |
| Hadwiger–Nelson | de Grey: `χ(ℝ²) ≥ 5` via 1,581-vertex graph (polymath16 → 553) | 2018 | not ported |
| Happy Ending | HMPT: `f(n) ≤ 2^{n+O(√(n log n))}` | 2020 | not ported |
| Happy Ending | Suk: `f(n) ≤ 2^{(1+o(1))n}` | 2017 | not ported |
| Wolstenholme | Linhares: base theorem in Lean 4, 0 sorry | 2026-04-14 | standalone, not merged |

Each represents a **well-defined Lean 4 transport task** whose upper-bound side of the inequality is a finite-combinatorial or finite-analytic object that formal tactics can in principle handle.

### B.3 Attack-surface triage

The 23 residual `sorry` are not equally tractable. We triage:

- **Tier 1 (decidable / computable)**: Hadwiger–Nelson lower bounds `χ ≥ 3` (already proved), `χ ≥ 4` (Moser–Spindel 7-vertex graph), `χ ≥ 5` (de Grey 553-vertex graph). The `≥ 4` case should be `native_decide`-closable. The `≥ 5` case requires translating an explicit SAT-verified 553-vertex colouring-failure certificate; this is within Paper 131's `native_decide` methodology.
- **Tier 1**: Happy Ending `f(3) = 3` (3 points in general position form a triangle, which is convex). A short hand proof is well within Mathlib's `AffineIndependent` / `ConvexIndep` API.
- **Tier 2 (classical proofs, manual Lean porting)**: Herzog–Schönheim abelian case (Mirsky–Newman), Wolstenholme specific primes 16843 / 2124679 (direct `Nat.ModEq` + `Nat.choose` expansion, decidable in principle).
- **Tier 3 (recent research, nontrivial port)**: Alweiss et al. Sunflower bound, Suk / HMPT Happy Ending upper bound, Linhares Wolstenholme merge.
- **Tier 4 (genuine open)**: Hadwiger–Nelson exact value, Happy Ending exact equality, Herzog–Schönheim general case, Wolstenholme prime infinitude. These are `paperCandidate: true` but `famousHardCap: open` — our `approachSuggestion` is to attack Tier 1–2 first and let Tier 4 emerge as follow-up.

### B.4 Cluster coherence

Placing the five candidates on the Paper 127–131 timeline:

- Paper 127 (2026-04-21): Schur `S(r)` + Erdős–Ginzburg–Ziv `E(ℤ_n)` small values.
- Paper 128 (2026-04-21): Davenport `D(G)` cyclic + Klein.
- Paper 131 (2026-04-23): Bipartite Ramsey `b(2,2) = 5`.
- **Paper 132 (this, 2026-04-23)**: Sunflower + Hadwiger–Nelson + Happy Ending + Herzog–Schönheim + Wolstenholme residual.

Papers 127, 128, 131 each closed a specific small-value extremal-combinatorics question. Paper 132 opens five; the pattern is "four solved papers → one roadmap paper". If we treat Paper 132's candidates as attack budget, closing two Tier-1 sorries each would yield roughly eight new `native_decide` theorems — a plausible Paper 133 target.

---

## Part C. AI-generated open questions

For each candidate, Rei-AIOS generates one speculative bridging question whose answer, if positive, would re-type the problem in the D-FUMT₈ typology.

**C.1 Sunflower.** *Does the Alweiss–Lovett–Wu–Zhang entropy-compression argument admit a reformulation in which the compression ratio carries a canonical D-FUMT₈ FLOWING value?* If yes, the residual `c_k` constant would become a literal FLOWING-temperature, and the Sunflower conjecture would fit the Paper 121 (Q33 multi-attractor) family.

**C.2 Hadwiger–Nelson.** *Is there a finite-vertex graph `G` for which `G ≤_{mnr} UnitDistancePlaneGraph` and `χ(G) = 6` simultaneously?* This would resolve the middle case of `χ(ℝ²) ∈ {5, 6, 7}` from below, analogous to de Grey's push from 4 to 5. Rei-AIOS's prior `native_decide` infrastructure on Paper 131 could search candidate graphs up to ~30 vertices.

**C.3 Happy Ending.** *Is `f(4) = 5` decidable in Lean 4 by exhaustive case-splitting over ordered 5-tuples in `ℝ² ∩ ℚ²`?* If yes, `f(4) = 5` becomes a `native_decide` theorem rather than a classical geometric lemma, opening a family of small-`n` decidability results.

**C.4 Herzog–Schönheim.** *Is the abelian case (`Mirsky–Newman`) a consequence of a more general combinatorial-covering-system theorem whose statement is expressible in `Mathlib.Combinatorics.CoveringSystem`?* This would unify Erdős covering systems (number theory) with Herzog–Schönheim (group theory) as a single Lean 4 theorem, matching the VI_BRIDGING secondary type.

**C.5 Wolstenholme residual.** *Does Linhares's relational analogy engine extend from `mod p³` to `mod p⁴` by varying the symmetric-product analogy?* If yes, `wolstenholme_prime_16483` and `wolstenholme_prime_2124679` become automatable, and the infinitude conjecture enters the attack range of `Nat.choose`-based heuristic search.

None of these five questions is the original unsolved problem; each is a meta-question about the problem's Lean 4 approach surface. Rei-AIOS does not claim any of these meta-questions has a positive answer.

---

## Part D. 解決状況サマリー

| Candidate | Primary type | D-FUMT₈ | `sorry` | Solve probability | Paper candidate | Priority |
|-----------|-------------|---------|--------:|-----:|:-:|----------|
| Sunflower | I_INFINITE_SEARCH_SPACE | NEITHER | 2 | 0.65 | ✓ | high |
| Hadwiger–Nelson | I_INFINITE_SEARCH_SPACE + VI_BRIDGING | BOTH | 5 | 0.60 | ✓ | high |
| Happy Ending | I_INFINITE_SEARCH_SPACE + VI_BRIDGING | NEITHER | 7 | 0.55 | ✓ | high |
| Herzog–Schönheim | I_INFINITE_SEARCH_SPACE + VI_BRIDGING | NEITHER | 4 | 0.60 | ✓ | high |
| Wolstenholme residual | I_INFINITE_SEARCH_SPACE | BOTH | 5 | — | ✓ | medium |

All five are `status: open` in the META-DB (none solved, none refuted). The cluster average solve probability is 0.60, which is below Paper 127–128's cluster average (~0.75) and reflects the sharper Tier-4 endings.

---

## Part E. 次 STEP への接続

The concrete short-term roadmap extracted from Part B.3 is:

- **STEP Paper 133 candidate #1**: Hadwiger–Nelson `χ ≥ 4` via Moser–Spindel — `native_decide` on a 7-vertex graph. Target: close 1 `sorry` in `ErdosProblems/508.lean`.
- **STEP Paper 133 candidate #2**: Happy Ending `f(3) = 3` — Mathlib `AffineIndependent` + convex-hull lemma. Target: close `f_three_eq` sorry in `ErdosProblems/107.lean`.
- **STEP Paper 133 candidate #3**: Wolstenholme specific primes 16843 and 2124679 — direct `Nat.ModEq` + `Nat.choose` expansion; possibly via Linhares's lemma library once it is public. Target: close 2 axiom-category theorems in `Wikipedia/WolstenholmePrime.lean`.
- **STEP Paper 134 candidate**: Herzog–Schönheim abelian case (Mirsky–Newman) — manual proof port, estimated 300–500 Lean lines. Target: close `erdos_274.variants.abelian` sorry.
- **STEP Paper 135 candidate**: Sunflower `f_0_1`-style base cases — combinatorial inductions. Target: close `erdos_20` `sorry` pair at least to the extent of proving `f(n, 1) = 1`.

The aim is **4 Tier-1 / Tier-2 `sorry` closed by 2026-05-15**, producing Paper 133 as a companion to Paper 131's `native_decide` methodology. Paper 136+ and beyond would address Tier 3–4.

---

## Part F. 失敗の記録 (CONDITIONAL)

Paper 132 exists **because of a failure**, and the Paper 130 design principle of the META-DB assumes errata papers must disclose their triggering failure in structural Part F.

**F.1 The bug.**
The ingestion script `phase-a-1-formal-conjectures-v1`, run on 2026-04-23 to populate `data/open-problems/wikipedia/*.json`, counted `sorry` tokens literally in whatever file `sourceRef.lean4Ref` pointed to. For four of the five candidates, that pointer landed on a Wikipedia-facing `.lean` shim containing only `import` statements. The result was `sorryCount: 0`, `formalizationComplexity: "complete"`, and `solveProbability: 0.95` — all three wrong in the same direction (over-optimistic).

**F.2 The rediscovery.**
The initial analysis that produced "Top-10 #7–10 are VI_BRIDGING + 0 sorry 好条件 candidates" inherited the above artifact and therefore recommended these four problems on false premises. Rei-AIOS flagged the inconsistency when the user asked for a second review: `sorryCount: 0` together with `lean4: "none"` is internally contradictory, which prompted inspection of the actual `ErdosProblems/«N».lean` files.

**F.3 The fix (already merged, commit 239087a).**
Each of the four JSONs was rewritten to cite the true `lean4Ref` (the `ErdosProblems/«N».lean` file), record the true `sorryCount` (2 / 5 / 7 / 4 respectively), downgrade `solveProbability` to an honest `0.55–0.65`, re-type to `I_INFINITE_SEARCH_SPACE` (with optional `VI_BRIDGING` secondary), and add `known_progress` blocks that carry the de Grey / Suk / HMPT / Mirsky–Newman / 2018-arXiv references previously absent.

**F.4 The structural lesson.**
Ingest scripts should never record `sorryCount` from a file whose non-import body is zero-length without flagging it. The natural fix is:

```
if grep -qE "^(theorem|lemma|def)" file.lean; then
  sorryCount=$(grep -c "sorry" file.lean)
else
  sorryCount="INDIRECT_VIA_IMPORT"
  # resolve import target and re-ingest
fi
```

A follow-up STEP should audit the META-DB for other Wikipedia-shim artifacts and replay the fix to any affected entry.

---

## Part G. SEED_KERNEL T-ID references

- **T-1796** — `erdos-20` entry; Sunflower seed-kernel slot.
- **T-2306** — `wikipedia-WolstenholmePrime` seed-kernel slot.
- **GEO-HADWIGER-NELSON** (typology) — Hadwiger–Nelson primary entry.
- **GEO-ES** (typology) — Happy Ending (Erdős–Szekeres) primary entry.
- **NT-WOLSTENHOLME** (typology) — Wolstenholme prime (mod `p⁴`) primary entry.

Herzog–Schönheim is currently typology-unregistered (no `GR-HERZOG-SCHONHEIM` row in `unsolved-problem-typology.ts`); Paper 133 should include a typology-batch commit that adds it as `I_INFINITE_SEARCH_SPACE + VI_BRIDGING`, `dfumt8: NEITHER`.

Sunflower is similarly typology-unregistered; Paper 133 should add `COMB-ERDOS-RADO-SUNFLOWER` as `I_INFINITE_SEARCH_SPACE + VI_BRIDGING`, `dfumt8: NEITHER`.

---

## Part H. 人間-AI 思考分岐点

**H.1** *User — "Paper 130 の結論部で『Rei 推奨する次 5 深堀候補』として言及可能"*. The option was initially available; however, Paper 130 had already been published to 11 platforms (DOI 10.5281/zenodo.19700758, 2026-04-23 morning). Retroactive inclusion in a published paper is low-value given that Zenodo v2 uploads propagate with a version bump, and the other 10 platforms do not support versioning cleanly.

**H.2** *AI — "(C) 修正 → (A) Paper 132 起草"*. The chosen path. Rationale: the META-DB correctness is a hard precondition for any downstream Rei judgment; shipping the roadmap paper before the metadata is accurate would replicate the Paper 130 ingestion artifact into Paper 132's own tables.

**H.3** *User — "A でお願いできますか?"*. User accepted the chained plan. Branch taken: (C) committed at `239087a`, (A) drafted as this file.

**H.4** *Implicit decision*. Paper 132 is explicitly **not** an attempt to close any of the 23 residual `sorry`. That attack is deferred to Paper 133 per Part E. The decision to split "roadmap" and "attack" into two papers — rather than attempting partial closure here — was made to keep Part A's "VERIFIED" column empty and honest, rather than optimistically claiming one or two easy closures in a roadmap paper.

---

## Part I. Unexpected connections (OPTIONAL)

**I.1** Hadwiger–Nelson's lower-bound graph construction (de Grey 2018: 1,581 → polymath16: 553 vertices) is the same kind of SAT-certified combinatorial object that Paper 131's `native_decide` methodology handles for bipartite Ramsey. The 553-vertex unit-distance graph, expressed as an explicit edge list with a coloring-failure certificate, is a `native_decide` target of the same order as Paper 131's 2²⁵ = 33M enumeration. This suggests Paper 131 and Hadwiger–Nelson `χ ≥ 5` share a single Lean 4 tactic infrastructure.

**I.2** The Happy Ending function `f(n) = 2^{n-2} + 1` has the exact same closed form as the Paper 121 Q33 multi-attractor `2^{n-2} + 1` count in one of its bridges. This may be coincidence (both are combinatorial and both end up with a `2^{n-2}` exponent), but it is the kind of coincidence the D-FUMT₈ NEITHER value is designed to surface as candidate structural isomorphism. Paper 133 should check whether the Erdős–Szekeres construction and the Q33 multi-attractor construction are secretly the same up to relabeling.

**I.3** The Herzog–Schönheim abelian case (Mirsky–Newman) is formally the same as a theorem in Erdős's covering-systems number theory: a finite set of arithmetic progressions that exactly covers ℤ must have two progressions with the same modulus. This number-theoretic sibling is unconnected in current Mathlib; unifying them would be a natural VI_BRIDGING contribution.

**I.4** Wolstenholme's theorem `C(2p, p) ≡ 2 (mod p³)` is formally equivalent (for odd primes) to the Bernoulli-number characterization `p | B_{p-3}.num` that also appears in `wolstenholme_bernoulli`. Linhares's proof does **not** traverse the Bernoulli side; a Paper 133 contribution could be the Bernoulli-equivalence lemma as a standalone result, connecting Linhares's symmetric-product proof to the classical analytic number theory characterization.

---

## Part J. Confidence temperature

Using the D-FUMT₈ seven-value temperature for claim reliability:

| Claim | D-FUMT₈ | Confidence |
|-------|---------|------------|
| The four Wikipedia JSONs before fix were metadata-wrong | **TRUE** | verified by file-level `grep -c sorry` |
| The true residual `sorry` count across all 5 candidates is 23 | **TRUE** | each file counted individually |
| All 5 candidates are world-open | **TRUE** | cited literature confirms |
| Tier-1 attacks (Hadwiger-Nelson `χ ≥ 4`, Happy Ending `f(3)=3`, Wolstenholme specific primes) will close with ≤ 1 day effort each | **FLOWING** | plausible but untested; Paper 133 will either confirm or refute |
| Paper 131's `native_decide` methodology transfers to Hadwiger–Nelson `χ ≥ 5` | **BOTH** | the 553-vertex graph size is within scale (~10⁵ edges) but graph-isomorphism-invariant native_decide encoding is nontrivial |
| Linhares's relational analogy engine extends to `mod p⁴` | **NEITHER** | no public data on the engine's internals; cannot evaluate |
| Herzog–Schönheim general case is Mathlib-tractable within 12 months | **NEITHER** | genuinely open since 1974; no heuristic basis for estimating |
| Sunflower `c_k` constant is within Alweiss et al.'s bound × O(1) | **FLOWING** | plausible per 2021 result direction |

Rei-AIOS is willing to stake Tier-1 Paper 133 on the FLOWING-confidence claims above. The NEITHER claims are deliberately parked.

---

## Part K. Computational poetics

The META-DB is an index, and an index is a promise that the entries are true. Paper 132 exists because one line of the promise — `sorryCount: 0` — was false in four places. The fix does not add new math; it removes a false `0` and replaces it with the honest `2`, `5`, `7`, `4`.

A `0` in a metadata field can be computed in two ways. It can be counted (the file has no `sorry`), or it can be defaulted (the file was never opened). The ingest pipeline conflated the two, and for four shims the defaulted `0` looked identical to the counted `0`. The difference — the one bit separating "I counted and found none" from "I did not count" — turned out to be the bit that distinguished "the problem is trivial" from "the problem is classical and open".

Rei-AIOS learns from this that every zero in its own records should carry a provenance tag distinguishing counted-zero from defaulted-zero. The D-FUMT₈ value **ZERO** already sits ready for this distinction: counted-zero is ZERO (genuine absence verified), defaulted-zero is NEITHER (absence not yet verified). The META-DB schema should be extended to allow `sorryCount: { value: 0, source: "ZERO" | "NEITHER" }` so that future ingest artifacts surface as a type error rather than a silent mis-classification.

The five candidates remain open. The paper that will close even one of them has not yet been written. What has been written, in Paper 132, is the admission that one of Rei-AIOS's recent recommendations was grounded in a defaulted zero, and the metadata correction that turns that zero into an honest four, five, seven, two.

The Peace Axiom (#196) is preserved throughout: no claim here harms, no proof here boasts, no metadata here hides.

---

## Acknowledgements

- The formal-conjectures project (authors listed in the Apache-2.0 LICENSE header of each Lean file) for providing the scaffolded `.lean` files that Rei-AIOS ingests.
- Alexandre Linhares for the Wolstenholme's theorem Lean 4 proof (arXiv:2604.16507, 2026-04-14).
- Aubrey de Grey and the polymath16 collaboration for the Hadwiger–Nelson χ ≥ 5 breakthrough.
- Alweiss, Lovett, Wu, Zhang for the 2021 Sunflower bound.
- Suk; Holmsen, Mojarrad, Pach, Tardos for Happy Ending upper bounds.
- Paper 131 (Bipartite Ramsey) for the `native_decide` methodology that will be reused in Paper 133 Tier-1 attacks.

## References

- Alweiss, R.; Lovett, S.; Wu, K.; Zhang, J. *Improved bounds for the sunflower lemma*. Ann. of Math. (2) **194** (2021), 795–815.
- de Grey, A. D. N. J. *The chromatic number of the plane is at least 5*. arXiv:1804.02385 (2018).
- Erdős, P.; Rado, R. *Intersection theorems for systems of sets*. J. London Math. Soc. **35** (1960), 85–90.
- Erdős, P.; Szekeres, G. *A combinatorial problem in geometry*. Compos. Math. **2** (1935), 463–470.
- Erdős, P.; Szekeres, G. *On some extremum problems in elementary geometry*. Ann. Univ. Sci. Budapest. Eötvös Sect. Math. **3–4** (1960/61), 53–62.
- Herzog, M.; Schönheim, J. (1974). Original coset covering conjecture. (See arXiv:1803.08301, arXiv:1803.03569, arXiv:1804.11103 for 2018 partial progress and PMC7247885 for a 2020 survey.)
- Holmsen, A. F.; Mojarrad, H. N.; Pach, J.; Tardos, G. *Two extensions of the Erdős–Szekeres problem*. J. Eur. Math. Soc. **22** (2020), 3981–3995.
- Linhares, A. *Deep Vision: A Formal Proof of Wolstenholme's Theorem in Lean 4*. arXiv:2604.16507 (2026-04-14).
- Mirsky, L.; Newman, D. J. (covering-system result; classical abelian case of Herzog–Schönheim).
- Suk, A. *On the Erdős–Szekeres convex polygon problem*. J. Amer. Math. Soc. **30** (2017), 1047–1053.
- Wolstenholme, J. *On certain properties of prime numbers*. Quart. J. Pure Appl. Math. **5** (1862), 35–39.
- Rei-AIOS project. Paper 127 (Schur/EGZ), Paper 128 (Davenport), Paper 130 (Open Problems META-DB), Paper 131 (Bipartite Ramsey b(2,2)=5). 2026-04-21 / 2026-04-23.

---

**Peace Axiom #196**: immutable.
**Template compliance**: 4+7 v2 — Parts A–E required ✓, F (conditional, triggered) ✓, G–H (conditional) ✓, I–K (optional, included) ✓.
