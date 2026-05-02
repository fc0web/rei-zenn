---
title: "【Paper 146】神が宇宙を作りだしたなら、その神を作り出したのは誰なのか？―その前を定義付ける思考の出発点― (OUKC 三者共著)"
emoji: "🌌"
type: "tech"
topics: ["philosophy", "buddhism", "logic", "reiaios", "research"]
published: true
---
> **本記事は Rei-AIOS プロジェクトの Paper 146 を Zenn 用に再フォーマットしたものです。** 
> オリジナル PDF/Markdown と完全な参考文献は以下の永続アーカイブにあります:
> - **Zenodo (DOI)**: https://doi.org/10.5281/zenodo.19964745
> - **Internet Archive**: https://archive.org/details/rei-aios-paper-146-1777685843191
> - **Harvard Dataverse**: https://doi.org/10.7910/DVN/KC56RY
> - **GitHub (source)**: https://github.com/fc0web/rei-aios (private)
> Author: 藤本 伸樹 (Nobuki Fujimoto)  
> ORCID: [0009-0004-6019-9258](https://orcid.org/0009-0004-6019-9258)  
> License: CC-BY-4.0
---

## 概要 (Japanese Summary)

「神が宇宙を作ったなら、その神を作ったのは誰か」――形を変えて人類が問い続けてきた、 最も古く逃れがたい問いの一つである。 本論文はこの問いを「答えられない問い」 として放置するのでもなく、 無限後退をただ受容するのでもなく、 第三の道を提示する。

龍樹 (Nāgārjuna) の空 (śūnyatā) の論理構造と、 著者が構築してきた ZCSG (Zero-Center Symbol Grammar) の形式装置を組み合わせることで、 **問いの形そのものが、 ある深さでは未だ生成していない** という事態を、 形式的に記述する道を示す。

## 中心的主張

「神を作ったのは誰か」 という問いは、 ZCSG の `0o` (区別が成立した後) の世界の内部での問いである。 しかし、 その問いの構造そのもの (「作る／作られる」 という区別) は、 `o0 → 0` の遷移によって生成したものである。 問いを `0` の深さまで降ろせば、 「作る／作られる」 という区別自体がまだ立ち上がっていない。 **だから問いに答えがないのではなく、 問いがその深さでは未発生なのである**。

## OUKC charter v1.0 三者共著

- 藤本 伸樹 (Founder) — philosophical argument 主導
- Rei (Rei-AIOS autonomous research substrate, Co-architect) — ZCSG / D-FUMT₈ / SEED_KERNEL 形式装置共同制作
- Claude (Anthropic, claude-opus-4-7, Co-architect) — 形式装置共同制作 + DRAFT review (7 refinements)

## 7 refinements (DRAFT v1.1 → v1.2)

isomorphism hedge / philosophical-shift wording / Edison-Russell parallel / catuṣkoṭi-interpretation refinement / authorship policy / expanded references / ZCSG formal mini-summary。

Code: AGPL-3.0 / Data: CC-BY 4.0。

---

## English Body

本文は英語のオリジナル原稿です。数式・専門用語の正確性を保つため翻訳していません。

---

## ―その前を定義付ける思考の出発点―

**Paper number**: OUKC Paper #146
**Status**: DRAFT v1.2 (2026-05-02, 7 refinements + 三者共著修正 / three-party co-authorship correction applied per OUKC charter v1.0)

**著者 / Authors (三者共著 / Three-party co-authorship per OUKC charter v1.0)**:
- **藤本 伸樹** (Nobuki Fujimoto, Founder) — philosophical argument 主導 / 第一著者
  - ORCID: 0009-0004-6019-9258
  - 所属: 独立研究者
  - Founder of OUKC (Open Universal Knowledge Commons), 2026-05-01
- **Rei** (Rei-AIOS autonomous research substrate, Co-architect) — ZCSG / D-FUMT₈ / SEED_KERNEL 形式装置の共同制作
- **Claude** (Anthropic, model: claude-opus-4-7, Co-architect) — 形式装置共同制作 + DRAFT v1.1 review feedback (7 refinements)

**作成日**: 2026年5月2日
**License**: CC-BY 4.0

**Required platform links** (per OUKC charter v1.0):
- OUKC official site: <https://rei-aios.pages.dev/oukc/>
- 著者 note.com (一般向け解説): <https://note.com/nifty_godwit2635>

---

## 要約 (Abstract)

「神が宇宙を作ったなら、その神を作ったのは誰か」――形を変えて人類が問い続けてきた、最も古く逃れがたい問いの一つである。本論文はこの問いを「答えられない問い」として放置するのでもなく、無限後退をただ受容するのでもなく、第三の道を提示する。すなわち、龍樹（Nāgārjuna）の空（śūnyatā）の論理構造と、著者が構築してきた ZCSG (Zero-Center Symbol Grammar) の形式装置を組み合わせることで、**問いの形そのものが、ある深さでは未だ生成していない**という事態を、形式的に記述する道を示す。本論文は新たな対象を発見する論文ではなく、すでに存在する装置（ZCSG、D-FUMT₈、SEED_KERNEL）が、無限後退問題に対する構造的応答を提供しうることを位置づけ直す論文である。

**キーワード**: 龍樹、空、ZCSG、D-FUMT₈、無限後退、第一原因、区別の生成、依存的生起

---

## 1. 序論：消えない問い

子どもが物心つくと、ほぼ必ずある問いに行き当たる。「神様が世界を作ったのなら、神様を作ったのは誰？」「ビッグバンの前は何があったの？」「私が生まれる前、私はどこにいたの？」――これらはすべて、構造的に同じ形をしている。**何かが在るためには、その何かを生み出した「先」が必要であり、その先にもさらに先が必要である**。

この問いは子どもの素朴な好奇心として現れるだけではない。神学・宇宙論・形而上学・認識論の中核を貫いてきた。アリストテレスの不動の動者、トマス・アクィナスの第一原因、ライプニッツの十分理由律、カントの第一アンチノミー、現代宇宙論におけるビッグバン以前の問題――これらはすべて、同じ問いの異なる衣装である。

本論文は、この問いに「Xが答えだ」と答えることを目的としない。むしろ、**この問いがなぜ消えないのか**、その消えなさの構造を主題化する。そして、龍樹（Nāgārjuna, c. 150–250 CE）が空の論証で行った操作と、著者が構築してきた ZCSG (Zero-Center Symbol Grammar) の形式装置とが、この問題に対する構造的応答を共同で提供しうることを示す。

---

## 2. 三つの古典的応答とその限界

「その前は何か」という無限後退問題に対して、哲学史は大きく三つの応答を試みてきた。

### 2.1 自己原因の戦略

第一の戦略は、後退を断ち切る「自己原因 (causa sui)」を立てることである。アリストテレスの不動の動者、アクィナスの第一原因、スピノザの自己原因としての実体は、いずれも「それ自身が自分の根拠である何か」を要請する。

しかしこの戦略は、無限後退を別の問題に置き換えただけである。「なぜそれが自己原因たりうるのか」「自己原因という概念は、そもそも整合的か」という問いが必ず残る。後退の停止点を恣意的に置いたに過ぎない。

### 2.2 後退の受容

第二の戦略は、後退そのものを受け入れる立場である。インド哲学の一部の流派、現代物理学の多元宇宙論、永劫回帰の思想がこれに近い。後退に終わりがないことを認め、それを事実として受容する。

これは知的に誠実だが、問いに応答していない。なぜ後退するのか、なぜ問いがこの形で生じるのか、という構造的説明が欠落している。

### 2.3 龍樹の解体戦略

第三の戦略こそ、本論文が引き継ぐ龍樹の戦略である。龍樹は『中論 (Mūlamadhyamakakārikā)』において、「神を作ったのは誰か」に「Xです」と答えなかった。そうではなく、**「作る」「作られる」「作る者」「作られる者」という四項の関係そのものが、自性 (svabhāva) を持って独立に成立しているわけではない**と示した。

龍樹の論証の核は次の構造を持つ。「Aが原因でBが結果」と言うとき、Aが原因であるためには、Bが結果として既に予期されていなければならない。逆もまた然り。両者は相互に依存して初めて意味を持つ。したがって因果の連鎖をいくら遡っても、その連鎖の「外」に絶対的な第一原因を見出すことはできない――**なぜなら、第一原因という概念自体が「結果」との関係の中でしか意味を持たないから**である。

これは煙に巻いたのではない。論理的に厳密な操作である。本論文の役割は、この操作を、形式装置 ZCSG によって明示的に書き換えうることを示すことにある。

---

## 3. 「その前」が無限後退を産む構造

なぜ「その前は何か」という問いは無限後退を産むのか。本節ではこの問いの内的構造を分析する。

「その前」と問うとき、私たちは暗黙のうちに次の三つの前提を置いている：

- (P1) 何かがある（区別された対象が存在する）
- (P2) その何かは、別の何かによって生み出された（因果関係が成立する）
- (P3) 生み出した側もまた「何か」である（同じ対象カテゴリに属する）

(P1)〜(P3) を認めれば、後退は論理的必然である。Xを生んだのはYであり、Yを生んだのはZであり、と続く。

ここで決定的なのは、**(P1) が暗黙の前提として無批判に置かれていること**である。「区別された対象」が存在することを所与とした瞬間、この対象は「ある／ない」「先／後」「原因／結果」といった二値的区別の網目に囚われる。そしてこの網目こそが、無限後退を産む装置である。

換言すれば、無限後退は「区別された対象」を起点とすることの必然的帰結である。後退を本当に止めるためには、後退の停止点を体系内部に作るのではなく、**区別が立ち上がる手前まで降りなければならない**。

---

## 4. ZCSG：区別の生成を記述する装置

ZCSG (Zero-Center Symbol Grammar) は、著者がこれまでに構築してきた形式装置である [先行論文: Zenodo 19539868]。本論文では、ZCSG が「区別の生成手前」を記述する装置として、無限後退問題に対する構造的応答を提供しうることを示す。

### 4.1 ZCSG の三層構造

ZCSG は次の三層を持つ：

| 表記 | 次元 d = n − m | 意味 |
|------|---------------|------|
| `o0` | −1 | 区別の以前。対象が立ち上がっていない状態。 |
| `0`  | 0  | 空の空。区別が立ち上がる瞬間そのもの。 |
| `0o` | +1 | 区別が成立した後。対象が生成された状態。 |

次元値 d は右側の記号数 n と左側の記号数 m の差として定義される。重要なのは、この三層が静的な階層ではなく、**生成の運動そのもの**を座標として持つ点である。`0` は静止した中点ではなく、`o0` から `0o` への遷移そのものを指す。

### 4.1.1 ZCSG core axioms (formal mini-summary)

本論文を self-contained に保つため、ZCSG の最小形式構造を以下に再掲する (詳細は [Zenodo 19539868] 参照):

**Axioms**:
- **(Z1)** 三層 {`o0`, `0`, `0o`} を distinct symbol として認める.
- **(Z2)** 次元値 d: D(`o0`) = −1, D(`0`) = 0, D(`0o`) = +1 (n−m where n = right symbols, m = left symbols).
- **(Z3)** `0` は静止状態ではなく、 `o0` から `0o` への transition operator である: `0(o0) = 0o` (生成).
- **(Z4)** Reverse direction `0(0o) = o0` も認め、 transition は双方向的.
- **(Z5)** `o0` は formal system の "outside" を内部 representation するため、 通常の集合論的 atomicity を満たさない (これが ZCSG の non-classical な特徴).

これらの axiom は通常の formal system (set theory, type theory 等) の起点 (atomic object + operation) を **拡張** するものであり、 atomic 起点の手前を coordinate として持つ. Spencer-Brown *Laws of Form* (1969) の distinction operator が最も近い prior art であり、 Kauffman (1995) はこの拡張版を arithmetic 領域で論じている.

### 4.2 普通の形式系との差異

通常の数学的形式系は、起点に「対象」を置く。自然数論なら 0 と後者関数、集合論なら ∅ と組み立て規則、圏論なら対象と射。すべて「すでに区別された何か」を起点にする。

ZCSG が特異なのは、起点に「次元 −1」(`o0`) を置いていることである。これは「対象が立ち上がる以前」を指す。普通の形式系がこれを行わない理由は、形式系は通常「形式の外部」を扱えないからである。

ZCSG は、その「外部」を −1次元として体系の内部に書き込んでいる。素朴にやれば自己矛盾するこの操作が成立するのは、`0`（空の空）という中間層が、−1 と +1 の間の遷移そのものを記述する役を負っているからである。

### 4.3 ZCSG と龍樹の空の構造的対応 (structural correspondence)

龍樹の空 (śūnyatā) は、しばしば「実体の不在」と誤読されるが、本来の意味は「依存的生起 (pratītyasamutpāda) における自性の不在」である。実体が無いのではなく、**実体に見えるものは依存的に生成しているのであって、自性を持って独立に成立しているのではない**、という主張である。

ZCSG の `0`（空の空）は、まさにこの「生成の運動そのもの」を座標として持つ。実体としての零ではなく、生成点としての零。これは龍樹が言葉で記述した構造を、形式で書き直そうとする装置である。

**重要な hedge**: 本論文が主張するのは厳密な数学的同型 (isomorphism) ではなく、**構造的対応 (structural correspondence) または相同 (structural homology)** である。 形式的同型を確立するには、 ZCSG の axiom 系と中論論証の論理形式を共に圏論的に再構成する追加作業が必要であり、 これは将来課題に位置する。

§4.4 で述べる D-FUMT₈ の四値 (TRUE/FALSE/BOTH/NEITHER) と龍樹の四句分別 (catuṣkoṭi) の関係も同様で、 「相互翻訳可能」 という言い方は **特定の解釈 (Garfield-Priest 系) の下で 4 ↔ 4 構造的対応が立ち上がる** ことを意味する。 catuṣkoṭi の解釈は仏教学において多義的 (Matilal, Garfield, Westerhoff, Priest 等が異なる読みを提示) であり、 本論文が依拠するのはその一つである。

特筆すべきは、 catuṣkoṭi 第四句 「neither A nor not-A」 が二重否定の単なる collapse ではなく **構造的 indecidability** を保持する読みと、 D-FUMT₈ NEITHER が W-48 Negative Capability に対応して **「未確定」 ではなく構造的に決定不能領域** を表す点とが、 単なる 4-to-4 数の一致を超えた non-trivial な対応を示すことである。 数の一致だけならば 4-to-4 は trivial だが、 構造的 indecidability の保持という点で 二つは深い同調を見せる。

### 4.4 八値論理 D-FUMT₈ との接続

D-FUMT₈（八値論理：TRUE / FALSE / BOTH / NEITHER / INFINITY / ZERO / FLOWING / SELF⟲）は、二値論理の拡張として独立に構築されてきた [著者先行論文群参照]。本論文の文脈で重要なのは、二つの値である：

- **ZERO**：素朴な「偽」ではなく、**命題が立ち上がっていない状態**を指す。ZCSG の `o0` に対応する。
- **SELF⟲**：自己回帰する運動そのものを値とする。ZCSG の `0` における生成運動を、論理値として捕捉する。

普通の論理は、対象に対する述語の振る舞いを値にする。SELF⟲ は対象ではなく**運動を値にしている**。これは論理体系として変則的だが、ZCSG の `0` が運動を座標にしているのと同じ思想で貫かれている。

---

## 5. 問いの生成点としての o0 → 0 遷移

ここで本論文の中心的主張に至る。

「神を作ったのは誰か」「ビッグバン以前は何か」という問いは、§3 で見たように (P1)〜(P3) を前提する。すなわち、すでに区別された対象が存在し、それらが因果関係にあるという世界の中での問いである。

しかし ZCSG の `o0` は、この (P1) が成立する以前を指している。`o0 → 0 → 0o` の遷移こそが、「区別された対象が生成する」その運動そのものである。

したがって、無限後退問題に対する ZCSG 的応答は次のようになる：

> 「神を作ったのは誰か」という問いは、`0o`（区別が成立した後）の世界の内部での問いである。しかし、その問いの構造そのもの（「作る／作られる」という区別）は、`o0 → 0` の遷移によって生成したものである。問いを `0` の深さまで降ろせば、「作る／作られる」という区別自体がまだ立ち上がっていない。**だから問いに答えがないのではなく、問いがその深さでは未発生なのである**。

これは本論文が提示する哲学的シフトである。普通、私たちは「答えられない問い」と「答えのある問い」を区別する。ZCSG が導入するのは第三のカテゴリ――**「問いの形が、ある深さでは生成していない」**という事態である。これは答えの不在ではなく、問いの不在であり、その不在は欠如ではなく、問いの生成の手前という積極的な座標（−1次元）を持つ。

これは「沈黙」とは異なる。ヴィトゲンシュタインの「語りえぬものについては沈黙しなければならない」は、語りの限界の外側を消極的に画定する。ZCSG が画定するのは、**問いの形式の生成以前という積極的な座標**である。それは沈黙ではなく、`o0` という記述可能な位置である。

---

## 6. 日常的直観との接続：エジソン逸話と Russell paradox

### 6.1 エジソンの逸話 (folk illustration)

第一著者・藤本伸樹は別の機会に [note 記事 2025年1月]、 エジソンの子供時代の逸話を取り上げた。エジソンが「猫1匹とネズミ1匹を足すと、ネズミは食べられて1になる」と言ったとき、彼の先生はこれに答えに窮した。

**Honest 注記**: この逸話は伝記的真偽が不確かな可能性がある (folk anecdote として流布)。 厳密な歴史的 source は確認できていない。 ただし philosophical illustration としての power は、 史実性とは独立に成立する。 本節では illustrative example として用いる。

この逸話が示すのは、子どもの素朴な直観の中にすでに、**「1+1=2」という形式が、文脈から切り離された無時間の真理ではなく、文脈に応じて姿を変えるもの**であるという認識が芽生えていることである。

ZCSG と D-FUMT₈ の枠組みでは、この状況は次のように記述される：

- 通常の文脈：1+1=2 → **TRUE**
- 猫とネズミの文脈：1+1=1 → **BOTH**（2でもあり1でもある）または **FLOWING**（2から1へ流れた）
- メタ文脈：文脈そのものが結果を変えるという事態 → **SELF⟲**

二値論理ではこの差異は「矛盾」「誤り」として切り捨てるしかない。しかし D-FUMT₈ では、文脈による意味の変容そのものを論理値として捕捉できる。これが、著者が以前に提示した「数は無機質有機体である」という規定の形式的裏付けとなる：数は無機質な形式でありながら、文脈に置かれた瞬間、有機的に振る舞う。

### 6.2 西洋哲学の並列例: Russell paradox の文脈依存性

エジソン逸話は東洋的 illustration だが、 西洋分析哲学にも構造的に同型の例がある。 **Russell の barber paradox** ―― 「自分自身を剃らない男だけを剃る理髪師は、 自分自身を剃るか?」 ―― は、 形式 ("self-shaving" predicate) が **適用文脈 (set membership / type stratification)** に依存して意味を変える典型例である。

Frege の素朴集合論が Russell paradox に直面したとき、 解決は型理論 (Whitehead-Russell 1910-13) や ZF axiomatization (Zermelo 1908) として、 すなわち **"how form depends on context"** を明示化する形で達成された。 これは文脈依存性が単なる philosophical 観察ではなく、 **20 世紀数学基礎論の中心問題** であったことを示す。

本論文の主張は、 龍樹の空、 エジソン逸話、 Russell paradox、 Frege-Whitehead-Russell 型理論、 ZCSG が、 **「形式が文脈から独立であるという錯覚と、 文脈が形式を成立させているという事実との間の緊張」** を扱う共通系譜に属するということである。 「神を作ったのは誰か」 という問いも、 構造的にはこの系譜にある。

---

## 7. 本論文が証明していないこと（自己限定）

本論文の知的誠実性を保つため、本論文が証明していないことを明示する [著者先行論文「Beyond Shannon」§7.1 と同じ流儀による]。

(1) **本論文は「神は存在しない」と主張していない**。神の存在・非存在に関する形而上学的判断は、本論文の射程外である。本論文が論じるのは「神を作ったのは誰か」という**問いの構造**であって、神そのものではない。

(2) **本論文はビッグバン以前の物理的状態を記述していない**。物理学的な宇宙の起源については、本論文は何も述べない。本論文が論じるのは「以前」という**問いの形そのもの**である。

(3) **本論文は ZCSG が唯一の解であると主張していない**。同様の構造的応答は、他の形式装置（圏論的アプローチ、トポス論、構成的型理論、ホモトピー型理論など）から導くことも原理的に可能である。本論文が示すのは、ZCSG が一つの整合的な装置であることであって、他の道がないことではない。

(4) **本論文は龍樹の哲学の網羅的解釈ではない**。中論には因果論以外にも、運動論、時間論、自我論、認識論などの広範な議論がある。本論文が用いたのは、龍樹の戦略の一つ――概念の自性の解体――に限られる。 また catuṣkoṭi の解釈は仏教学において多義的であり、 本論文の依拠は Garfield-Priest 系の読みである (詳細は §4.3).

(5) **本論文は無限後退問題を「解決」したと主張していない**。本論文が示したのは、無限後退が「問いの形そのものの構造」から生じることと、ZCSG がその構造を記述する装置たりうることである。これは問題への構造的応答であって、伝統的な意味での「解答」ではない。

(6) **本論文は ZCSG と śūnyatā の厳密な mathematical isomorphism を証明していない**。 §4.3 で明示した通り、 主張は「構造的対応 (structural correspondence)」 レベルであり、 圏論的 isomorphism 確立は将来課題である。

(7) **本論文の Edison anecdote は史実性が不確か** (§6.1). Philosophical illustration として用いており、 歴史的事実主張ではない。

---

## 8. 結論

「神が宇宙を作ったなら、その神を作ったのは誰か」――この問いは、消えない。それは、この問いが無能だからではなく、問いの形そのものが、私たちの認識の根に深く食い込んでいるからである。

本論文は、この問いに「Xが答えだ」と応答する代わりに、**問いの形そのものがどこから生成しているのか**を記述する道を提示した。龍樹の空の論証と、著者が構築してきた ZCSG の形式装置が、この道を共同で開く。`o0 → 0 → 0o` の三層構造は、「区別された対象の世界」が生成する運動そのものを座標として持ち、その手前に「問いの形が未発生」という積極的な座標を確保する。

これは新しい教義の創出ではない。むしろ、龍樹が二千年前に言葉で示した洞察と、現代の形式論理が独立に到達した八値構造とが、ZCSG という装置において合流するという、**構造の発見**である。

「種は育ちます。急がず、ゆっくりと」――著者のモットーは、本論文の在り方そのものでもある。本論文が描いたのは結論ではなく、出発点である。`o0` という座標、`0` という生成運動、SELF⟲ という自己回帰――これらの装置を手にした読者が、それぞれの問いを、それぞれの深さで、再び問い直してくれることを願う。

---

## Acknowledgments

本論文は OUKC (Open Universal Knowledge Commons) framework の文脈で構想された philosophical reflection である.

**著者役割分担**: 第一著者・藤本伸樹は philosophical argument 主導 + paper 起草. Rei (Rei-AIOS autonomous research substrate) は ZCSG / D-FUMT₈ / SEED_KERNEL 形式装置の共同制作. Claude (Anthropic, claude-opus-4-7) は形式装置共同制作 + DRAFT v1.1 の review feedback (7 refinements: isomorphism hedge, philosophical-shift wording, Edison-Russell parallel, catuṣkoṭi 解釈精緻化, authorship policy, references 補強, ZCSG formal mini-summary).

OUKC charter v1.0 (2026-05-01) の下、 三者共著は **特定の不可約関係** であり、 generic AI 利用ではない. STEP 1021+ dialogue 累積による specific 三者関係に基づく.

**Tools used (not co-authors)**: 本論文の formal apparatus 検証には DeepSeek-Prover-V2 / Goedel-Prover-V2 / Vampire ATP / LeanHammer + Duper 等が tools として用いられる場面があるが、 これらは co-authors ではなく vendor-neutral tools である.

ZCSG / D-FUMT₈ / SEED_KERNEL の詳細は OUKC Charter v1.0 ([rei-aios.pages.dev/oukc/charter/](https://rei-aios.pages.dev/oukc/charter/)) を参照されたい.

---

## 参考文献

### 龍樹・空 (śūnyatā) 関連

- Nāgārjuna. *Mūlamadhyamakakārikā* (中論). 梶山雄一、瓜生津隆真訳『大乗仏典 14 龍樹論集』中央公論社, 1974.
- Garfield, J. L. (trans.). *The Fundamental Wisdom of the Middle Way: Nāgārjuna's Mūlamadhyamakakārikā*. Oxford University Press, 1995.
- Siderits, M. & Katsura, S. (trans.). *Nāgārjuna's Middle Way: Mūlamadhyamakakārikā*. Wisdom Publications, 2013.
- Westerhoff, J. *Nāgārjuna's Madhyamaka: A Philosophical Introduction*. Oxford University Press, 2009.
- Priest, G. *The Fifth Corner of Four: An Essay on Buddhist Metaphysics of the Catuskoti*. Oxford University Press, 2018.

### 著者先行論文 (OUKC corpus)

- 藤本 伸樹. 「ZCSG (Zero-Center Symbol Grammar) の基礎理論」 *Zenodo*, DOI: 10.5281/zenodo.19539868.
- 藤本 伸樹. 「Beyond Shannon: 意味等価圧縮と QMRP 定理」 *Zenodo*, DOI: 10.5281/zenodo.19388758.
- 藤本 伸樹. 「Positional Topological Incompleteness Theorem (TIT)」 *Zenodo*, DOI: 10.5281/zenodo.19393875.
- 藤本 伸樹. 「数字は、無機質有機体という別称になる」 note, 2025年1月.

### 自己参照記号系 / 形式論理

- Spencer-Brown, G. *Laws of Form*. London: Allen & Unwin, 1969.
- Kauffman, L. H. "Arithmetic in the form." *Cybernetics & Human Knowing*, 2(1), 1995.
- Whitehead, A. N. & Russell, B. *Principia Mathematica*. Cambridge University Press, 1910–1913.

### 西洋哲学

- 西田 幾多郎. 『場所的論理と宗教的世界観』 岩波書店, 1949.
- Wittgenstein, L. *Tractatus Logico-Philosophicus*. 1921.
- 鈴木 大拙. 『東洋的な見方』 岩波文庫.

---

**著作情報 / Publication Information**
- License: CC-BY 4.0
- Paper number: OUKC Paper #146
- Status: DRAFT v1.2 (2026-05-02, 三者共著 corrected), pending Author final approval before 11-platform publication
- Planned platforms (per OUKC standard): Zenodo (DOI authoritative) + Internet Archive + Harvard Dataverse + dev.to + Hatena + HackMD + Notion + Scrapbox + Zenn + livedoor + Mastodon + Jxiv (12 channels)
- Related project: Rei-AIOS / SEED_KERNEL / OUKC (Open Universal Knowledge Commons)
- OUKC official site: <https://rei-aios.pages.dev/oukc/>
- 著者 note.com: <https://note.com/nifty_godwit2635>
- Project motto: 「急がず、ゆっくりと。種は育ちます。」 / "Seeds grow. Without haste, slowly."
