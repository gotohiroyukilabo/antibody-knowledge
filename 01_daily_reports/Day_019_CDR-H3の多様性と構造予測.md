---
day: 19
topic: CDR-H3――最も多様で予測が難しいループ
created: 2026-09-08
status: unread
---

# Day 019：CDR-H3の多様性と構造予測

## 今日の問い

6本のCDRのうち、なぜ重鎖の3番目にあるCDR-H3は配列・長さ・立体構造が特に多様なのか。その多様性は抗原認識に何をもたらし、構造予測や抗体×AIをなぜ難しくするのか。

## 本文

### 1. CDR-H3は抗原結合面の中央にある可変ループ

抗体のFvでは、重鎖可変ドメイン（VH）と軽鎖可変ドメイン（VL）から3本ずつ、計6本のCDRが集まってパラトープをつくる。CDR-H3はVHのF鎖とG鎖を結び、VH–VL界面に近い結合面中央へ突き出すことが多い。H1/H2の大部分がV遺伝子断片にコードされるのに対し、H3はV、D、J断片の接合部をまたいで生じる。この由来が多様性の出発点である。[Chiu et al., 2019](https://doi.org/10.3390/antib8040055) なおIMGTではCDR3-IMGTを105–117番、その外側のCys 104とTrp 118をアンカーとするが、KabatやChothiaでは境界と長さの数え方が違う。「H3長14残基」を論文間で比較するときは番号付け方式を確認する。[IMGT](https://www.imgt.org/IMGTScientificChart/Numbering/CDR3-IMGTposition.html)

### 2. V(D)J接合が配列と長さを同時に多様化する

発生中のB細胞では、重鎖遺伝子のV、D、J断片が一つずつ選ばれる。連結時にはDNA末端が削られ、鋳型にないNヌクレオチドやヘアピン開裂由来のPヌクレオチドが加わり得る。したがってH3は断片の組合せだけでなく、接合位置、Dの読み枠、削除・挿入によって配列と長さが変わり、抗原刺激後には体細胞超変異も加わる。一方、軽鎖L3はV–J接合でDを含まないため、H3の方が一般に生成上の自由度が大きい。「H3はV遺伝子内の高可変区間ではなく、再構成の継ぎ目そのもの」と理解しよう。ゆえにgermline割当でも接合中央部の由来は曖昧になりやすい。

### 3. 長さは結合面の地形を変えるが、機能を単独では決めない

短いH3では6本のCDRがつくる面がくぼみや溝になりやすく、複数ループが抗原へ接触できる。長いH3は突出して奥まったエピトープへ届き、障害物を越えられる場合がある。171個の非冗長な抗体–抗原複合体の解析では、H3の長さが結合面全体の形と他CDRの参加の仕方にも関係した。[Tsuchiya and Mizuguchi, 2016](https://doi.org/10.1002/pro.2874) ただし「長いほど高親和性」「H3が常に最大寄与」という法則ではない。結合はH3の側鎖と向き、他CDR、VH–VL配向、抗原の形・柔軟性の組合せで決まる。突出部は新しい部位へ届く反面、疎水面の露出、自己会合、非特異的結合、立体衝突のリスクも持つ。長さは特徴量であって、affinityやdevelopabilityの答えではない。

### 4. 「根元」と「先端」を分けると構造多様性が見える

H3はframeworkにつながるstem/base（根元）と、抗原側のtip/head（先端）に分けると理解しやすい。多くの抗体の根元には、βストランドの規則的対合を途中で崩すkinked型が見られ、少数はextended型をとる。kinkは先端が取り得る方向を広げ、構造多様性に寄与すると考えられる。[Weitzner et al., 2015](https://doi.org/10.1016/j.str.2014.11.010) 根元に傾向があっても、先端はループ長、H3内相互作用、隣接CDRやVLとのパッキングで大きく変わり、同じ長さでもstraight、bent、broadなどになり得る。同一H3配列でもVH/VL環境が違えば配座が変わり得るので、「配列→構造」はH3だけの局所問題ではなくFv全体の問題である。

ここで「多様な構造」と「常に柔らかく動くこと」を区別したい。PDBに登録された多数の異なるH3が多様な形を示すことは、ある一つのH3が溶液中で無秩序に揺らぐことを直接意味しない。実際、H3は一般のタンパク質ループより特別に高い柔軟性を示すとは限らないとの比較解析がある。[Regep et al., 2017](https://doi.org/10.1002/prot.25291) 結合前後の構造差を論じるには、同じ抗体の非結合型と結合型を比較し、結晶中の欠損残基やB-factor、測定分解能も確認する。一本の結晶構造は配座集団の一断面であり、「静的に見える」と「溶液中で一つの形しかない」も同義ではない。

### 5. H3予測が他のCDRより難しい理由

非H3の5本は、長さと鍵残基から限られたcanonical structureを選べる場合が多い。H3は長さ・配列の範囲が広く、同じ長さにも多様な主鎖配座があり、近いテンプレートがないことがある。構造比較では、H3の30%以上が非冗長な一般タンパク質断片集合に近縁構造を持たず、他ループより独特な局所配座が多いと報告された。[Regep et al., 2017](https://doi.org/10.1002/prot.25291) 従来法はframeworkと非H3 CDRを組み、H3候補をテンプレート検索またはde novo生成して順位づけする。深層学習でも、主鎖、側鎖、VH–VL環境、場合によっては抗原を同時に整合させる必要がある。confidenceが高くてもH3の実験構造や結合界面の正しさを保証しないため、領域別RMSDを見る。

### 6. H3配列・構造・機能を一対一対応させない

H3は抗原認識で重要だが、単独で働く部品ではない。界面解析では、どの残基が抗原へ接触するか、他CDRと水素結合・パッキングするか、構造が抗原結合型か非結合型かを見る。同一配列の複数構造が異なるなら、配座集団、結晶条件、抗原結合、VH/VL環境の違いを検討する。工学でH3を変えると特異性を大きく動かせる一方、発現、安定性、非特異的結合も変わり得る。変異体はaffinityだけでなく`kon`・`koff`、熱安定性、単分散性、polyreactivityを同じformatとassayで比較する。H3は強力な設計レバーだが、Fv全体と抗原から切り離して最適化してはいけない。

## 図または比較表

```text
重鎖遺伝子の再構成                 抗体Fvの立体構造
 V末端 ─┬─ D ─┬─ J先頭              H1   H3   L1
        │     │                       \  ↑  /
    削除・P/N付加                    H2─抗原─L2
        └──┬──┘                        \   /
        CDR-H3                     VH ─── VL
   配列と長さが多様              根元(base)→先端(tip)
```

| 観点 | 非H3 CDR（H1/H2/L1/L2/L3） | CDR-H3 |
|---|---|---|
| 遺伝的由来 | 主にV、またはV–J接合 | V–D–Jの二つの接合部をまたぐ |
| 長さ・配列 | 比較的制約が強い | とくに多様 |
| 主鎖構造 | canonical classに入ることが多い | 根元に傾向はあるが先端は多様 |
| 抗原結合での位置 | 結合面の周辺〜中央 | 中央から突出しやすい |
| 予測 | テンプレート選択が比較的有効 | テンプレート不足と探索空間が難所 |

## 論文を読むためのポイント

1. CDR-H3の境界、残基番号、長さがどの番号付け方式で定義されたかを確認する。
2. 「H3が重要」という主張を、接触数、埋没表面積、変異効果、結合自由エネルギーのどれで示したか分ける。
3. 構造がX線結晶構造、cryo-EM、予測モデルのどれか、抗原結合型か非結合型かを見る。
4. 予測精度では全Fvの平均値だけでなく、H3主鎖RMSD、長さ別成績、側鎖・界面精度を確認する。
5. 比較する配列で重鎖だけでなく軽鎖と抗原が対応しているかを確認する。

## 抗体×AIとの接続

CDR-H3は、配列生成、構造予測、結合予測で頻繁に出力対象となる。しかしH3配列だけを入力してaffinityを学習すると、抗原、軽鎖、他CDR、assay条件という因果上重要な情報が欠ける。少なくともpaired VH/VL、抗原IDまたは構造、測定法、単位を保持し、H3長を独立した特徴量として扱う必要がある。

データ分割にも注意する。同じclonotypeの近縁H3、同一抗原、同一親抗体の変異系列をtrain/testへ無作為に分けると、モデルは一般則ではなく系列固有の配列を記憶できる。構造予測では、公開時点より後のPDB構造をtestに使う時間分割や、H3配列・frameworkの類似性を制御した分割が望ましい。評価も配列回収率だけでなく、H3 RMSD、物理的妥当性、抗原界面、実験的な結合・developabilityで行う。

## 重要用語5〜8語

- **CDR-H3**：重鎖可変ドメインの3番目のCDR。V–D–J接合部から生じ、抗原結合面の中央に位置しやすい。
- **V(D)J再構成**：V、D、J遺伝子断片を選択・連結して重鎖可変領域をつくる過程。
- **junctional diversity**：接合部での塩基削除やP/Nヌクレオチド付加が生む多様性。
- **canonical structure**：長さと特定残基に対応して反復するCDR主鎖構造の型。
- **kinked conformation**：CDR-H3根元のβストランド対合が折れ曲がった代表的配座。
- **de novo loop modeling**：既知ループを単純転写せず、配座を生成・探索して構造を予測する方法。
- **RMSD**：対応原子の位置ずれを表す指標。原子選択と重ね合わせ方法を併記して解釈する。
- **clonotype**：共通の免疫学的起源をもつ近縁抗体群をまとめる概念。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

CDR-H3が非H3 CDRより配列と長さの多様性を得やすい遺伝的理由は何か。

**模範回答：** CDR-H3はV、D、Jの二つの接合部をまたぎ、断片選択に加えてDNA末端の削除、P/Nヌクレオチド付加、Dの読み枠の違いを受けるためである。抗原刺激後には体細胞超変異も加わる。

### 問2

二つの抗体が同じ長さのCDR-H3を持つだけでは、同じ立体構造や結合性を期待できないのはなぜか。

**模範回答：** 同じ長さでもアミノ酸配列と内部相互作用が異なり、隣接CDR、framework、軽鎖、抗原との構造環境も配座を変える。長さは重要だが、構造やaffinityを単独で決める変数ではない。

## さらに調べる疑問2〜3問

1. ヒト、マウス、ウシ、ラクダ科でCDR-H3長分布と代表的構造はどう異なるか。
2. H3のkinked型とextended型を配列から判別する規則は、現在の構造データでどこまで通用するか。
3. H3生成モデルを抗原条件付きにしたとき、結合性とpolyreactivityをどう同時評価すべきか。

## 自分の3行要約

- CDR-H3はV–D–J接合部から生じるため、6本のCDRの中でも配列と長さが特に多様になる。
- H3の長さと配座は結合面の地形を変えるが、抗原認識は他CDR・軽鎖・frameworkとの協働で決まる。
- H3構造予測とAI設計では、局所配列だけでなくFv・抗原の文脈と厳密なデータ分割が必要である。

## 未解決の疑問

抗原に結合していない抗体の配列だけから、CDR-H3が取り得る配座集団と各配座の存在比を、単一構造ではなく確率分布としてどこまで正しく予測できるだろうか。

## 参考文献

1. Chiu ML, Goulet DR, Teplyakov A, Gilliland GL. [Antibody Structure and Function: The Basis for Engineering Therapeutics](https://doi.org/10.3390/antib8040055). *Antibodies (Basel).* 2019;8:55.
2. IMGT®. [Correspondence between V numberings: CDR3-IMGT](https://www.imgt.org/IMGTScientificChart/Numbering/CDR3-IMGTposition.html). Accessed 2026-09-08.
3. North B, Lehmann A, Dunbrack RL Jr. [A New Clustering of Antibody CDR Loop Conformations](https://doi.org/10.1016/j.jmb.2010.10.030). *J Mol Biol.* 2011;406:228–256.
4. Weitzner BD, Dunbrack RL Jr, Gray JJ. [The Origin of CDR H3 Structural Diversity](https://doi.org/10.1016/j.str.2014.11.010). *Structure.* 2015;23:302–311.
5. Tsuchiya Y, Mizuguchi K. [The Diversity of H3 Loops Determines the Antigen-binding Tendencies of Antibody CDR Loops](https://doi.org/10.1002/pro.2874). *Protein Sci.* 2016;25:815–825.
6. Regep C, Georges G, Shi J, Popovic B, Deane CM. [The H3 Loop of Antibodies Shows Unique Structural Characteristics](https://doi.org/10.1002/prot.25291). *Proteins.* 2017;85:1311–1318.
7. Ruffolo JA, Sulam J, Gray JJ. [Antibody Structure Prediction Using Interpretable Deep Learning](https://doi.org/10.1016/j.patter.2021.100406). *Patterns.* 2022;3:100406.
8. Abanades B, Wong WK, Boyles F, et al. [ImmuneBuilder: Deep-Learning Models for Predicting the Structures of Immune Proteins](https://doi.org/10.1038/s42003-023-04927-7). *Commun Biol.* 2023;6:575.
