---
day: 87
topic: 抗体AIのデータ設計――配列、構造、assay、ラベル、provenance
created: 2026-11-17
status: unread
---

# Day 087：抗体AIデータ設計の基本

## 今日の問い

抗体AIの性能を決めるのはモデル構造だけだろうか。配列、構造、assay、ラベルをどの単位で結び、どの由来・処理履歴まで残せば、予測値を生物学的に解釈し、新しい抗体や抗原へ一般化できるのか。

## 本文

### 1. 学習例は「配列1本」ではなく、問いに対応した記録である

抗体AIでは、まず予測単位を定義する。自然らしい可変領域を学ぶなら単鎖配列でもよいが、抗原結合を予測するなら少なくとも重鎖、軽鎖、抗原の組が必要である。同じ重鎖でも軽鎖が変わればパラトープの形と結合性は変わる。IgGの機能やdevelopabilityを扱うなら、アイソタイプ、Fc、糖鎖、発現宿主、製剤条件も関係する。「抗体ID」を一列だけ置くのでなく、`antibody_construct_id`、`heavy_chain_id`、`light_chain_id`、`antigen_id`、`assay_id`を分離し、関係を保つ。

大規模配列資源OASは、AIRR-seq由来の配列を洗浄・注釈し、非ペア配列と重鎖–軽鎖ペア配列を提供する[1]。大量配列は言語モデルの事前学習に有用だが、各配列が特定抗原へ結合するという教師ラベルではない。一方、SAbDabはPDB中の抗体構造を標準化し、鎖の対応、抗原、実験法、解像度などを注釈する[2]。構造は原子座標を与えるが、PDBに登録されやすい抗原・成功した複合体へ偏り、非結合例を自然には与えない。データ量と、答えたい問いへの適合性は別である。

### 2. 構造と配列には「対応関係」と品質情報が要る

構造入力では、どの配列残基がどの座標に対応するかを固定する。番号付け規則、欠損残基、alternate conformation、分解能、apo／抗原結合状態、実験構造／予測構造を記録する。座標のないCDRを配列から補完したなら、その処理も入力の一部である。予測構造を実験構造と同じ欄に入れると、モデルは誤差を真の構造差として学び得る。

重複排除も文字列一致だけでは足りない。同一抗体が別名、別PDB、別濃度の測定として複数行に現れることがある。逆に、同一配列でも抗原、assay条件、フォーマットが異なれば別の観測である。したがって「分子実体」と「観測」を別表にし、同一性を保ちながら測定反復を残す設計がよい。

### 3. ラベルは数値だけでなく、測定の文脈を含む

`KD = 10 nM`という数値だけでは不十分である。SPR、BLI、ITCなどの測定法、単価Fabか二価IgGか、抗原の構成、固定化方向、温度、pH、濃度範囲、解析モデル、反復数を伴って初めて意味が定まる。`KD`、EC50、IC50、binding／non-bindingを一つの「affinity」列へ無条件に混ぜてはならない。単位を標準化しても、測定量そのものの違いは消えない。検出限界による`KD < 1 nM`は点推定値でなく打ち切り値として保存する。

developabilityも同様で、HIC保持時間、AC-SINS、発現量、Tmは異なる目的変数である。Jainらは137抗体を同一形式で発現し、12種のassayを同じ枠組みで測定した[3]。このような整合した測定は、小規模でも複数文献から条件不明の値を集めた表より比較しやすい。ラベルには`label_name`、値、単位、方向、uncertainty、下限・上限、反復集約法、実測／計算予測の別を持たせる。2026年の統合データセットANDDも、複数資源を統合しつつ、実測affinityに加えて予測affinityを含む[4]。両者を区別しない学習は、別モデルの予測を実験的真実として再学習する循環を生む。

とくに注意すべきは陰性例である。データベースに結合記録がない抗体を`non-binder`と置くことはできない。未測定、測定したが非公開、検出限界以下、発現不良で測定不能は別状態である。panning後に残らなかった配列も、非結合とは限らず、初期頻度、発現、増殖、洗浄条件の影響を受ける。明示的な陰性対照と、同じassayで測った陽性・陰性を優先し、`not tested`、`not detected`、`failed QC`を区別する。さらに同じ候補を技術反復した行と、独立に得た生物学的反復を区別しなければ、見かけのsample数と確信度を過大評価する。

### 4. provenanceは「その行がここに来るまでの履歴」である

**provenance**には、原著・データベース名とversion、取得日、試料・assay、原データID、抽出規則、単位変換、フィルタ、番号付け、重複統合、構造予測モデルとversionを含める。AIRR CommunityのMiAIRRは、study、subject、sample、実験処理、データ処理、注釈にまたがる最小metadataを提案している[5]。全項目をそのまま使う必要はないが、「元データ」「変換」「現在値」を追跡できる考え方が重要である。処理済みCSVだけでなく、再現可能なスクリプト、schema version、データsnapshotを固定する。

### 5. splitは将来の使用場面を模擬する実験設計である

無作為な行分割では、同一clonotypeの近縁変異、同一抗原、同一PDB由来の重複がtrainとtestに跨がり、記憶を一般化と誤認する。未知変異を予測したいなら系列単位、未知抗原なら抗原または抗原family単位、将来データへの性能なら公開日によるtemporal splitを使う。Bittonらは抗体developability予測で、配列familyを同じsplitへまとめ、split間のFab配列同一性が95%を超えないようにした[6]。ただし95%は万能な正解ではない。分割単位、類似度定義、閾値を明記し、目的に合う厳しさを選ぶ。

分割は重複排除と同じ処理ではない。完全重複を除いた後にも近縁系列は残るため、全データでclusterを作ってからcluster単位で割り当てる。testを見て閾値や前処理を選べば、それ自体が評価情報の漏洩になるので、選択はvalidationまでで完結させる。

最後に、データカードへ対象集団、包含・除外基準、欠測、陽性／陰性の作り方、抗原・clonotype別件数、assay別分布、既知の偏り、許可条件を記す。よいデータ設計とは、巨大な表を作ることではなく、モデルの成功と失敗をどの生物学的条件まで遡って説明できる状態を作ることである。

## 図または比較表

```text
分子実体（H鎖・L鎖・抗原・format）
              ↓ IDで結合
観測（assay・条件・反復） → ラベル（値・単位・打ち切り・不確実性）
              ↓
provenance（原典 → 抽出 → 変換 → version）
              ↓
目的に対応したgroup split → 学習・評価 → 新規実験
```

| データ層 | 最低限残す項目 | 失うと起きる問題 |
|---|---|---|
| 配列 | H/Lペア、抗体format、番号付け | 誤った鎖対応、CDR位置の不一致 |
| 構造 | 抗原鎖、apo/holo、実験法、品質、欠損 | 座標誤差を生物学的差と誤認 |
| assay | 方法、構成、条件、反復、解析モデル | 異質な測定値を同じラベルとして混合 |
| ラベル | 定義、単位、範囲、uncertainty、実測/予測 | EC50とKD、点推定と打ち切りを混同 |
| provenance | 原典ID、version、取得日、全変換 | 誤りの追跡・再構築ができない |
| split | grouping単位、類似度、閾値、cutoff日 | 近縁配列や抗原のリーク |

## 論文を読むためのポイント

1. **学習例の単位**：単鎖、H–Lペア、抗体–抗原pair、assay観測のどれか。分母は抗体数か測定行数か。
2. **ラベルの定義**：`KD`、EC50、binary binding、発現量などが混在せず、単位・条件・欠測・打ち切りが説明されているか。
3. **入力の由来**：実験構造と予測構造、実測値と擬似ラベルを区別しているか。
4. **分割の意味**：clonotype、抗原、project、時間のどれを跨がせず、どの未知性を評価しているか。
5. **追跡可能性**：source ID、snapshot、処理codeがあり、表の一行を原著とraw dataまで戻せるか。

## 抗体×AIとの接続

データschemaはモデルの入力・出力を先に決める設計図である。配列言語モデルの事前学習、構造モデルのfine-tuning、assay別予測を一つの表へ押し込まず、共有する分子IDで接続すれば、多目的学習でも欠測を明示できる。active learningでは、予測値だけでなく不確実性、assay費用、既測定条件、系列の多様性を使って次の実験を選ぶ。新しい測定は同じschemaとprovenanceで戻し、モデルversionとデータsnapshotを固定して初めて、改善が新規データによるものか手法によるものか比較できる。

## 重要用語（8語）

- **schema**：項目、型、関係、許容値を定めたデータの設計図。
- **assay metadata**：測定法、試料構成、条件、装置、解析法を説明する情報。
- **label provenance**：教師ラベルの原典と生成・変換履歴。
- **censoring（打ち切り）**：測定限界により真値を範囲としてしか観測できない状態。
- **paired sequence**：天然または実験的に対応づけられた重鎖・軽鎖配列。
- **clonotype**：共通祖先に由来するとみなす近縁抗体配列群。
- **group split**：関連する試料群を分割間で混ぜずに割り当てる方法。
- **data leakage**：本来未知であるべきtest情報が学習や前処理へ入り込むこと。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

異なる論文の`KD = 5 nM`と`IC50 = 5 nM`を、同じ5 nMのaffinityラベルとして学習してよいか。

**模範回答：** 原則として同一視しない。`KD`は結合平衡、IC50は特定条件での阻害濃度であり、分子format、assay、温度、抗原構成などを別に記録し、必要なら別taskとして扱う。

### 問2

同一clonotypeの1残基変異体を行単位で無作為にtrain/test分割すると、なぜ高性能に見えやすいか。

**模範回答：** test配列とほぼ同じ配列・系列背景がtrainに入り、モデルが未知系列への規則でなく近縁例を記憶できるからである。clonotypeや配列clusterを同じsplitにまとめる。

## さらに調べる疑問2〜3問

1. 未知抗原への結合予測では、抗原を配列family、構造fold、epitopeのどれでgroup化すべきか。
2. 複数施設のSPRデータを統合するとき、共通参照抗体でbatch effectをどこまで補正できるか。
3. 打ち切り値と欠測が多いdevelopabilityデータには、どの損失関数と評価指標が適切か。

## 自分の3行要約

- 抗体AIの学習例は、H鎖・L鎖・抗原・formatとassay観測をIDで結んだ記録として設計する。
- ラベルは数値だけでなく、定義、条件、単位、不確実性、実測／予測の別、provenanceを含む。
- splitはclonotype・抗原・時間など将来の利用場面に合わせ、近縁例のリークを防ぐ実験設計である。

## 未解決の疑問

配列、構造、複数assayの欠測率が大きく異なる現実の抗体データで、測定されやすさ自体の偏りを補正しながら、多目的モデルの外部一般化をどう評価すべきだろうか。

## 参考文献

1. Olsen TH, Boyles F, Deane CM. Observed Antibody Space: A diverse database of cleaned, annotated, and translated unpaired and paired antibody sequences. *Protein Sci.* 2022;31:141–146. [DOI: 10.1002/pro.4205](https://doi.org/10.1002/pro.4205)
2. Dunbar J, et al. SAbDab: the structural antibody database. *Nucleic Acids Res.* 2014;42:D1140–D1146. [DOI: 10.1093/nar/gkt1043](https://doi.org/10.1093/nar/gkt1043)
3. Jain T, et al. Biophysical properties of the clinical-stage antibody landscape. *Proc Natl Acad Sci USA.* 2017;114:944–949. [DOI: 10.1073/pnas.1616408114](https://doi.org/10.1073/pnas.1616408114)
4. Liu N, et al. A Unified Dataset for Antibody and Nanobody Design Including Sequence, Structure, and Binding Affinity Data. *Sci Data.* 2026. [DOI: 10.1038/s41597-026-06878-0](https://doi.org/10.1038/s41597-026-06878-0)
5. Rubelt F, et al. Adaptive Immune Receptor Repertoire Community recommendations for sharing immune-repertoire sequencing data. *Nat Immunol.* 2017;18:1274–1278. [DOI: 10.1038/ni.3873](https://doi.org/10.1038/ni.3873)
6. Bitton DA, Fayadat-Dilman L. A machine learning strategy for the identification of key in silico descriptors and prediction models for IgG monoclonal antibody developability properties. *mAbs.* 2023;15:2248671. [DOI: 10.1080/19420862.2023.2248671](https://doi.org/10.1080/19420862.2023.2248671)
