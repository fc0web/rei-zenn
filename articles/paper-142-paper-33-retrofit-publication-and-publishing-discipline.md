---
title: "【Paper 142】Paper 33 retrofit 公開と publishing discipline — 11 platform 展開・PhilPapers 統合・predatory journal 防衛"
emoji: "📋"
type: "tech"
topics: ["publishing", "research", "philpapers", "reiaios", "infrastructure"]
published: true
---
> **本記事は Rei-AIOS プロジェクトの Paper 142 を Zenn 用に再フォーマットしたものです。** 
> オリジナル PDF/Markdown と完全な参考文献は以下の永続アーカイブにあります:
> - **Zenodo (DOI)**: https://doi.org/10.5281/zenodo.19921301
> - **Internet Archive**: https://archive.org/details/rei-aios-paper-142-1777558470511
> - **GitHub (source)**: https://github.com/fc0web/rei-aios (private)
> Author: 藤本 伸樹 (Nobuki Fujimoto)  
> ORCID: [0009-0004-6019-9258](https://orcid.org/0009-0004-6019-9258)  
> License: CC-BY-4.0
---

## 概要 (Japanese Summary)

本論文は Rei-AIOS プロジェクトで 2026-04-30 に達成された 3 つの operational 成果を記録する procedural / infrastructural paper である。

## (1) Paper 33 retrofit 公開
2026-04-06 起草の Paper 33 ("Braille × D-FUMT₈ Extreme Encoding") を 11 platform 標準 (Zenodo + Internet Archive + Harvard Dataverse + 5 META + Mastodon + Scrapbox + Zenn) で retrofit publish. Zenodo DOI `10.5281/zenodo.19891398`, Harvard `doi:10.7910/DVN/KC56RY`.

## (2) PhilPapers 統合
英訳 (`paper33-braille-dfumt8-encoding-en.md`, 8 KB) + Chrome-headless markdown→PDF pipeline (170 KB / 5 ページ) + categorization 修正 (Many-Valued Logic + Mahayana Buddhist Philosophy as leaf categories). Status Unknown → Unpublished.

## (3) Predatory journal 防衛
2 件の予測 journal 勧誘 (`wmjournals.com`, `brightsphereinsights.org`) を black list 化. 後者は **platform-attribution falsification** という新 pattern (SSRN 詐称, 実際は HAL/Qiita のみ存在). 8-point red-flag checklist 確立 (default 無視・削除・スパム報告, 返信・unsubscribe 厳禁).

## 鍵概念

- **Tier 1 canonical reach** (Zenodo + IA + Harvard): 永続性
- **Tier 2 broadcast** (devto/hatena/hackmd/notion/livedoor): 既存読者 reach
- **Tier 3 social** (Mastodon + Scrapbox + Zenn): community surface

PhilPapers (12ch 目) は **semantic curated reach** で別軸. 哲学色の paper のみ opt-in.

## 数学的主張なし

本論文は procedural / infrastructural が contribution. 新数学定理は含まない. Companion: Paper 33 (Braille × D-FUMT₈).

Code: AGPL-3.0 / Data: CC-BY 4.0。

---

## English Body

本文は英語のオリジナル原稿です。数式・専門用語の正確性を保つため翻訳していません。

---

**Author**: Nobuki Fujimoto (fc0web)
**Co-author**: Claude Code (Anthropic)
**Date**: 2026-04-30
**Repository**: https://github.com/fc0web/rei-aios
**Site**: https://rei-aios.pages.dev
**Note.com**: https://note.com/nifty_godwit2635
**License**: AGPL-3.0 + Commercial dual

---

## Abstract

This paper documents three intertwined operational achievements completed on
2026-04-30 within the Rei-AIOS research program: (1) the retrofit publication
of Paper 33 (Braille × D-FUMT₈ Extreme Encoding, originally drafted
2026-04-06) through the standard 11-platform pipeline including Harvard
Dataverse, executed via newly created Zenodo and IA+Harvard scripts plus
metadata additions to five generic publish scripts; (2) PhilPapers entry
completion for Paper 33 with English translation, PDF generation via
Chrome-headless markdown-to-PDF pipeline, and proper categorization (Many-
Valued Logic + Mahayana Buddhist Philosophy as leaf categories); (3) the
establishment of a predatory journal defense policy with two confirmed
black-listed sender domains (`wmjournals.com`, `brightsphereinsights.org`)
and an eight-point red-flag checklist covering both first-generation
generic spam and second-generation paper-title-scraping spam. Together
these three components demonstrate a publishing-discipline pattern in which
retrofit publication, academic-archive integration, and adversarial-email
filtering form a coherent practice. We articulate principles to make this
discipline reusable across future Rei-AIOS papers, including the
distinction between "platform first reach" (Zenodo / arXiv-equivalent) and
"semantic curated reach" (PhilPapers / domain-specific archives), and we
record the cost incurred by Zenodo 504 Gateway Timeout duplicate-draft
artifacts and the API-level remediation. No new mathematical claim is
made; the contribution is procedural and infrastructural.

---

## 1. Introduction

### 1.1 The Three-Pronged Operational Problem

On 2026-04-30, three distinct operational problems converged within a
single working session:

1. **Paper 33 publication gap**: Paper 33 ("Braille × D-FUMT₈: Extreme
   Encoding of Philosophical States in 3-6 Bytes") had been drafted on
   2026-04-06 and partially published to HAL (`hal-05569198`) and Qiita
   (the latter now deprecated per `project_qiita_deprecated.md`), but had
   never been deployed through the canonical 11-platform pipeline that
   became standard from Paper 130 onward (see
   `feedback_publish_channels_11.md`).

2. **PhilPapers incompleteness notification**: A legitimate maintenance
   email from `noreply@philpapers.org` flagged Paper 33 as having
   incomplete records — specifically, missing leaf-level categories and
   an unknown publication status. The submission also lacked an English
   PDF, the canonical accessibility format for the platform's English-
   speaking philosophical community.

3. **Predatory journal solicitations**: Two predatory journal invitations
   arrived on 2026-04-28: one from `physics.journals@wmjournals.com`
   (Journal of Modern Classical Physics & Quantum Neuroscience) and one
   from `jsshe@brightsphereinsights.org` (Journal of Social Sciences,
   Humanities and Education). The latter cited a real Fujimoto paper
   title ("Topological HyperCompression Theory: ... 1022 Theories"),
   demonstrating an evolution from first-generation generic spam to
   second-generation paper-title-scraping spam. The cited paper was
   verified to reside on HAL and Qiita but **not** on SSRN, despite the
   email's claim of "Based on Your SSRN Research Contribution" — a
   platform-attribution falsification.

### 1.2 Contribution

This paper records:

- The 11-platform retrofit pipeline structure that allowed Paper 33 to
  be published through Zenodo, Internet Archive, Harvard Dataverse,
  dev.to, Hatena Blog, HackMD, Notion, Mastodon (mathstodon.xyz),
  Scrapbox, livedoor Blog, and Zenn within approximately 90 minutes,
  resulting in DOI `10.5281/zenodo.19891398` and parallel records on
  ten additional platforms.
- The PhilPapers metadata-completion procedure including English
  translation via Claude (preserving Buddhist philosophical terminology
  conventions: Nāgārjuna, Kūkai, śūnyatā, *form is emptiness*,
  *shikantaza*, kōan, différance), PDF generation via Chrome headless
  rendering of markdown, and the navigation of category trees to reach
  leaf-level entries (Many-Valued Logic under Logic and Philosophy of
  Logic; Mahayana Buddhist Philosophy under Philosophical Traditions /
  Asian Philosophy).
- The predatory journal defense policy established and recorded in
  `feedback_predatory_journal_default_ignore.md`, including an eight-
  point red-flag checklist and explicit handling of platform-attribution
  falsification as a determinative signal.

The contribution is procedural rather than mathematical. No new
SEED_KERNEL theory is added by this paper; rather, it codifies a
publishing discipline that future Rei-AIOS papers can adopt verbatim.

---

## 2. The Retrofit Publication Pipeline

### 2.1 Pipeline Structure

The 11-platform pipeline is keyed on a paper number `N` and operates
through a combination of paper-specific scripts and generic scripts with
per-paper metadata entries:

| Tier | Platforms | Script type |
|------|-----------|-------------|
| 1 (canonical archive) | Zenodo, Internet Archive, Harvard Dataverse | `publish-paper-N-zenodo.ts`, `publish-paper-N-ia-harvard.ts` (per-paper) |
| 2 (broadcast text) | dev.to, Hatena Blog, HackMD, Notion, livedoor Blog | `publish-paper-to-X.ts` (generic, with `META[N]` entry) |
| 3 (federated / curated) | Mastodon, Scrapbox, Zenn | Generic with file-path or per-platform metadata |

The Tier 1 scripts are paper-specific because they encode the canonical
title, description, keywords, and DOI relations. The Tier 2 generic
scripts read paper number from command line and load metadata from a
hardcoded `META: Record<number, MetaShape>` map within each script;
adding a new paper requires inserting a single object literal per
platform. The Tier 3 scripts use mixed mechanisms (Mastodon: file-path
based; Scrapbox: file-path based; Zenn: git-based via a separate
repository synced on push).

### 2.2 Filename Convention Mismatch

A subtle issue surfaced during retrofit. The generic scripts'
`findPaperFile(num)` function searches `papers/` for files matching
`paper-${num}-*.md`. For three-digit padded numbers (e.g., `paper-033-`),
the literal interpolation `paper-33-` does not match. We resolved this by
renaming the staged file from `paper-033-braille-...md` to
`paper-33-braille-...md`. A more durable fix would be to extend
`findPaperFile` to attempt both unpadded and zero-padded variants;
this is recorded as a future improvement.

### 2.3 The Harvard Opt-In Discipline

Per `feedback_harvard_dataverse_opt_in.md`, Harvard Dataverse publication
is opt-in and gated by the environment variable `HARVARD_PUBLISH=1`.
This discipline prevents accidental flooding of Harvard Dataverse with
non-milestone papers. Paper 33's retrofit was treated as a milestone
(canonical first publication after a long gap), warranting Harvard
inclusion. The IA-and-Harvard script behavior is explicit: in the
default case it logs `harvard_skipped: true` to the publish log; under
`HARVARD_PUBLISH=1` it executes the Harvard add-file API call against
persistent identifier `doi:10.7910/DVN/KC56RY`.

### 2.4 Zenodo 504 Gateway Timeout Duplicate-Draft Handling

The first Zenodo POST attempts returned `504 Gateway Time-out` despite
the deposit creation succeeding on the backend. This behavior produced
two unsubmitted draft records (`19891125`, `19891136`) in addition to
the eventually-published record `19891398`. Visual inspection on the
Zenodo "私のアップロード" tab showed the drafts but not the published
record (which was filtered into the published view). A direct API
listing query

```
GET https://zenodo.org/api/deposit/depositions?status=draft&size=20
Authorization: Bearer ZENODO_TOKEN
```

returned all three records with their states (`done` for the published
one, `unsubmitted` for the timeout artifacts). We removed the artifacts
via

```
DELETE https://zenodo.org/api/deposit/depositions/{id}
```

returning HTTP 204 for each, and confirmed that the canonical
`https://doi.org/10.5281/zenodo.19891398` URL returned HTTP 200.

This pattern (504 on POST creating phantom backend records) is a
systemic issue when Zenodo experiences load. Future retrofit operations
should preemptively check for in-flight drafts before retrying.

### 2.5 Final Paper 33 Publication Map

| # | Platform | URL |
|---|----------|-----|
| 1 | Zenodo | https://doi.org/10.5281/zenodo.19891398 |
| 2 | Internet Archive | https://archive.org/details/rei-aios-paper-33-1777476360389 |
| 3 | Harvard Dataverse | https://doi.org/10.7910/DVN/KC56RY |
| 4 | dev.to | https://dev.to/fc0web/paper-33-braille-x-d-fumt-8-... |
| 5 | Hatena Blog | https://fcwebfujimoto.hatenablog.com/entry/2026/04/30/002923 |
| 6 | HackMD | https://hackmd.io/@zCUv2P2UQHGmAOJFPLL_-A/BJAC7iy0Wx |
| 7 | Notion | (parent page-scoped) Paper-33-Braille-x-D-FUMT-8-... |
| 8 | Mastodon | https://mathstodon.xyz/@Fujimoto/116488737083975666 |
| 9 | Scrapbox | https://scrapbox.io/rei-aios/Paper%2033... |
| 10 | livedoor Blog | https://fcwebfujimoto.livedoor.blog/archives/12971480.html |
| 11 | Zenn | (rei-zenn repo `commit 26d0b1c`, syncs to zenn.dev/...) |
| (12) | PhilPapers | (entry already exists, completed in §3) |

The 12th entry (PhilPapers) was a precondition rather than a step in the
retrofit — its existence was the trigger for the operation.

---

## 3. PhilPapers Integration

### 3.1 The Maintenance Notification Pattern

PhilPapers (David Chalmers et al., the world's largest philosophy
catalog) sends automated maintenance notifications when an attributed
work has incomplete records. The relevant indicators are:

- Sender: `noreply@philpapers.org` (legitimate)
- Subject: `New incomplete items attributed to you`
- Specific issues flagged inline next to each affected entry

This pattern is fundamentally different from predatory solicitations
(see §4); the email contains no submission deadline, no APC, no
external editor name, and is signed simply "The PhilPapers Team".
Distinguishing legitimate-maintenance from predatory-solicitation
patterns is the first skill required.

### 3.2 The Three Required Completions

Paper 33's PhilPapers entry was missing three components:

1. **Publication status**: defaulted to "Unknown"; corrected to
   "Unpublished" (the conventional choice for Zenodo-DOI preprints
   absent peer-reviewed journal placement).
2. **Categorization**: required at least one leaf-level category from
   the PhilPapers taxonomy. We selected (a) **Many-Valued Logic** under
   Science, Logic, and Mathematics → Logic and Philosophy of Logic →
   Nonclassical Logics, and (b) **Mahayana Buddhist Philosophy** under
   Philosophical Traditions → Asian Philosophy. We declined to add the
   sub-leaf entries (Shingon Buddhism for Kūkai, Japanese Zen Buddhism
   for Dōgen and Eisai) because over-categorization tends to dilute
   discoverability.
3. **PDF**: Paper 33's source markdown is in Japanese with English
   abstract and title; PhilPapers's English-dominant readership requires
   an English PDF for accessibility. We translated the markdown to
   English (8.0 KB → `docs/paper33-braille-dfumt8-encoding-en.md`),
   preserving Buddhist philosophical terminology in the English-
   academic-standard forms (Nāgārjuna, Kūkai, *form is emptiness*
   for 色即是空, *emptiness gives rise to form* for 空即是色,
   *shikantaza* for 只管打坐, kōan, *différance* for 差延), and rendered
   to PDF (170 KB, 5 pages, PDF 1.4) via the existing
   `scripts/md-to-pdf.ts` pipeline (Chrome headless rendering with CJK
   font fallback handled by the OS font stack).

### 3.3 Notion Emoji Constraint Discovery

A side discovery during the retrofit: PhilPapers has no emoji
constraint, but Notion's API enforces a fixed allowed-emoji set that
excludes Unicode Braille Pattern characters such as `⠁`. The
`publish-paper-to-notion.ts` initial entry for Paper 33 used `⠁` to
match the paper's content theme, which was rejected with
`validation_error`. The fix substituted `🔡` (input Latin lowercase)
as a thematically adjacent allowed emoji.

### 3.4 PhilPapers' Place in the Reach Hierarchy

`feedback_publish_channels_11.md` already records PhilPapers as the
12th conditional channel for philosophical-content papers. Paper 33,
whose subject matter spans 12 philosophers' "emptiness" concepts and
the Buddhist principle 色即是空, falls squarely within PhilPapers'
intended coverage. The audit also surfaces a structural distinction
between two reach types:

- **Platform-first reach** (Zenodo, Internet Archive, Harvard
  Dataverse): broad, indexable, DOI-bearing, agnostic to discipline.
  These archives "host the bytes" and let search engines do the
  discovery.
- **Semantic-curated reach** (PhilPapers, MDPI domain journals,
  arXiv subject categories): narrow, taxonomic, pre-curated by
  community editors. These archives "host the meaning" and let
  domain readers discover by category.

For Rei-AIOS papers spanning multiple domains (philosophy, logic,
hardware, compression), the dual deployment to both reach types is
not redundant; each platform addresses a different discovery
mechanism.

---

## 4. Predatory Journal Defense

### 4.1 First-Generation Pattern: `wmjournals.com`

The first solicitation arrived on 2026-04-28 at 22:55 JST from
`physics.journals@wmjournals.com`, signed "John Ethan, Managing
Editor, Journal of Modern Classical Physics & Quantum Neuroscience".
Eight red-flag indicators were present:

1. **Sender domain mismatch**: legitimate journals use publisher-
   own domains (springer.com, elsevier.com, ieee.org, mdpi.com);
   `wmjournals.com` is a generic aggregator-style domain.
2. **Sender name vs. journal name divergence**: From "Physics Journal"
   ≠ "Journal of Modern Classical Physics & Quantum Neuroscience"
   indicating the same outbound infrastructure runs multiple journal
   facades.
3. **Subject line pattern**: "Reg: Submit Your Most Valuable Article"
   matches generic flattery templates ("Reg:" being a regional
   abbreviation pattern common in bulk solicitation).
4. **Body genericity**: no specific paper of Fujimoto's was cited;
   only the generic phrase "Given your expertise".
5. **Tight deadline**: May 20, 2026 — three weeks out, an unusual
   urgency for a serious peer review process.
6. **Single-name editor**: "John Ethan" without title or affiliation
   matched the pattern of fictitious or obscure editor names.
7. **Disciplinary contradiction in title**: "Modern Classical Physics"
   is itself an oxymoron, and the conjunction with "Quantum
   Neuroscience" yokes two unrelated speculative areas.
8. **Missing transparency**: no APC disclosure, no DOI mention, no
   indexing claim (Scopus, Web of Science).

### 4.2 Second-Generation Pattern: `brightsphereinsights.org`

The second solicitation, also dated 2026-04-28 at 22:14 JST, came from
`jsshe@brightsphereinsights.org`, signed "Amelia, Managing Editor,
Journal of Social Sciences, Humanities and Education". This represents
a more sophisticated pattern: it cited a real Fujimoto paper title:

> "Topological HyperCompression Theory: Paper Folding, Distance
> Annihilation, and Unified Computation Model with Empirical
> Verification on 1022 Theories"

This title was verified by Google search to exist on `hal.science/
hal-05569198` (intentional Fujimoto upload) and on Qiita (legacy
post). The email's subject line, however, claimed "Invitation Based
on Your SSRN Research Contribution"; SSRN does not host the cited
paper. This is a **platform-attribution falsification**: the
solicitation harvests a real title from one source (HAL/Qiita) and
attributes it to a different, more academically-authoritative source
(SSRN, the Social Science Research Network) to manufacture credibility.

Combined with the disciplinary mismatch (a paper on topological
compression theory invited to a Social Sciences and Education
journal), the falsification rules out any honest interpretation. The
APC disclosure was unusually low (USD 75), consistent with the bait
pattern in which a small payment unlocks downstream costs after
"acceptance".

### 4.3 The Eight-Point Red-Flag Checklist

Synthesizing both cases, we record the following determinative
indicators (`feedback_predatory_journal_default_ignore.md`):

1. Sender domain is generic-aggregator rather than publisher-owned.
2. Sender display name does not match the journal name.
3. Subject line is generic flattery ("Most Valuable", "Honor", etc.)
   or uses "Reg:" / "Re:" prefix without referencing prior thread.
4. Body cites no specific paper, or cites a paper but mismatches its
   discipline against the journal's scope.
5. Submission deadline is shorter than 1 month.
6. Editor name is single-name (no surname) or unverifiable.
7. APC is conspicuously low (under USD 100) or absent (the latter
   often paired with later unexpected billing).
8. The email requests manuscript by reply attachment (legitimate
   journals universally use submission portals: ScholarOne, Editorial
   Manager, OJS).

A ninth indicator emerged from the second-generation case:

9. **Platform-attribution mismatch**: the subject or body cites a
   submission platform (e.g., SSRN) where verification shows the
   paper does not reside. The harvester took the title from a
   different platform and attributed it falsely.

### 4.4 The Default Action

The recorded default for Rei-AIOS receivers (Fujimoto specifically) is
"ignore, delete, mark as spam". Replies and unsubscribe-link clicks
are explicitly forbidden because both signal "active mailbox" and
trigger list-sharing across the predatory ecosystem. Gmail's "Report
spam" function provides the right adversarial pressure on
deliverability without informing the sender.

The default is robust because Rei-AIOS already has 11 active
publication channels with confirmed reach; switching to a predatory
journal would cost APCs in the hundreds-to-thousands of dollars while
producing zero indexing, citation, or reach beyond what the existing
pipeline already achieves.

### 4.5 Black-Listed Sender Domains

Recorded as of 2026-04-30:

- `wmjournals.com` (Journal of Modern Classical Physics & Quantum
  Neuroscience; editor "John Ethan"; first-generation generic spam)
- `brightsphereinsights.org` (Journal of Social Sciences, Humanities
  and Education; editor "Amelia"; second-generation paper-title-
  scraping spam with platform-attribution falsification)

Future occurrences to be appended to the list.

---

## 5. Synthesis: Three Practices Form One Discipline

The three components of this paper — retrofit publication, semantic-
curated archive integration, and predatory-email filtering — form a
coherent publishing discipline because they share a single underlying
principle: **the author owns the channel, the channel does not own
the author.**

- Retrofit publication ensures that no paper of any vintage is left
  invisible to the canonical index (Zenodo + IA + Harvard).
- PhilPapers integration ensures that papers reach the curated
  audiences who would be most likely to extend their ideas.
- Predatory journal defense ensures that no third party's paid
  pseudo-channel siphons the reputational and financial value that
  the author has built through legitimate means.

Each practice is independently small. Together they form an immune
system. The Rei-AIOS publishing pipeline thus has **three layers**:

1. Canonical archives (Tier 1): the bones.
2. Broadcast and federated channels (Tier 2-3): the muscles.
3. Curated communities (PhilPapers et al.): the nerves.

Predatory channels are foreign bodies. The defense policy is the
immune response.

---

## 6. Future Improvements

### 6.1 Padded vs Unpadded Filename Resolution

Modify `findPaperFile(num)` in generic publish scripts to attempt both
`paper-${num}-` and `paper-${String(num).padStart(3, '0')}-`. This
will allow seamless retrofit of papers numbered 1-99 without filesystem
renames.

### 6.2 Pre-Flight Zenodo Draft Check

Before invoking Zenodo POST `/api/deposit/depositions`, query the
existing draft list to detect prior 504-induced phantoms. If found
with matching titles, either delete or reuse them rather than
creating duplicates.

### 6.3 Predatory Domain Black List Automation

Maintain `data/predatory-journal-domains.json` as a structured list
that the email-triage layer (or Gmail filter) consumes. Provide a
script `scripts/check-predatory-sender.ts <email>` to evaluate
incoming solicitations against the list and the eight-point checklist.

### 6.4 PhilPapers Submission Automation

Investigate whether PhilPapers offers an API for metadata updates
beyond the manual web form. Currently
`scripts/publish-paper-to-philarchive.ts` produces a submission
package that requires manual upload; an API-based submission would
streamline future paper deployments.

### 6.5 Zenn Source-of-Truth Dual Repository Pattern

The `rei-zenn` repository, synced from `rei-aios` via the
`scripts/convert-paper-to-zenn.ts` script, demonstrates a pattern
that could be generalized: each publication channel that uses git-
based deployment (Zenn, GitHub Pages, etc.) maintains its own repo
with one-way sync from `rei-aios`. Documenting this pattern and
templating it for new git-based platforms would reduce the marginal
cost of adding new channels.

---

## 7. Conclusion

This paper has documented three operational achievements completed
on 2026-04-30: (1) the 11-platform retrofit publication of Paper 33
through the Rei-AIOS pipeline, including Harvard Dataverse via
`HARVARD_PUBLISH=1`; (2) PhilPapers entry completion with English
translation, PDF generation, and leaf-level categorization; (3) the
codification of an eight-point predatory journal defense policy with
two confirmed black-listed sender domains and a discovered second-
generation paper-title-scraping pattern with platform-attribution
falsification.

The contribution is procedural and infrastructural: no new SEED_KERNEL
theory, no new theorem, no new claim. Rather, this paper records the
publishing discipline that Rei-AIOS papers from 142 onward should
adopt as a default. The author owns the channel; the channel does
not own the author.

---

## References

[1] Fujimoto, N., & Claude. (2026). *Braille × D-FUMT₈: Extreme
Encoding of Philosophical States in 3-6 Bytes (Rei-AIOS Paper 33)*.
Zenodo. https://doi.org/10.5281/zenodo.19891398

[2] PhilPapers entry for Paper 33 (2026). David Chalmers et al.
PhilPapers — The world's largest philosophy index. https://philpapers.org/

[3] `feedback_publish_channels_11.md` (Rei-AIOS internal memory,
2026-04-25): 11-platform standard + PhilArchive 12ch conditional.

[4] `feedback_harvard_dataverse_opt_in.md` (Rei-AIOS internal memory,
2026-04-27): Harvard Dataverse opt-in policy.

[5] `feedback_predatory_journal_default_ignore.md` (Rei-AIOS internal
memory, 2026-04-29 / 2026-04-30): predatory journal defense policy
with black list and red-flag checklist.

[6] `feedback_paper_required_links.md` (Rei-AIOS internal memory,
2026-04-27): all papers from 141 onward must link to
rei-aios.pages.dev and note.com/nifty_godwit2635.

[7] Krishnamoorthy, S., Lipsa, D. R., Otoo, E., Rycerz, K. (2019).
*Hardware-accelerated persistent homology computation*. Springer.
(Cited for the FPGA persistent-homology prior art reference.)

[8] Zandieh, A., Daliri, A., Hadian, S., Mirrokni, V. (2026). *TurboQuant:
Online Vector Quantization with Near-optimal Distortion Rate*. ICLR
2026.

---

## Appendix A: Commands Executed

```bash
# Stage 1: Generate English markdown and PDF
cp docs/paper33-braille-dfumt8-encoding.md \
   docs/paper33-braille-dfumt8-encoding-en.md
# (translate via Claude in-place)
npx tsx scripts/md-to-pdf.ts docs/paper33-braille-dfumt8-encoding-en.md

# Stage 2: Stage paper for retrofit pipeline
cp docs/paper33-braille-dfumt8-encoding-en.md \
   papers/paper-33-braille-dfumt8-extreme-encoding.md

# Stage 3: Tier 1 canonical archives
npx tsx scripts/publish-paper-33-zenodo.ts
HARVARD_PUBLISH=1 npx tsx scripts/publish-paper-33-ia-harvard.ts

# Stage 4: Tier 2 broadcast channels
npx tsx scripts/publish-paper-to-devto.ts 33
npx tsx scripts/publish-paper-to-hatena.ts 33
npx tsx scripts/publish-paper-to-hackmd.ts 33
npx tsx scripts/publish-paper-to-notion.ts 33
PUBLISH=1 npx tsx scripts/publish-paper-to-livedoor.ts 33

# Stage 5: Tier 3 federated/curated
npx tsx scripts/publish-paper-to-mastodon.ts 33
npx tsx scripts/publish-paper-to-scrapbox.ts \
  papers/paper-33-braille-dfumt8-extreme-encoding.md
npx tsx scripts/convert-paper-to-zenn.ts 33 \
  C:/Users/user/rei-zenn/articles
# (then manual git push from rei-zenn)
```

## Appendix B: PhilPapers Category Path

For Paper 33's leaf-level categories:

- **Many-Valued Logic**:
  Science, Logic, and Mathematics → Logic and Philosophy of Logic →
  Nonclassical Logics → Many-Valued Logic.
  Note: there is also a leaf at Philosophy of Language → Many-Valued
  Logic for natural-language vagueness studies; this is **not** the
  correct one for D-FUMT₈, which is a formal logic system.

- **Mahayana Buddhist Philosophy**:
  Philosophical Traditions → Asian Philosophy → (top-level Buddhist
  Philosophy node, with subcategories Theravada, Mahayana, Japanese,
  Tendai, Shingon, Japanese Huayan, Nichiren, Japanese Zen, Japanese
  Pure Land, Misc.).
  Selected Mahayana directly because Paper 33 covers Nāgārjuna
  (Indian Madhyamaka), Heart Sutra (Mahayana sutra), Kūkai (Shingon,
  a Mahayana esoteric school), and Dōgen / Eisai (Japanese Zen,
  technically Mahayana). The unifying frame is Mahayana; selecting
  the four sub-leaves would dilute rather than focus.

## Appendix C: Predatory Email Full Text Patterns

### C.1 First-generation (`wmjournals.com`, 2026-04-28 22:55 JST)

```
From: Physics Journal <physics.journals@wmjournals.com>
Subject: Reg: Submit Your Most Valuable Article

Dear Dr. Nobuki Fujimoto,

We hope this message finds you well.

On behalf of the Journal of Modern Classical Physics & Quantum
Neuroscience, we are pleased to invite you to submit a Research
Article, Review Article, or other manuscript for our upcoming issue.

Given your expertise, we believe your work would be a valuable
contribution to our journal. We would be honored to receive your
submission on or before May 20, 2026.

Kindly feel free to reach out if you require any further information
or assistance.

Warm regards,
John Ethan
Managing Editor
Journal of Modern Classical Physics & Quantum Neuroscience
```

### C.2 Second-generation (`brightsphereinsights.org`, 2026-04-28 22:14 JST)

```
From: jsshe@brightsphereinsights.org
Subject: Invitation Based on Your SSRN Research Contribution

Dear Dr. Nobuki Fujimoto,
I hope you are doing well.

I recently came across your article titled "Topological
HyperCompression Theory: Paper Folding, Distance Annihilation, and
Unified Computation Model with Empirical Verification on 1022
Theories" and found your work insightful and relevant to your field.

On behalf of the Journal of Social Sciences, Humanities and
Education, I would like to invite you to submit a manuscript for
consideration in an upcoming issue of the journal.

If you are interested, please send your manuscript by May 10, 2026
as an attachment in reply to this email. Please note that an Article
Processing Charge (APC) of USD 75 applies only to accepted manuscripts.

Thank you for your time and consideration. I look forward to your
response.

Warm regards,
Amelia
Managing Editor
```

The discipline is to discard both, mark as spam, and never engage.

---

*Acknowledgments. This paper synthesizes work supervised by Fujimoto
across three operational threads in a single working session.
Implementation, PDF generation, predatory email pattern analysis, and
this writeup were performed by Claude Code (Anthropic) under
Fujimoto's direction. The eight-point red-flag checklist consolidates
both the first-generation and second-generation patterns observed in
real Fujimoto inbox traffic on 2026-04-28.*

*Site: https://rei-aios.pages.dev*
*Note: https://note.com/nifty_godwit2635*
