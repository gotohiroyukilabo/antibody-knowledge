---
day: 42
topic: BLI――ハイスループットな速度論測定
created: 2026-10-01
status: unread
---

# Day 042：BLIで高速に結合速度を測る

## 今日の問い

BLIはどのように抗体―抗原結合を多数並列で測り、どの条件を確認すれば `kon`、`koff`、`KD` を信頼できる速度論データとして読めるのだろうか。

## 本文

### 1. BLIは「結合で厚くなる層」を光の干渉で読む

Bio-layer interferometry（BLI）は、光ファイバー型biosensor先端の分子層に起こる結合を実時間で検出する手法である。sensor内部の参照面とligandを固定した先端面から反射する白色光は干渉する。溶液中のanalyteが結合すると光学的厚さが増し、干渉スペクトルが移動する。この変化をnm単位のwavelength shiftとして記録する[1,2]。SPRは金属表面近傍の屈折率変化、BLIは2つの反射光の干渉変化を読むが、どちらも表面化によるartifactを受ける。

測定は、①sensorの水和、②ligandのloadingまたはcapture、③bufferでbaseline、④analyte溶液でassociation、⑤analyteを含まないbufferでdissociation、の順に行う。sensor自体がplate内の液間を移動するため「dip-and-read」と呼ばれる。流路を使わず複数sensorを並列に動かせることが高throughputの源である[2,3]。

### 2. センサーグラムから求める量はSPRと同じ

単純な1:1反応なら、BLIでも次の速度式を用いる。

```text
dR/dt = kon × C × (Rmax − R) − koff × R
KD = koff / kon
```

`R` は波長shift、`C` はanalyte濃度である。複数濃度のassociationとdissociationをglobal fitし、共通の `kon` と `koff` を推定する。曲線の高さは分子量、活性ligand量、固定化密度にも依存するため、高い応答が高affinityを直接意味しない。濃度系列、blank、reference sensor、反復をそろえ、fit線だけでなく残差と濃度依存性を確認する[3,4]。

多数候補のoff-rate rankingにも使えるが、1濃度のscreening値は厳密な速度定数とは区別する。活性濃度や平衡へ近づく範囲を検証していない見かけのKDは、一次順位付けには使えてもassay間で比較可能な定数とは限らない。

補正では、ligandを載せたsensorのbuffer応答だけでなく、ligandを載せていないreference sensorへのanalyte応答も見る。両者を差し引くdouble referencingは、buffer mismatch、非特異的結合、sensor driftを減らす助けになる。ただし、大きな補正で生データの異常を隠してはいけない。補正前曲線も確認し、referenceの応答が試料濃度とともに増えるなら、buffer組成やblocking条件を先に直す。

### 3. なぜハイスループットなのか

使い捨てsensorを各wellへ浸すため、microfluidicsの洗浄や詰まりが少なく、独立試料を並列処理しやすい。適切なreferenceと非特異的結合対策があれば培養上清のscreeningにも利用できる。kinetics、濃度定量、競合、epitope binningを同じ基本装置で行え、数十〜数百cloneを絞る段階に向く[3,5]。

ただし、wellごとの蒸発、液量差、気泡、sensor間のloading差、振とう不足、温度差は系統誤差を作る。sensor先端が浸る液量を保ち、plate内にblank・reference・反復を分散する。plateや実験日をまたいで順位付けするなら、共通control抗体を各runへ入れる。

sensor chemistryも実験設計の一部である。biotin―streptavidinは強固な固定化に向くが、biotin化位置が結合面を塞がないことを確かめる。Protein A/Gや抗ヒトFcによるcaptureはIgGの配向をそろえやすい一方、抗体サブクラスやFc改変でcapture効率が変わり得る。amine couplingは広く使えるが配向が不均一になりやすい。候補間のloading差が大きい場合、最大応答の単純比較は避ける。

### 4. assay orientationと表面密度が値を変える

抗体をProtein A/G系sensorでcaptureし可溶性抗原を測る配置は、抗体の向きをそろえやすい。biotin化抗原をstreptavidin sensorへ固定し抗体をanalyteにする配置は、抗原panelを共有しやすい。しかしIgGを高密度抗原へ結合させると、2本のFabによるavidityで見かけの `koff` が遅くなり得る。抗原が多量体でも1:1仮定が崩れる。

ligandを高密度に載せるとsignalは増すが、正確さは必ずしも上がらない。表面近傍のanalyteが枯渇するmass transport limitationでは、拡散・混合が見かけのassociationを制限する。解離分子が隣のligandへ再結合するrebindingは、見かけの `koff` を遅くする。Kamatらは、低いcapture密度でこれらを抑え、最適条件ではBLIとSPR/SPRiの速度定数がよく一致することを示した[4]。低密度表面、十分な振とう、長いdissociation、異なるloading量や配置での再現を検証する。

### 5. BLIの数値を「条件付き測定値」として読む

BLIとSPRは、条件を最適化すれば近い速度定数を得られる。一方、高親和性相互作用では表面現象により溶液平衡法と10倍以上異なるKDが報告された例もある[3–5]。「BLIは粗い」「SPRは正しい」と装置名だけで決めず、試料品質、固定化化学、価数、loading、混合、観測時間、補正、fit modelを読む。

小分子や弱い応答ではsignal-to-noiseが制約になりやすい。非常に遅い解離も、短い観測では下限付近の同じ値に見える。報告値が測定可能範囲内か、`<` や `>` の打ち切りを通常値として扱っていないか確認する。BLIの強みは多数を同じ設計で比べて絞ることである。重要候補は配置を変えた測定、SPR、溶液平衡法、細胞機能assayなどで直交検証する。

論文やデータセットでは、装置名だけでなく温度、buffer、振とう速度、sensor種類、loading範囲、濃度系列、測定時間、fit model、反復数を残す。同じ抗体でも、pHや塩濃度、抗原の品質が変われば速度定数は変わる。代表曲線1本だけでなく全濃度のsensorgram、fit、残差、反復間変動があれば、読者は数値の識別可能性まで評価できる。

## 図または比較表

```text
水和 → ligand loading → baseline → association → dissociation
                     sensorを各wellへ移動（dip-and-read）

光ファイバー先端
  参照反射面 ───┐
                 ├─ 2つの反射光が干渉
  ligand表面 ───┘   analyte結合で光学的厚さ↑ → 波長shift↑
```

| 観点 | BLI | SPR | ELISA |
|---|---|---|---|
| 検出原理 | 反射光の干渉波長shift | 金属表面近傍の屈折率変化 | 標識による終点signal |
| 測定形式 | sensorをplateのwellへ浸す | 流路でanalyteを表面へ送る | plate上で反応・洗浄 |
| 実時間kinetics | 可能（kon、koff、KD） | 可能（kon、koff、KD） | 通常は不可 |
| 並列性 | 高い。独立試料のscreening向き | 装置のchannel構成に依存 | 非常に高い |
| 主な注意 | sensor差、振とう、rebinding、mass transport | 流路・参照、mass transport、再生 | 固相化、洗浄、標識、終点依存 |

## 論文を読むためのポイント

1. **測定配置**：何をsensorへ固定・captureし、何をanalyteにしたか。分子の価数は1:1仮定と整合するか。
2. **sensorとloading**：sensor chemistry、loading量（nm shift）、固定化法が示され、過剰な表面密度を避けているか。
3. **濃度と時間**：複数濃度がKDの上下を覆い、association・dissociation時間は速度に対して十分か。
4. **補正と反復**：blank analyte、reference sensor、double referencing、独立反復、共通controlがあるか。
5. **解析品質**：fit model、global/local fit、除外基準、残差、測定可能範囲が提示されているか。
6. **screeningか精密測定か**：単一濃度のrankingと、濃度系列から求めたkinetic constantsを混同していないか。

“High-throughput kinetic screening” は「大量候補の相対比較」を指す場合がある。各cloneの完全な濃度系列と独立反復を測ったのか、単一濃度で見かけのoff-rateを順位付けしたのかをMethodsで確認する。

## 抗体×AIとの接続

BLIは多数cloneへラベルを付けやすいため、抗体AIの学習データ源になり得る。しかし `KD`、`kon`、`koff`、単一濃度response、off-rate rankは別の教師ラベルである。sensor chemistry、assay orientation、抗体format、抗原の多量体状態、loading、濃度、温度、buffer、fit model、測定上限・下限もprovenanceとして保存する。

同じplateの反復や同一clonotypeをtrain/testへ分散すると、配列だけでなくrun固有のbiasまで共有して性能が過大評価される。clonotype・抗原・実験runを意識して分割し、共通controlでrun効果を監視する。active learningで候補を選ぶ場合も、高throughputなBLI screeningの後に直交法と細胞機能で少数を再測定し、「測りやすいbinder」だけを最適化しない設計が必要である。

## 重要用語（8語）

- **BLI**：biosensor先端の光学的厚さの変化を、反射光の干渉波長shiftとして測る手法。
- **dip-and-read**：sensorをplate内の異なる溶液へ順に浸して測定する方式。
- **wavelength shift**：結合に伴う干渉スペクトルの波長変化。一般にnmで表示される応答値。
- **biosensor loading**：ligandをsensor先端へ固定またはcaptureする工程とその応答量。
- **assay orientation**：抗体と抗原のどちらを表面側・溶液側に置くかという測定配置。
- **mass transport limitation**：表面へのanalyte供給が結合反応より遅く、見かけの速度を制限する状態。
- **rebinding**：解離したanalyteが表面から離れる前に別のligandへ再結合する現象。
- **epitope binning**：抗体どうしの競合パターンから、認識部位が近い群へ分類する測定。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

BLIでligandのloading量を増やすと応答が大きくなった。なぜ、その条件が正確なkinetics測定に最適とは限らないのか。

**模範回答：** 高密度表面ではanalyte供給が律速になるmass transport limitationや、解離分子のrebinding、IgGの二価結合が起こりやすい。signalの大きさと速度定数の正確さは別なので、低密度条件でも値が再現するか確認する。

### 問2

単一濃度のBLIで100 cloneのoff-rateを順位付けした。この結果をそのまま精密なKDデータセットとしてAIへ使えるか。

**模範回答：** そのままでは使えない。単一濃度のoff-rate rankingは候補比較用で、濃度系列から求めた `kon` と `KD` ではないため、ラベル種別と測定限界を明示し、重要候補は濃度系列と直交法で再測定する。

## さらに調べる疑問2〜3問

1. BLIのepitope binningで、競合と立体障害をどの対照実験で区別できるか。
2. 培養上清を直接測るとき、非特異的結合と抗体濃度差をどう補正するか。
3. BLIとSPRでKDが一致しない場合、assay orientation、表面密度、活性濃度をどの順に検証すべきか。

## 自分の3行要約

- （1行目）
- （2行目）
- （3行目）

## 未解決の疑問

- （学習後に記入）

## 参考文献

1. Sultana A, Lee JE. [Measuring protein-protein and protein-nucleic acid interactions by biolayer interferometry](https://doi.org/10.1002/0471140864.ps1925s79). *Curr Protoc Protein Sci.* 2015;79:19.25.1–19.25.26.
2. Sartorius. [Biomolecular Binding Kinetics Assays on the Octet BLI Platform](https://www.sartorius.com/resource/blob/742330/05671fe2de45d16bd72b8078ac28980d/octet-biomolecular-binding-kinetics-application-note-4014-en-1--data.pdf). Application Note, 2022.
3. Abdiche Y, Malashock D, Pinkerton A, Pons J. [Determining kinetics and affinities of protein interactions using a parallel real-time label-free biosensor, the Octet](https://doi.org/10.1016/j.ab.2008.03.035). *Anal Biochem.* 2008;377:209–217.
4. Kamat V, Rafique A. [Designing binding kinetic assay on the bio-layer interferometry biosensor to characterize antibody-antigen interactions](https://doi.org/10.1016/j.ab.2017.08.002). *Anal Biochem.* 2017;536:16–31.
5. Estep P, Reid F, Nauman C, et al. [High throughput solution-based measurement of antibody-antigen affinity and epitope binning](https://doi.org/10.4161/mabs.23049). *mAbs.* 2013;5:270–278.
6. Noy-Porat T, Alcalay R, Mechaly A, et al. [Characterization of antibody-antigen interactions using biolayer interferometry](https://doi.org/10.1016/j.xpro.2021.100836). *STAR Protoc.* 2021;2:100836.
