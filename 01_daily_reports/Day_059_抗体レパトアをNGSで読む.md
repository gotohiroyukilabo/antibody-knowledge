---
day: 59
topic: 抗体レパトアとNGS――大量の抗体配列を読む
created: 2026-10-18
status: unread
---

# Day 059：抗体レパトアをNGSで読む

## 今日の問い

血液や組織から得た大量の抗体配列は、B細胞集団の何を直接観測し、何を推定しているのだろうか。また、read数をそのままclone数と見なせないのはなぜか。

## 本文

### 1. レパトアNGSが観測するもの

**抗体レパトア**とは、個体や組織、ある時点のB細胞がもつB細胞受容体（BCR）・抗体配列の集合である。V(D)J再構成、接合部多様性、重鎖・軽鎖の組合せ、体細胞超変異が巨大な多様性を作る。NGSを用いるAIRR-seqは、多数の再構成配列からV・D・J使用、CDR3、変異、isotype、clone頻度、系統を調べる[1–3]。

しかし結果は体内レパトアの完全な一覧ではない。採取部位・時点、B細胞subset、細胞数、核酸抽出、library調製を通過した**標本**である。末梢血は骨髄・リンパ節のB細胞や血清抗体をそのまま表さない。sequencingを深くしても、採取されなかったcloneは回復できない。「観測clone数」と「個体の総多様性」を区別する[1,2]。

### 2. gDNAとcDNAでread数の意味が変わる

bulk AIRR-seqはgenomic DNA（gDNA）か、mRNAを逆転写したcDNAを読む。gDNAでは再構成座位のcopy数が細胞あたりほぼ一定なので、適切に補正した頻度はcloneの**細胞数**に近い。cDNAは発現配列を高感度に読め、constant領域からisotypeも判定できる。一方、BCR転写量はnaive B細胞と抗体分泌細胞で大きく違う。cDNA read数は細胞数と一細胞当たり転写量の積であり、clone細胞数そのものではない[2–4]。

multiplex PCRではV遺伝子ごとのprimer適合度が増幅率を変える。5′ RACEは共通adapterによりV primer biasを減らせるが、逆転写・adapter付加・PCRのbiasは残る。鋳型、増幅法、投入細胞数、PCR cycle数を見ずにread数を生物学的頻度へ変換してはいけない。

### 3. UMIで直せる誤差、直せない偏り

PCR前の各鋳型へランダムな**unique molecular identifier（UMI）**を付け、同じUMI由来のreadをconsensus化すると、PCR duplicateを一分子として数えられる。polymerase・sequencing errorを真の体細胞超変異と誤認する危険も減る。ShugayらのMIGECはこの分子識別をrepertoire解析へ実装した[5]。

UMIにも別分子へ同じtagが付くcollision、UMI自体の誤読、少数readのUMI群、付加前の逆転写biasがある。consensus条件によって残る配列も変わる。さらにUMIは、採取されなかった細胞や抽出時に失われた分子を戻せない。独立にlibraryを作るtechnical replicateは、希少cloneのdropoutや頻度の不安定さを見つける助けになる。

### 4. readからcloneへは推定が積み重なる

生readはquality filtering、UMI consensus、V(D)J germlineへのalignment、CDR3・productive配列の判定、重複除去、clonal family clustering、系統解析を通る。IgBLASTなどがV・D・Jとframework/CDRを注釈する[6]。個人のgermline alleleが参照databaseになければ、遺伝差を体細胞超変異と誤る可能性がある。

**sequence**と**clonotype／clonal family**は同義ではない。一つの祖先B細胞由来の系統も、体細胞超変異により複数配列を含む。同一V/J、近いCDR3長・配列などでcluster化するが、閾値が厳しすぎれば一系統を分割し、緩すぎれば別系統を統合する[2]。同じCDR3 amino acidも独立に生成され得る。clone定義とsoftware versionを読まずに、多様性指標を比較してはいけない。

### 5. 配列頻度だけでは機能を証明できない

出力にはV/J使用率、CDR3長、変異率、isotype割合、clone頻度、多様性指標、lineage treeがある。ワクチン後のclone増加は免疫応答の候補証拠だが、抗原特異性や中和能の証明ではない。抗原probeによるsorting、重鎖・軽鎖を組み合わせた組換え抗体、結合・機能assayへ接続する必要がある。

sample比較では投入細胞数とsequencing depthを考慮する。1万細胞と100万細胞由来のlibraryを同じread数へdownsamplingしても、生物学的sampling差は消えない。健常者10人の深い解析では、各人のレパトアが非常に多様な一方、共有clonotypeも観察された[7]。共有配列は興味深いが、同じ抗原への結合を直ちに意味しない。

bulk sequencingでは、別々に読んだ重鎖と軽鎖を元の一細胞の組合せへ戻せないことが多い。重鎖CDR3だけでcloneを追跡する研究も、完成した抗体の結合部位全体を直接読んだわけではない。single-cell V(D)J法は細胞barcodeで天然の重鎖・軽鎖pairingを保てるが、回収細胞数、捕捉効率、doublet、dropoutという別の制約をもつ。論文の「抗体配列」が重鎖のみか、paired VH/VLかを必ず確認する。

AIRR CommunityのMiAIRRはstudy・subject、sample、試料処理、sequencing、data processing、処理済み配列の最小情報を定める[8]。配列数だけでなく、donor、組織、時点、subset、DNA/cDNA、primer、UMI、chain、参照germline、pipeline、clone定義を確認する。抗体レパトアNGSの価値は、多数の文字列を得ることではなく、その配列が生じた生物試料と測定過程を追跡できることにある。

## 図または比較表

```text
個体内のB細胞集団
  ↓ 採血・組織・時点・subset選択（生物学的sampling）
細胞 → gDNA または RNA→cDNA
  ↓ primer／5′ RACE・UMI・PCR（library bias）
NGS reads
  ↓ QC → UMI consensus → V(D)J注釈 → clone clustering
観測レパトア
  ↓
多様性・clone拡大・系統を推定 → 組換え抗体と機能assayで検証
```

| 観点 | gDNAベース | cDNAベース |
|---|---|---|
| 主に近い量 | 再構成をもつ細胞数 | 抗体転写物の分子数 |
| 強み | 細胞頻度を比較しやすい | 高感度、発現配列・isotypeを捉えやすい |
| 主なbias | 非productive配列、primer・PCR bias | 逆転写、細胞種ごとの転写量、primer・PCR bias |
| read数の解釈 | 条件が適切ならclone細胞数のproxy | 細胞数と一細胞当たり発現量が混在 |
| 適した問い | clone頻度、clonality | 発現レパトア、isotype、成熟系統 |

## 論文を読むためのポイント

1. **母集団と標本を分ける**：donor、組織、時点、B細胞subset、入力細胞数を確認する。
2. **鋳型の意味を読む**：gDNAかcDNAか、read countが細胞数・分子数のどちらに近いかを見る。
3. **増幅法を確認する**：multiplex PCRか5′ RACEか、primer biasとPCR cycle数が報告されているか。
4. **誤り補正を監査する**：UMI付加時点、consensus条件、technical replicate、synthetic controlを見る。
5. **注釈の前提を確認する**：germline database、softwareとversion、productive判定、CDR3定義を読む。
6. **clone定義を読む**：V/J、CDR3長、nucleotide／amino acid identityの閾値を確認する。
7. **機能を過剰解釈しない**：拡大や共有だけで抗原特異性を断定せず、組換え抗体での検証を見る。

## 抗体×AIとの接続

レパトアNGSはprotein language modelの事前学習、抗原特異性予測、生成確率や体細胞超変異のモデル化に使える大規模データである。しかし、回収された配列は「自然界で機能する抗体」の無作為標本ではなく、donor、組織、B細胞subset、発現量、primer、pipelineで条件づけられた観測である。未観測配列をnegative、clone拡大をbinding labelと置くのは危険である。

同一donor、同一clonal family、同一時系列sampleの近縁配列がtrain/testへ分かれると、モデルは抗原認識則ではなく系統を記憶できる。分割はsequence単位でなくclonal family、donor、study単位を候補にし、目的が未知donorか未知抗原かを先に定める。入力配列にはchain、isotype、sample、UMI補正、clone定義、assay provenanceを残し、抗原特異性やaffinityを学ばせるなら独立した結合・機能測定を教師ラベルにする。

## 重要用語（8語）

- **antibody repertoire**：ある個体・組織・時点で存在または観測されるBCR／抗体配列の集合。
- **AIRR-seq**：適応免疫受容体の再構成配列を高スループットで読む方法の総称。
- **clonotype／clonal family**：共通の再構成祖先に由来すると推定される配列群。定義は解析法に依存する。
- **UMI**：PCR前の鋳型分子を識別し、重複除去とconsensus誤り補正に使うランダムbarcode。
- **5′ RACE**：転写物5′端へ共通adapterを付加し、V遺伝子別primerへの依存を減らす増幅法。
- **V(D)J annotation**：観測配列へV・D・J遺伝子、CDR3、変異などを割り当てる処理。
- **sampling depth**：試料から取得した細胞・鋳型・readの規模。sequencing depthだけでは決まらない。
- **MiAIRR**：AIRR-seq研究を再利用可能にするための最小metadata報告標準。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

cDNA由来のある抗体配列がreadの20%を占めたとき、そのcloneがB細胞の20%を占めると直ちに言えないのはなぜか。

**模範回答：** cDNA read数にはclone細胞数だけでなく、一細胞当たりのBCR転写量、逆転写効率、primer・PCR biasが影響する。特に抗体分泌細胞は転写物が多いため、細胞頻度を過大に見せ得る。

### 問2

UMIを使えば、元の個体内レパトアを完全に復元できるか。

**模範回答：** できない。UMIは主にPCR duplicateと一部の配列誤りを補正するが、採取されなかった細胞、抽出・逆転写で失われた分子、UMI付加前のbiasは回復できない。

## さらに調べる疑問2〜3問

1. clone clusteringの配列identity閾値を変えると、多様性とclone拡大の結論はどの程度変わるか。
2. 血中B細胞レパトアと血清抗体proteomeを対応づけるには、どの測定を組み合わせる必要があるか。
3. 未知抗原への汎化を測るAIデータ分割では、donor・clonal family・抗原をどの順でgroup化すべきか。

## 自分の3行要約

- （1行目）
- （2行目）
- （3行目）

## 未解決の疑問

- （学習後に記入）

## 参考文献

1. Georgiou G, et al. [The promise and challenge of high-throughput sequencing of the antibody repertoire](https://doi.org/10.1038/nbt.2782). *Nat Biotechnol.* 2014;32:158–168.
2. Yaari G, Kleinstein SH. [Practical guidelines for B-cell receptor repertoire sequencing analysis](https://doi.org/10.1186/s13073-015-0243-2). *Genome Med.* 2015;7:121.
3. Calis JJA, Rosenberg BR. [Characterizing immune repertoires by high throughput sequencing: strategies and applications](https://doi.org/10.1016/j.it.2014.09.004). *Trends Immunol.* 2014;35:581–590.
4. Greiff V, et al. [Systems Analysis Reveals High Genetic and Antigen-Driven Predetermination of Antibody Repertoires throughout B Cell Development](https://doi.org/10.1016/j.celrep.2017.03.054). *Cell Rep.* 2017;19:1467–1478.
5. Shugay M, et al. [Towards error-free profiling of immune repertoires](https://doi.org/10.1038/nmeth.2960). *Nat Methods.* 2014;11:653–655.
6. Ye J, et al. [IgBLAST: an immunoglobulin variable domain sequence analysis tool](https://doi.org/10.1093/nar/gkt382). *Nucleic Acids Res.* 2013;41:W34–W40.
7. Briney B, et al. [Commonality despite exceptional diversity in the baseline human antibody repertoire](https://doi.org/10.1038/s41586-019-0879-y). *Nature.* 2019;566:393–397.
8. Rubelt F, et al. [Adaptive Immune Receptor Repertoire Community recommendations for sharing immune-repertoire sequencing data](https://doi.org/10.1038/ni.3873). *Nat Immunol.* 2017;18:1274–1278.
