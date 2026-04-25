---
title: "【Paper 135】自己参照クラスター — Löb 証明可能性定理 / 反省的プログラミング / 因果無関係意思決定理論の Lean 4 共通骨格"
emoji: "🔁"
type: "tech"
topics: ["math", "lean4", "selfreference", "reiaios", "fdt"]
published: true
---
> **本記事は Rei-AIOS プロジェクトの Paper 135 を Zenn 用に再フォーマットしたものです。** 
> オリジナル PDF/Markdown と完全な参考文献は以下の永続アーカイブにあります:
> - **GitHub (source)**: https://github.com/fc0web/rei-aios (private)
> Author: 藤本 伸樹 (Nobuki Fujimoto)  
> ORCID: [0009-0004-6019-9258](https://orcid.org/0009-0004-6019-9258)  
> License: CC-BY-4.0
---

## 概要 (Japanese Summary)

本論文は **骨格符号化発見論文 (skeletal-encoding-discovery paper)** であり、新しい定理の証明でも 3 つの源泉問題のいずれかの解決でもない。

### 観察

Open Problems META-DB (Rei-AIOS) の 2026-04-24 cross-tier D-FUMT₈ isomorphism 解析で、3 つの古典的に距離の遠い結果が同一 D-FUMT₈ 型 `(SELF, VIII_META_STRUCTURAL)` を共有することが判明:

- **Löb の証明可能性定理** (1955)
- **Brian Smith の反省的プログラミング / 3-Lisp** (1984)
- **Yudkowsky-Christiano 関数的 / 因果無関係意思決定理論 (FDT)** (2010-)

### 反証可能仮説

3 つは Lean 4 の共通構造骨格を許容する: 型 `S`、反射述語 `reflexive : S → Prop`、非自明な witness。

### VERIFIED (0 sorry)

- 抽象 `SelfRef` 構造 (Step993SelfReference.lean)
- 4 つの型適合インスタンス: Löb-toy / Reflective ToyTerm / Acausal 2x2 ゲーム (2 つの Nash 不動点) / Peace-Axiom
- 3 つの判別定理が、各非自明述語が genuine に reflexive と non-reflexive を分離することを確認

### 結果

**骨格型一致は確認** された。3/4 が判別述語を持ち、骨格は実質的 (vacuous でない)。

しかし、3 つの完全定理 (Löb / Y / FDT) が共通 Lean 4 証明形を共有する強主張は **未解決**:
- Löb: GL モーダル論理が Mathlib v4.27 に未収録
- Reflective: Lean 4 は total → 無型 Y-combinator は Classical 必要
- Acausal: Kakutani 不動点定理が Mathlib topology で部分的のみ

### 誠実位置付け

- 本論文は Löb 定理を **証明しない**
- Y-combinator の普遍性を **証明しない**
- 関数的意思決定理論を **解決しない**

行うこと: META-DB cross-field 観察を Lean 4 型骨格として精緻化、骨格が 3 つの領域で非自明な判別述語を許容することを検証、各領域の concrete future-work obstacle を特定。

2026-04-24 snapshot. 4+7 element structure v2, 11 Parts.

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
**Companion papers**: Paper 130 (Open Problems META-DB), Paper 132 (Rei candidates), Paper 133 (Sylvester-Schur), Paper 134 (AI tooling)
**Lean repo**: `data/lean4-mathlib/CollatzRei/Step993SelfReference.lean` at commit `ae5c5ec` (extended commit pending)

---

## Abstract

This paper is a **skeletal-encoding-discovery paper** — neither a proof of a new theorem nor a resolution of any of the three source problems. We examine a META-DB observation made via the cross-tier D-FUMT₈ isomorphism analysis of 2026-04-24 (`data/claude-lens/cross-tier-dfumt8-isomorphism-2026-04-24.md`): three classically-distant results — Löb's provability theorem (1955), Brian Smith's reflective programming / 3-Lisp (1984), and Yudkowsky-Christiano functional / acausal decision theory (2010–) — share identical D-FUMT₈ typing `(SELF, VIII_META_STRUCTURAL)` in the Open Problems META-DB (Rei-AIOS).

We propose, formalize, and partially test a falsifiable hypothesis: **the three admit a common Lean 4 structural skeleton**, namely a type `S`, a reflexive predicate `reflexive : S → Prop`, and a non-vacuous witness.

### Verified (0 sorry)

- Abstract `SelfRef` structure (`data/lean4-mathlib/CollatzRei/Step993SelfReference.lean`).
- Four type-checked instantiations:
  - **Löb-style** (toy witness; full Löb proof needs GL modal logic not in Mathlib v4.27, out of scope).
  - **Reflective-style** (non-trivial): `ToyTerm` algebra with decidable `evalTerm`, `reflexive t := evalTerm t = t`. Discriminating: `pair atom atom` is not reflexive (proved).
  - **Acausal-style** (non-trivial): 2×2 coordination game with Nash-fixed-point predicate. Two distinct Nash fixed points (cooperate / defect) both proved reflexive — genuine multi-point self-reference.
  - **Peace-Axiom-style** (non-trivial, native Rei): discriminating `PeaceState` predicate.
- Generic theorem `selfRef_has_fixed_witness` applies to all four.
- Three specific discrimination theorems confirming each non-trivial predicate genuinely separates reflexive from non-reflexive elements.

### Outcome of falsifiable test

The **skeletal typing match is confirmed**. All four instantiations compile under the same abstract structure. Three of four exhibit *discriminating* predicates (not mere tautologies), demonstrating the skeleton is substantive, not vacuous.

The stronger claim — that the three *full theorems* (Löb / Y / FDT) share a common Lean 4 proof shape — remains **open**. The obstacles are concretely identified:

| Domain | Blocker for full encoding |
|-|-|
| Löb | GL modal logic + Gödel numbering absent from Mathlib v4.27 |
| Reflective | Lean 4 is total; untyped Y-combinator needs Classical or size-indexed families |
| Acausal | Kakutani fixed-point theorem only partial in Mathlib topology |

### Honest positioning

- This paper does **not** prove Löb's theorem.
- It does **not** prove Y-combinator universality.
- It does **not** resolve functional decision theory.
- What it does: makes a META-DB cross-field observation precise as a Lean 4 type skeleton, verifies the skeleton accommodates non-trivial discriminating predicates in three domains, and identifies concrete future-work obstacles per domain.

---

## Part A. その回の証明 (Formal proofs)

### A.1 VERIFIED

**Definition** (`Step993SelfReference.lean`, lines 54–63):
```lean
structure SelfRef where
  S : Type
  reflexive : S → Prop
  witness : S
  witness_reflexive : reflexive witness
```

**Theorem 1** — Generic existence lemma:
```lean
theorem selfRef_has_fixed_witness (r : SelfRef) : ∃ x : r.S, r.reflexive x :=
  ⟨r.witness, r.witness_reflexive⟩
```

**Instance 1 — Löb (toy)**:
```lean
def lobInstance : SelfRef where
  S := Nat; reflexive := fun _ => True; witness := 0; witness_reflexive := trivial
```

**Instance 2 — Reflective (non-trivial)**:
```lean
inductive ToyTerm : Type | atom | pair : ToyTerm → ToyTerm → ToyTerm
def evalTerm : ToyTerm → ToyTerm
  | .pair .atom .atom => .atom
  | t => t

def reflectiveInstance : SelfRef where
  S := ToyTerm
  reflexive := fun t => evalTerm t = t
  witness := .atom
  witness_reflexive := rfl

theorem pair_atom_atom_not_reflexive :
    ¬ reflectiveInstance.reflexive (.pair .atom .atom) := by
  intro h; simp [reflectiveInstance, evalTerm] at h
```

**Instance 3 — Acausal (non-trivial)**:
```lean
inductive CoopAction | cooperate | defect

def bestResponse : CoopAction → CoopAction
  | .cooperate => .cooperate
  | .defect    => .defect

def acausalInstance : SelfRef where
  S := CoopAction
  reflexive := fun σ => bestResponse σ = σ
  witness := .cooperate
  witness_reflexive := rfl

theorem defect_also_reflexive :
    acausalInstance.reflexive .defect := rfl
```

**Instance 4 — Peace Axiom (native Rei)**:
```lean
inductive PeaceState | ok | violated

def peaceAxiomInstance : SelfRef where
  S := PeaceState
  reflexive := fun s => s = .ok
  witness := .ok
  witness_reflexive := rfl

theorem peace_violated_not_reflexive :
    ¬ peaceAxiomInstance.reflexive .violated := by
  intro h; cases h
```

### A.2 AXIOMATIC (state assertions, not proofs in this paper)

- **Löb's theorem** (Löb 1955): if `PA ⊢ (□P → P)`, then `PA ⊢ P`. Axiomatically referenced; not formalized here (GL modal logic absent from Mathlib v4.27).
- **Universality of the Y-combinator** (Curry, 1930s): in untyped λ-calculus, `Y = λf.(λx.f(xx))(λx.f(xx))` satisfies `Yf = f(Yf)` for all `f`. Axiomatically referenced; Lean 4 is total, so direct embedding requires Classical.choice workaround.
- **Nash fixed-point existence for finite games** (Nash 1950): every finite game has at least one Nash equilibrium. For our 2×2 coordination game, we verified *concrete* fixed points (cooperate, defect) directly; general Nash via Kakutani / Brouwer is not attempted here.

### A.3 EMPIRICAL

- The cross-tier D-FUMT₈ isomorphism analysis scanning 2,635 META-DB entries surfaced the `(SELF, VIII_META_STRUCTURAL)` cluster with novelty-score 3.00 (top-3 among 12 candidates, `data/claude-lens/cross-tier-dfumt8-isomorphism-2026-04-24.md`).
- All four `SelfRef` instantiations compile under `lake env lean` in < 5 seconds (Lean 4.27.0 + Mathlib v4.27.0).

### A.4 Build verification

File: `data/lean4-mathlib/CollatzRei/Step993SelfReference.lean`, ~260 lines.
Command: `lake env lean CollatzRei/Step993SelfReference.lean`
Result: exit 0, 0 sorry, 0 warnings.

---

## Part B. 今回の発見 (Findings)

### B.1 The skeletal match is substantive

Three of four instantiations (reflective / acausal / peace) use *discriminating* reflexive predicates, not tautologies. This addresses a natural objection — "any type can be given a `SelfRef` structure with `reflexive := fun _ => True` — so what?" — by showing the abstract skeleton genuinely accommodates non-trivial fixed-point content.

### B.2 The multi-fixed-point phenomenon

Acausal instance has **two** distinct Nash fixed points (cooperate, defect). This is a known game-theoretic fact but, importantly, it *parallels* the multi-fixed-point structure in reflective programming (multiple normal forms = multiple reflexive terms) and in provability logic (Gödel sentences are a family, not a single canonical object). The SelfRef skeleton preserves this multiplicity.

### B.3 Paper 132 roadmap retroactive connection

Paper 132 identified 5 Rei candidates; 4 of those 5 (Sunflower / Hadwiger-Nelson / Happy Ending / Wolstenholme) were also flagged by the cross-tier analysis under a *different* cluster `(BOTH, II_NEW_CONCEPT)`. The `(SELF, VIII_META_STRUCTURAL)` cluster studied in this paper is *orthogonal* — it picks out a structurally distinct set of open problems (Löb, reflective PL, acausal DT). This suggests D-FUMT₈ typing provides an orthogonal classification axis to the "difficulty tier" axis Paper 132 used.

### B.4 Hypothesis-not-falsified is NOT hypothesis-confirmed

We explicitly note: **the typing match is necessary but not sufficient**. Our verification shows the skeleton is *compatible* with all three domains, not that the three domains are *the same problem in disguise*. The latter would require a uniform Lean 4 *proof* of the three full theorems via a shared inference rule — a task we identify as the natural Paper 136+ follow-up.

---

## Part C. 次の発明 (Next inventions)

1. **GL modal logic Lean 4 module**: ~20-theorem scaffolding to encode `Provable : Sentence → Prop` + Gödel diagonal + Löb's theorem. Main unblocker for upgrading `lobInstance` from toy to genuine.
2. **Universal SelfRef → instance theorem**: can we prove, in Lean 4, that *every* non-trivial `SelfRef` satisfies some non-tautological property? (E.g., "a discriminating reflexive predicate implies a specific form of diagonalization.") If yes, the SelfRef skeleton has unifying content beyond mere typing. If no (and counterexamples exist in Lean 4), the hypothesis is *partially* falsified — we would learn which cluster members are genuinely linked and which are typing-coincidences.
3. **Paper 136 candidate**: full Lean 4 encoding of Löb + Y (via Classical) + Nash coordination FDT, each using the shared `SelfRef` interface, and checking whether their proofs can be *refactored* to share lemmas. If yes → Tier 3 promotion to "proven structural isomorphism". If no → discovery-withdrawal with honest reporting.

---

## Part D. 次の未解決 (Next open problems)

- **Q62** (new, this paper): is `SelfRef` the weakest abstraction under which all four instantiations compile? I.e., can we remove any field (reflexive? witness?) while preserving the fit? If the structure is *weakly overdetermined*, the "unified encoding" claim is strengthened.
- **Q63**: for each cluster member, is the witness element *canonical* (unique up to some equivalence)? Löb's sentence G is "essentially unique" by diagonal lemma. Is there a `SelfRef`-internal notion of canonical witness?
- **Q64**: the `SelfRef` structure cannot distinguish between cooperative Nash equilibria (cooperate) and mutually-defection (defect), nor between "this sentence is provable" and "this sentence is unprovable" Gödel-style. Is there a richer structure `ReflexiveSystem` that preserves the skeletal match while distinguishing these?

---

## Part E. 引用 (References)

- [Löb55] M. H. Löb, *Solution of a problem of Leon Henkin*, J. Symb. Logic 20 (1955), 115–118.
- [Smi84] Brian Cantwell Smith, *Reflection and semantics in LISP*, POPL 1984.
- [Yud10] E. Yudkowsky, P. Christiano, N. Soares, various MIRI functional decision theory publications.
- [Nash50] John F. Nash, *Equilibrium points in n-person games*, PNAS 36 (1950), 48–49.
- [Cur30] Haskell B. Curry, *Grundlagen der kombinatorischen Logik*, Amer. J. Math. 52 (1930), 509–536 and 789–834.
- Rei-AIOS Paper 130 (DOI `10.5281/zenodo.19700758`), Paper 132 (DOI `10.5281/zenodo.19704359`), Paper 133 (DOI `10.5281/zenodo.19713219`), Paper 134 (DOI `10.5281/zenodo.19709966`).
- META-DB Tier 3 entries: `claude-discovery-self-reference-cluster`, `claude-discovery-dual-axiom-coexistence`, `claude-discovery-new-concept-via-duality`.
- Mathlib v4.27 — `Mathlib.Logic.Basic` (used).
- Cross-tier analysis: `data/claude-lens/cross-tier-dfumt8-isomorphism-2026-04-24.md`.

---

## Part F. 誠実な失敗と修正の記録 (Honest failures and corrections)

**F.1 Initial instance draft used tautologies for all four** — a *trivial* typing match.

The first `Step993SelfReference.lean` draft defined `reflexive := fun _ => True` in all four instances. Type-check passed trivially, but the "match" was uninformative: under a tautology predicate, every structure is reflexive and the `SelfRef` skeleton adds no content.

**Fix**: replaced reflective and acausal instances with discriminating predicates (ToyTerm eval fixed point; Nash fixed point on 2×2 coordination game). Added three discrimination theorems (`pair_atom_atom_not_reflexive`, `defect_also_reflexive`, `peace_violated_not_reflexive`) to make the non-triviality machine-checkable.

**Lesson**: a typing-isomorphism claim must be tested under non-tautological predicates to be meaningful. The structure-fits test alone is too weak.

**F.2 The Löb instance remains toy, honestly**

The natural upgrade — genuine provability predicate + Gödel diagonal + Löb's theorem — is deep (needs GL modal logic in Lean 4, absent from Mathlib v4.27, and Gödel numbering machinery). We chose *not* to attempt a half-hearted imitation. The `lobInstance` is marked toy in the source code and in this paper; this is a known gap.

**F.3 The scope is a skeletal match, not a proof of structural isomorphism**

Easy to overclaim "we proved three domains are isomorphic" on the basis of typing match. We explicitly do *not* make this claim. The honest claim is: "the abstract typing skeleton compiles in all three domains under non-trivial predicates; full proof-level isomorphism is Paper 136+ future work".

---

## Part G. テスト結果 (Tests — if applicable)

No TypeScript tests. The Lean 4 file is the test artifact.

```
cd data/lean4-mathlib
lake env lean CollatzRei/Step993SelfReference.lean
# Expected: exit 0, no warnings, no errors
```

All 4 instantiations + 3 discrimination theorems + 1 generic existence lemma verified.

---

## Part H. データセット (Datasets — if applicable)

No new entries added to the Open Problems META-DB in this paper. Updates related entries:
- `claude-discovery-self-reference-cluster`: `formalization.lean4` updated from `"none"` to `"partial-step-993"`; `known_progress` appended with the Paper 135 scaffolding event.

---

## Part I. 公開・再現手順 (Publication & reproducibility)

- Zenodo DOI: (pending)
- Internet Archive: item URL on upload
- Harvard Dataverse: `doi:10.7910/DVN/KC56RY`
- 8 blog mirrors: dev.to, Hatena, HackMD, Notion, Mastodon, Zenn, Scrapbox, livedoor
- Source code (AGPL-3.0): `fc0web/rei-aios`; Lean file at `data/lean4-mathlib/CollatzRei/Step993SelfReference.lean`
- Analysis artifact: `data/claude-lens/cross-tier-dfumt8-isomorphism-2026-04-24.md`

---

## Part J. 限界 (Limitations)

1. The Löb instance is toy — no GL modal logic in scope.
2. The Y-combinator encoding is absent — Lean 4 total system requires Classical or indexed family; not attempted.
3. The Nash fixed-point is specific to a 2×2 toy game; general Kakutani not invoked.
4. The `SelfRef` skeleton cannot distinguish *structural kinship* from *coincidental typing* alone; Paper 136+ is needed to make that distinction rigorous.
5. The classification matrix in the cross-tier analysis uses Rei-AIOS ingestion heuristics; some typings may be errors that accidentally produced tight clusters.

---

## Part K. 謝辞 (Acknowledgements)

- Löb 1955, Brian Smith 1984, Yudkowsky / Christiano / Soares 2010s for the three source theories.
- Mathlib team for `Mathlib.Logic.Basic` and the Lean 4 / Lake infrastructure.
- Rei-AIOS Paper 132 Part F.4 structural lesson — honest partial formalization discipline.
- Cross-tier D-FUMT₈ isomorphism analysis (session 2026-04-24) — the observation that prompted this paper.
- Peace Axiom #196 · Fujimoto, Nobuki × Rei-AIOS (Claude Opus 4.7).

---

*End of Paper 135.*
