# VPSY — Virtual Psychology

一般に感情と呼ばれる現象を時刻Tで分解し、記憶・環境・性格などの多要素と接続した、感情のシミュレーション装置の構想と研究計画です。

立場は、感情の再現ではなく **模倣** です。
目的は、誰かを理解することではなく、誰かを理解する一助、人が判断する材料の一欠片となることです。

---

## このリポジトリについて

VPSYの文書を、段階ごとの版として置いています。

| 版 | 段階 | 時期 | 内容 |
| --- | --- | --- | --- |
| v1 | 構想 | 2025年10月 | 設計思想、OSI参照モデルに対応づけた7層、記憶・通信モデル、データ型、テーブル設計案 |
| v2 | 研究計画 | 2026年10月 | 研究の問い、仮説H01〜H28、先行研究との照合、要件定義の判断点、次の作業の手順 |

v1は構想を人に見せる形にまとめた段階、v2はその構想を**先行研究と照合でき、妥当性を測れる形**にした段階です。v2はv1を置き換えるものではなく、v1の構想が照合を経てどう変わったかが分かるように、両方を残しています。

実装コードは含まれていません。

---

## 読むときの前提

次の三点を知らずに読むと、主張を取り違えやすいことが分かっています。

1. **VPSYの語はモジュール名である。** 感情、気分、気持ち、観念、傾向性などは、システムのモジュールにあてがった名前で、一般の意味や心理学の専門用語とは一致させていません。先行研究とは、語の文字列ではなく機能で照合しています。たとえば、心理学で感情（emotion）と呼ばれ数分以上続くものは、機能としてVPSYの「気持ち」に当たります。VPSYの「感情」は、その下にある数秒単位の層です。
2. **技術は構造だけを借りている。** TCP/IP、TTL、サブネット、ハフマン符号化などは、論理の構成や分け方を借りてVPSY向けに広げたもので、技術そのものの性質（例：ハフマン符号化は可逆）を主張に持ち込んではいません。
3. **強い言い切りは、考え抜いた限界点の表明である。** 「常に」「実在できない」などの表現は、例外を暗黙に前提したうえで、ここではこう捉える、という意味で使っています。

---

## 研究の問い（v2）

**主な問い**：一般に感情と呼ばれる現象を時刻Tで分解し多要素と接続したモデルは、心理学研究の結果と過程をどこまで模倣できるか

**副次的な問い**

- そのモデルにおいて、性格は有限のパターンに収束するか
- 睡眠のように先行研究で決着していない処理を、先行研究の結果と軋轢を生まない範囲で、どこまでセンチネル値のような簡略的な処理で扱えるか

**判定**は、結果と過程の2軸で4通りに分けます。

| 結果 | 過程 | 意味 |
| --- | --- | --- |
| 同じ | 似ている | 装置が妥当に動いている証拠 |
| 違う | 似ている | 研究結果の誤りや、一般化の限界の可能性を示唆する |
| 同じ | 違う | 偶然の一致。妥当とは言えない |
| 違う | 違う | 装置の側の見直しが必要 |

---

## 文書

### v2：研究計画（`docs/v2/`）

| # | 文書 | 内容 |
| --- | --- | --- |
| 0 | [研究計画の概要](docs/v2/01_research-plan-overview.md) | 全体像を2〜3枚にまとめた入口。まずこれを読む |
| 1 | [概念整理（仮説と構成図）](docs/v2/02_concepts-hypotheses-and-diagram.md) | 研究の問い、一番上の要求、照合の前提、モジュールの機能、仮説H01〜H28と決めたこと、構成図 |
| 2 | [先行研究 総合調査結果](docs/v2/03_prior-research-survey.md) | 仮説ごとの照合結果、独自性の評価、照合の方法と目標値、訂正の一覧、残っている課題、参考文献 |
| 3 | [次の作業の手順](docs/v2/04_next-steps.md) | 判断点D1〜D9の結果、基本設計で決めること、文献の読解の手順 |

### v1：構想（`docs/v1/`）

| # | 文書 | 内容 |
| --- | --- | --- |
| 1 | [概念全体の地図](docs/v1/01_overview.md) | VPSYの目的・位置づけ・全体構造 |
| 2 | [設計思想と哲学的立場](docs/v1/02_design-principles.md) | 模倣・観察という立場の定義と根拠 |
| 3 | [感情処理7層モデル](docs/v1/03_layer-model.md) | OSI参照モデル対応の階層アーキテクチャ |
| 4 | [記憶モデル](docs/v1/04_memory-model.md) | ハフマン符号化＋エビングハウス応用 |
| 5 | [通信・伝達モデル](docs/v1/05_communication-model.md) | TCP/IPアナロジーによる感情伝達設計 |
| 6 | [データ型定義](docs/v1/06_data-types.md) | 環境・関係性・状態データタイプ |
| 7 | [DBテーブル設計案](docs/v1/07_table-design.md) | 主要14テーブルの設計案 |
| 8 | [未考察・拡張テーマ](docs/v1/08_future-topics.md) | 考察中・未解決の拡張テーマ群 |

v1の文書では、名称の英語展開を "Virtual Simulation System for Psychodynamics" としていました。現在は Virtual Psychology を用いています。

---

## v1からv2への主な変化

| 項目 | v1 | v2 |
| --- | --- | --- |
| 語の扱い | 一般語と地続きに読めた | モジュール名として定義し、先行研究とは機能で照合する |
| 感情・気分・気持ち | 7層の上位3層 | 心理学の感情エピソードを最上層の気持ちに当て、その下に数秒の感情を置く3層の対応付け |
| 理解力の位置 | 観念と傾向性の間の層 | 傾向性の優先度・重み付けのためのパイプライン |
| 性格 | 傾向性が決定づけるもの | 一定の観測期間における傾向性の出力パターンの言語化。傾向性は器官、性格は働きの名称 |
| 環境の正常値 | 「〜経験が無いもの」をデフォルトとして記述 | 社会的問題やマイノリティの属性の側が値を持ち、経験が無いデフォルトは平常値を持たない、という向きで統一 |
| 意識的な思考 | 未定義 | 内部で自律生成せず、外部情報のデータタイプとして入力する（D3） |
| 睡眠 | 無知覚状態 | 裏の処理として別モジュールに分け、センチネル値のような特殊な値で表す（D6） |
| 妥当性の測り方 | 未定義 | 結果と過程の2軸・4通りの判定。各層の途中の値を心理学研究の過程と照合する |

---

## 先行研究との関係（v2）

28の仮説を、10回の調査で先行研究と機能で照合しました。機能で照合すると、VPSYの主張と対立する先行研究は残りませんでした。

**既知の部分**：短い層の出力が長い層を動かす直列の構成（ALMA、WASABI、Soarに基づくモデル）、性格を状態の分布とする見方（Fleeson、CAPS）、感情の文脈とともに符号化し想起で書き換わる記憶（CMR3）、逆境の累積の測り方（ACE）など。

**VPSYに固有と言える部分**

- 心理学の感情（emotion）を最上層の気持ちに当て、その下に数秒の感情を置く3層の対応付け
- 範囲（サブネット）としての一致とTTLによる段階的な遷移
- 記憶と環境を別のバイアス源として分けること、sentimentが環境から傾向性・観念へ形成される順序
- 正常値を反転させた計測の向きを、感情のシミュレーションの基礎にすること
- 各層の途中の値の照合を、一番上の要求の段階から組み込んだこと

一つ一つの主張の多くは既知です。固有なのは、時間の対応付け、遷移の規則、記憶と環境の分け方、そして照合を最初から要求に入れた組み立て方です。詳細は[総合調査結果](docs/v2/03_prior-research-survey.md)の5章にあります。

---

## 現在のステータス

```
構想（v1）        : ██████████  完了
先行研究との照合  : ██████████  完了（第1回〜第10回、2026/10）
要件定義          : ██████████  判断点D1〜D9を決定
基本設計          : ░░░░░░░░░░  未着手
実装              : ░░░░░░░░░░  未着手
照合              : ░░░░░░░░░░  未着手
```

次の段階は、広範要求仕様と分解後要求仕様、その後に基本設計（傾向性の個人差の持ち方、TTLの長さと閾値など）と実装です。開発範囲は最初から、個人としての感情シミュレーションに必要な全てとします。各層が互いの入力になる循環があり、一部だけ作ると照合の意味を失うためです。

---

## 作成の分担

- VPSYの構想、各仮説の主張、研究の問い、判断点の結論は、著者が考え、決めたものです。
- v2の文書の作成、先行研究の調査、文献の確認、仮説と先行研究の照合は、その大部分をAI（Claude）が行い、著者が読んで修正・確認しました。
- 参考文献には、どこまで確かめたか（本文、抜粋、要旨、二次文献、書誌のみ）を記号で付けています。

---

## 構想の背景

この構想は、学校にはほとんど通えず、複雑な家庭環境のなかで感情を押し殺して生活していた時期に考え始めたものです。感情が理解できなくなるという感覚の中で、「もし感情をシミュレートできる仕組みがあれば、自分のような苦しさを抱える人の一助になるのではないか」という問いが出発点になりました。

14〜15歳頃に構想を始め、通信制大学で哲学を独学していた19〜22歳頃に骨組みのほとんどを作り、エンジニアになってから技術的な部分を足してきました。2025年10月に構想として文書化し（v1）、2026年10月に先行研究と照合して研究計画の形にしました（v2）。

---

## ライセンス

[CC BY-SA 4.0](LICENSE)

引用・改変・再配布の際は原著者の表示と同一ライセンスの適用をお願いします。

---

## 免責事項

本リポジトリに含まれる記述は構想と研究計画であり、医学的・臨床的な診断・治療・助言を目的とするものではありません。環境・状態などのデータタイプの記述は、シミュレーションの対象を定義するためのものであり、当事者への直接的な関与や診断を意図しません。

---
---

# VPSY — Virtual Psychology (English)

A concept and research plan for an emotion simulation apparatus: the phenomenon generally called "emotion" is decomposed along time T and connected to multiple elements such as memory, environment and personality.

The stance is **imitation**, not reproduction, of emotion.
The purpose is not to understand someone, but to be an aid to understanding someone — one fragment of the material a person uses to judge.

---

## About This Repository

The VPSY documents are kept as versions, one per stage.

| Version | Stage | Date | Contents |
| --- | --- | --- | --- |
| v1 | Concept | October 2025 | Design philosophy, 7 layers mapped to the OSI reference model, memory and communication models, data types, draft table design |
| v2 | Research plan | October 2026 | Research question, hypotheses H01–H28, comparison with prior research, requirements decisions, next steps |

v1 is the stage where the concept was written up to be shown to others; v2 is the stage where that concept was put into a form that **can be compared with prior research and whose validity can be measured**. v2 does not replace v1. Both are kept so that it is visible how the concept changed through the comparison.

No implementation code is included.

---

## Premises for Reading

Reading without the following three points is known to lead to misreadings of the claims.

1. **VPSY's terms are module names.** Emotion (感情), mood (気分), feeling (気持ち), idea (観念), tendency (傾向性) and the rest are names assigned to system modules; they are not made to coincide with everyday meanings or with psychological terminology. Prior research is compared by function, not by the string of the word. For example, what psychology calls an emotion and finds to last minutes or longer corresponds, by function, to VPSY's "feeling." VPSY's "emotion" is the layer beneath it, on the order of seconds.
2. **Only the structure of the technologies is borrowed.** TCP/IP, TTL, subnets, Huffman coding and the like are borrowed for their logical organisation and partitioning and extended for VPSY. The properties of the technologies themselves (for example, Huffman coding being lossless) are not carried into the claims.
3. **Strong assertions express a considered limit.** Expressions such as "always" or "cannot exist" are used in the sense "this is how it is taken here," with exceptions implicitly presupposed.

---

## Research Question (v2)

**Main question**: To what extent can a model that decomposes the phenomenon generally called emotion along time T, and connects it to multiple elements, imitate the results and the processes of psychological research?

**Secondary questions**

- In such a model, does personality converge to a finite set of patterns?
- For processes on which prior research has not settled, such as sleep, how far can they be handled with simplified treatment such as sentinel values, within the range that does not conflict with prior results?

**Judgement** is made on two axes, result and process, giving four cases.

| Result | Process | Meaning |
| --- | --- | --- |
| Same | Similar | Evidence that the apparatus works validly |
| Different | Similar | Suggests a possible error in the research result, or a limit of its generalisation |
| Same | Different | Coincidence; not valid |
| Different | Different | The apparatus needs revision |

---

## Documents

### v2: Research plan (`docs/v2/`)

| # | Document | Contents |
| --- | --- | --- |
| 0 | [Overview of the research plan](docs/v2/01_research-plan-overview.md) | The whole in two or three pages. Start here |
| 1 | [Concept organisation (hypotheses and structure diagram)](docs/v2/02_concepts-hypotheses-and-diagram.md) | Research question, top-level requirement, premises for comparison, module functions, hypotheses H01–H28 and decisions, structure diagram |
| 2 | [Prior research: consolidated survey results](docs/v2/03_prior-research-survey.md) | Comparison results per hypothesis, assessment of originality, comparison method and target values, list of corrections, remaining issues, references |
| 3 | [Next steps](docs/v2/04_next-steps.md) | Decisions D1–D9, what is to be decided in basic design, procedure for reading the literature |

The v2 documents are in Japanese.

### v1: Concept (`docs/v1/`)

| # | Document | Contents |
| --- | --- | --- |
| 1 | [Conceptual Overview](docs/v1/01_overview.md) | Purpose, positioning, and overall structure of VPSY |
| 2 | [Design Principles](docs/v1/02_design-principles.md) | Definition and rationale of the imitation-and-observation stance |
| 3 | [7-Layer Emotion Processing Model](docs/v1/03_layer-model.md) | Hierarchical architecture mapped to the OSI reference model |
| 4 | [Memory Model](docs/v1/04_memory-model.md) | Huffman coding + Ebbinghaus forgetting curve application |
| 5 | [Communication Model](docs/v1/05_communication-model.md) | Emotional transmission design via TCP/IP analogy |
| 6 | [Data Type Definitions](docs/v1/06_data-types.md) | Environment, relationship, and state data types |
| 7 | [DB Table Design](docs/v1/07_table-design.md) | Draft design of 14 core tables |
| 8 | [Future Topics](docs/v1/08_future-topics.md) | Unresolved and extended themes under consideration |

The v1 documents expanded the name as "Virtual Simulation System for Psychodynamics." The name now used is Virtual Psychology.

---

## Main Changes from v1 to v2

| Item | v1 | v2 |
| --- | --- | --- |
| Treatment of terms | Could be read as continuous with everyday words | Defined as module names; compared with prior research by function |
| Emotion / mood / feeling | The upper three of seven layers | A three-layer mapping that places the psychological emotional episode at the top layer (feeling) and a seconds-scale emotion beneath it |
| Position of understanding (理解力) | A layer between idea and tendency | A pipeline for the priority and weighting of tendency |
| Personality (性格) | Something that tendency determines | The verbalisation of tendency's output pattern over a given observation period. Tendency is the organ; personality is the name of its working |
| Normal value of environment | Described with "no ~experience" as the default | Unified in the direction that the side with social-problem or minority attributes holds values, and the default with no such experience holds no normal value |
| Conscious thought | Undefined | Not generated autonomously inside; input as a data type of external information (D3) |
| Sleep | A state without perception | Separated into a background module, represented by a special value akin to a sentinel (D6) |
| How validity is measured | Undefined | Two axes, four cases. Intermediate values of each layer are compared with the processes shown by psychological research |

---

## Relation to Prior Research (v2)

Twenty-eight hypotheses were compared with prior research by function, over ten rounds of survey. When compared by function, no prior research remained in conflict with VPSY's claims.

**Already known**: serial structures in which the output of a shorter layer drives a longer one (ALMA, WASABI, Soar-based models); personality as a distribution of states (Fleeson, CAPS); memory encoded with emotional context and rewritten on recall (CMR3); the measurement of cumulative adversity (ACE), and others.

**Parts that can be called specific to VPSY**

- The three-layer mapping that places the psychological emotion at the top layer (feeling) and a seconds-scale emotion beneath it
- Matching as a range (subnet), and stepwise transition by TTL
- Separating memory and environment as distinct sources of bias, and the order in which sentiment forms from environment into tendency and idea
- Making the inverted direction of measurement of the normal value the basis of emotion simulation
- Building the comparison of each layer's intermediate values into the top-level requirement from the outset

Most of the individual claims are known. What is specific is the time mapping, the transition rule, the separation of memory and environment, and the assembly that places comparison in the requirement from the start. Details are in chapter 5 of the [consolidated survey results](docs/v2/03_prior-research-survey.md).

---

## Current Status

```
Concept (v1)                 : ██████████  Done
Comparison with prior research: ██████████  Done (rounds 1–10, Oct 2026)
Requirements                 : ██████████  Decisions D1–D9 made
Basic design                 : ░░░░░░░░░░  Not started
Implementation               : ░░░░░░░░░░  Not started
Comparison                   : ░░░░░░░░░░  Not started
```

The next stage is the broad requirement specification and the decomposed requirement specification, followed by basic design (how individual differences in tendency are held, TTL lengths and thresholds, and so on) and implementation. The development scope is, from the start, everything needed for the emotion simulation of one individual: the layers feed one another in a loop, and building only a part would make the comparison meaningless.

---

## Division of Work

- The VPSY concept, the claims of each hypothesis, the research question and the conclusions of the decision points were conceived and decided by the author.
- For the v2 documents, most of the writing, the survey of prior research, the checking of the literature and the comparison of hypotheses with prior research were done by AI (Claude); the author read, corrected and confirmed them.
- The references carry markers for the level to which each was checked (full text, excerpt, abstract, secondary source, bibliographic record only).

---

## Background

This concept began during a period when I could barely attend school and was suppressing my emotions just to get through each day in a complex home environment. In the midst of losing the ability to understand my own emotions, I asked: if there were a system that could simulate emotion, could it help people carrying the same kind of weight I was? That question became the starting point.

I began the concept at around 14 or 15, built most of its skeleton at 19 to 22 while studying philosophy on my own at a correspondence university, and added the technical parts after becoming an engineer. In October 2025 it was written up as a concept (v1); in October 2026 it was compared with prior research and shaped into a research plan (v2).

---

## License

[CC BY-SA 4.0](LICENSE)

When citing, adapting, or redistributing, please credit the original author and apply the same license.

---

## Disclaimer

The contents of this repository are a concept and a research plan. They are not intended as medical, clinical, diagnostic, treatment, or advisory content. The descriptions of data types such as environment and state define the targets of simulation; they are not intended as direct engagement with or diagnosis of any individual.
