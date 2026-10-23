---
day: 64
topic: 配列重複とclonotype――AIデータセットでの独立性
created: 2026-10-23
status: unread
---

# Day 064：配列重複とclonotype分割

## 今日の問い

抗体配列が別々の行に記録されていても、なぜ独立な学習例とは限らず、AIモデルの評価前に重複とclonotypeを調べる必要があるのだろうか。

## 本文

### 1. 「別の行」と「独立な抗体」は違う

抗体データでは、一つのB細胞由来配列のPCR read、同じ配列の複数record、1残基違いのvariantが別々の行に現れ得る。完全一致をまとめる**deduplication**だけでは不十分である。B細胞cloneが体細胞超変異（SHM）で枝分かれし、共通祖先をもつ近縁配列を生むからだ[1–3]。

`read`、UMIでまとめた`molecule`、`unique sequence`、`cell`、`clonotype`は異なる単位である。100万readは100万個の独立な抗体ではない。sample数が何を数えた値か確認する。

### 2. clonotypeは何を同じとみなすか

生物学的なB細胞cloneは、同じnaive B細胞を祖先とする細胞群である。配列解析では、同じ重鎖V/J遺伝子とCDR-H3（junction）長をもつ配列を集め、CDR-H3距離が閾値以内のものを同じclonotypeと推定する[2,3]。共有SHMも手掛かりになる[3]。

ただし定義は一つではない。完全一致CDR-H3、約90%の類似性、可変領域全体、重鎖・軽鎖pairなど、規則は目的で変わる[1,4]。閾値が緩いと別系統を併合し、厳しいと一系統を分割する。別個体に独立に生じるpublic clonotypeもあり、「配列が似る」と「同じ祖先」は同義ではない。鎖、距離、閾値を読む。

### 3. random splitで起こる近縁配列リーク

親抗体のsingle-mutant群をrandom splitすると、trainに親配列と一部variant、testに残りが入る。モデルは近傍配列からラベルを補間できる。AIRR-seqでも同一clonotypeがsplitをまたげば、testは未知系統ではない。これが**similarity-induced leakage**である[6,7]。

完全一致を削っても、1残基違い、同じCDR-H3、同じlibrary由来という相関は残る。結合予測では、相同抗原が両側にあれば抗原側も記憶できる。SAbDabにも冗長性があるため、抗体と抗原の両方を監査する[8]。

### 4. 目的から分割単位を決める

まず一般化の対象を決める。親抗体の追加変異を順位づけるrandom splitは**系列内補間**を測る。新規系列ならclonotypeを一つのpartitionへまとめ、新規標的なら抗原cluster、新規campaignならcampaign、新規患者ならdonorを保持して分ける[6,7]。

実務では、(1) 配列を標準化、(2) 完全一致を統合しlabel矛盾を記録、(3) donor、parent、library、campaign、assay IDを保持、(4) clonotype/類似clusterを作成、(5) group単位でsplit、(6) test–train最近傍identityを報告する。抗体–抗原pairなら両者を扱う[7]。AIRR標準metadataは監査を支える[5]。

### 5. 厳しいsplitは低い点数でも価値が高い

cluster splitはtest数と性能が下がりやすいが、近傍記憶と外挿を分けられる。`random/variant`、`clonotype`、`antigen/campaign holdout`を並べ、差が大きければ系列内補間への依存を疑う。

独立性は二値ではない。最近傍identity、V/J重複率、抗原相同性、donor/campaignの交差数も示す。評価値は「そのsplitが模擬する問い」にだけ答える。厳しいsplitで低くても、未知系列への性能を正直に測る方が価値をもつ。

## 図または比較表

```text
同じclonotypeの親配列 A
        ├─ A1（SHM 1個） ─ train
        ├─ A2（SHM 2個） ─ train       random split：近縁情報が漏れる
        └─ A3（SHM 1個） ─ test   ← A1/A2からほぼ補間できる

group split
  clonotype A ─ 全てtrain
  clonotype B ─ 全てvalidation
  clonotype C ─ 全てtest       ← 未知系列への一般化を測る
```

| 分割法 | testが模擬する問い | 長所 | 主な限界 |
|---|---|---|---|
| 行単位random split | 同じ分布・系列内の未知record | 簡単、class比を保ちやすい | 近縁配列リークに弱い |
| exact-sequence group | 同一配列の再出現 | 完全重複を防ぐ | SHM variantは跨げる |
| clonotype/cluster split | 未知の抗体系統 | 系列記憶を抑える | 定義・閾値に依存する |
| donor/campaign split | 新規個体・新規実験 | batch依存を検出する | データ数と条件均衡が難しい |
| antibody＋antigen split | 未知の抗体–標的組合せ | 相互作用モデルに厳しい | 一部pairを割り当てにくい |

## 論文を読むためのポイント

1. **標本単位**：read、unique sequence、cell、variant、clonotypeのどれを`n`としているか。
2. **clonotype定義**：V/J、CDR-H3長、距離尺度、閾値、重鎖・軽鎖の利用が明記されているか。
3. **重複処理**：完全一致、別名、複数assay、親抗体由来variantの重複をどの段階で統合したか。
4. **splitの順序**：先に全データでgroupを作り、その後group単位で分けたか。行を分けてから各集合内で重複除去してもリークは防げない。
5. **二つの配列軸**：結合予測では抗体だけでなく抗原・epitopeの重複も監査したか。
6. **最近傍解析**：test–train間の最大identityやCDR-H3類似性と、性能の関係を示しているか。
7. **主張との整合**：系列内補間の結果から「未知抗体・未知抗原へ一般化」と飛躍していないか。

## 抗体×AIとの接続

抗体AIでは、高性能なmodelより先に**evaluation unit**を設計する。parent抗体の変異最適化なら系列内split、新規binder発見ならclonotype・campaign holdout、汎用的な抗体–抗原予測なら抗体clusterと抗原clusterの同時holdoutが対応する。pretrained protein language modelでは、事前学習corpusにtest配列または近縁配列が含まれる可能性も別の漏れとして記録する。

再現可能な報告には、raw sequence ID、正規化法、group ID、clustering toolとversion、距離・閾値、random seed、split一覧を残す。random splitと厳しいgroup splitを併記し、性能低下を隠さない。これにより「既知系列の補間が得意なモデル」と「新規系列へ移れるモデル」を同じaccuracyで混同せずに済む。

## 重要用語（8語）

- **deduplication**：同一配列や同一分子由来recordを検出し、解析単位に応じて統合する処理。
- **clonotype**：共通祖先に由来すると推定される免疫受容体配列群。操作的定義は研究ごとに異なり得る。
- **clonal family**：SHMで多様化した同一B細胞系統の配列群。clonotypeとほぼ同義に使われることがある。
- **sequence identity**：alignmentした位置のうち、同じ残基である割合。
- **group split**：同じgroupの全sampleを一つのpartitionだけへ割り当てる分割法。
- **data leakage**：本来test時に未知である情報が学習側へ入り、評価を不当に容易にすること。
- **public clonotype**：複数個体に独立に現れる、遺伝子使用とCDR3が似た抗体群。
- **out-of-distribution（OOD）**：学習時と異なる系列、抗原、campaignなどの分布に属するデータ。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

完全一致する抗体配列を削除した後でも、random splitにリークが残るのはなぜか。

**模範回答：** 同一clonotypeや同一親抗体由来のSHM variantは、完全一致でなくても配列とラベルが強く似る。近縁variantがtrainとtestを跨ぐと、testは未知系列ではなく既知系列の補間になる。

### 問2

未知の抗体と未知の抗原の組合せへの結合予測を評価したい。何をgroup化して分割すべきか。

**模範回答：** 抗体をclonotypeまたは配列類似clusterでまとめるだけでなく、抗原も相同性clusterでまとめ、両方の近縁群がtrainとtestを跨がないようにする。分割不能なpairの扱いも報告する。

## さらに調べる疑問2〜3問

1. CDR-H3 identityの閾値を80%、90%、100%に変えると、group数と評価性能はどう変わるか。
2. 重鎖だけのclonotypeと重鎖・軽鎖pairを用いたclonotypeで、結合性予測のリーク量はどれほど違うか。
3. protein language modelの事前学習corpusとtest setの重複を、公開情報の範囲でどう監査できるか。

## 自分の3行要約

- （1行目）
- （2行目）
- （3行目）

## 未解決の疑問

- （学習後に記入）

## 参考文献

1. Mhanna V, et al. [Adaptive immune receptor repertoire analysis](https://doi.org/10.1038/s43586-023-00284-1). *Nat Rev Methods Primers.* 2024;4:6.
2. Nouri N, Kleinstein SH. [A spectral clustering-based method for identifying clones from high-throughput B cell repertoire sequencing data](https://doi.org/10.1093/bioinformatics/bty235). *Bioinformatics.* 2018;34:i341–i349.
3. Nouri N, Kleinstein SH. [Somatic hypermutation analysis for improved identification of B cell clonal families from next-generation sequencing data](https://doi.org/10.1371/journal.pcbi.1007977). *PLoS Comput Biol.* 2020;16:e1007977.
4. Pelissier A, et al. [Exploring the impact of clonal definition on B-cell diversity](https://doi.org/10.3389/fimmu.2023.1123968). *Front Immunol.* 2023;14:1123968.
5. Rubelt F, et al. [Adaptive Immune Receptor Repertoire Community recommendations for sharing immune-repertoire sequencing data](https://doi.org/10.1038/ni.3873). *Nat Immunol.* 2017;18:1274–1278.
6. Wossnig L, et al. [Best practices for machine learning in antibody discovery and development](https://doi.org/10.1016/j.drudis.2024.104025). *Drug Discov Today.* 2024;29:104025.
7. Joeres R, et al. [Data splitting to avoid information leakage with DataSAIL](https://doi.org/10.1038/s41467-025-58606-8). *Nat Commun.* 2025;16:3337.
8. Dunbar J, et al. [SAbDab: the structural antibody database](https://doi.org/10.1093/nar/gkt1043). *Nucleic Acids Res.* 2014;42:D1140–D1146.
9. Olsen TH, et al. [Observed Antibody Space: A diverse database of cleaned, annotated, and translated unpaired and paired antibody sequences](https://doi.org/10.1002/pro.4205). *Protein Sci.* 2022;31:141–146.
