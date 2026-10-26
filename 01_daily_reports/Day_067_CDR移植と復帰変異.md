---
day: 67
topic: CDR graftingとback mutation――結合性を維持するヒト化
created: 2026-10-26
status: unread
---

# Day 067：CDR移植と復帰変異

## 今日の問い

非ヒト抗体のCDRをヒトframeworkへ移植しただけでは、なぜ結合性が低下することがあるのか。どのframework残基をback mutationの候補とし、どの実験で必要性を判定すればよいのか。

## 本文

### 1. CDR graftingは「ループのコピー」では終わらない

古典的なCDR graftingでは、非ヒトdonor抗体のVH・VLから各3本のCDRを取り、ヒト抗体のacceptor frameworkへ移す。Jonesらは1986年、マウス重鎖CDRをヒト可変ドメインへ移してhapten結合性を移植できることを示し、その後、蛋白質抗原を認識する抗体にも適用された[1–3]。

ただし、抗原結合部位はCDR配列だけで決まる交換部品ではない。frameworkはCDRの根元を支え、VHとVLの向きも決める。acceptorへの置換がCDR直下のpacking、水素結合、局所電荷、VH–VL界面を変えれば、CDR配列が同じでもparatopeの形や揺らぎが変わる。直接抗原に触れない残基でも`koff`を悪化させ、`KD`を上げ得る[5,6]。目標は、donorで成立したCDR–framework–VH/VLの協調関係を、よりヒトらしい配列上で再構成することである。

### 2. 最初の設計：CDR境界とacceptorを明示する

まず親抗体のVH・VL配列を定め、Kabat、Chothia、IMGTなど、どの番号付け・CDR定義を使うか固定する。定義により、とくにH-CDR1、H-CDR2周辺で移植範囲が変わるため、定義のないCDR配列だけでは設計を再現できない[7]。

次にヒトgermlineまたは既知ヒト抗体からacceptor候補を選ぶ。framework全体の配列同一性は出発点になるが、それだけで決めない。CDR長とcanonical構造を支える残基、CDR直下、VH–VL界面、埋もれたcoreの適合性を見る。Queenらはanti-Tac抗体で、相同性に加えて構造モデルからCDRまたは抗原と相互作用しそうなCDR外残基を残し、親抗体の約3分の1のaffinityを得た[4]。「最も似た配列」と「構造的に合う骨格」は同じとは限らない。

### 3. Back mutationは仮説を検証する復帰変異である

CDR移植後に結合や機能が低下したとき、ヒトacceptor残基を対応するdonor残基へ戻す操作がback mutation（復帰変異）である。候補は、(1) CDR直下でloopを支えるVernier zone、(2) CDR接触残基、(3) VH–VL界面、(4) 抗原へ直接触れ得るframework残基、(5) core packingや安定性に関わる残基から選ぶ。

FooteとWinterはanti-lysozyme抗体D1.3で、frameworkのH27、H29、H71、L71が結合自由エネルギーへ寄与し、組合せによりヒト化体のaffinityを親抗体の4倍以内まで回復した。差は主に解離速度に現れた[6]。frameworkがCDR形状を介して間接的に結合を制御する実例である。

ただしVernier候補を全部戻すと、非ヒト残基が不必要に増え、因果も分からない。まず「CDR移植のみ」の基準体を作り、単独変異または小さな組合せを比較し、必要な復帰変異だけを残す。back mutationは失った親抗体の性質を再現する操作であり、親を超える新規変異を探すaffinity maturationとは区別する。

変異効果は常に足し算になるとは限らない。ある残基は単独では無効でも、別の残基と同時に戻すとCDRのpackingが整うことがある。これはepistasisであり、単独変異の結果だけで有望な組合せを捨てる危険を示す。一方、候補5残基を全組合せすると32通りになるため、構造仮説で絞った小規模matrixやdisplay選択を用いる。各variantの完全なVH・VL配列と測定値を保存すれば、後から相互作用を解析できる。

### 4. 段階的な実験で因果を切り分ける

比較する最小系列は、親抗体、同じヒトFcを持つキメラ体、graft-only体、back mutation変異体群である。まず発現量と単量体率を確認し、Fabまたは低密度条件で`kon`、`koff`、`KD`を測る。細胞表面結合と機能assayは別に行う。IgG avidityだけでは小さなaffinity低下を隠すからである。

候補間では抗原調製法、固定化方向、表面密度、温度、再生条件を揃える。親抗体だけFab、ヒト化体だけIgGで測る比較や、単一濃度の結合シグナルだけでの判定は避ける。`KD`が同等でも`kon`低下と`koff`低下が相殺されていることがあり、細胞上の受容体占有や作用時間は変わり得る。速度定数まで読むことで、数値上の「回復」が同じ機構かを判断できる。

HER2抗体4D5では、graft中心のhumAb4D5-1の`KD`は25 nMだったが、構造モデルに基づく追加変異体humAb4D5-8は0.10 nMとなり、マウス親抗体の0.30 nMより強く結合した[8]。完成品だけでなく中間変異体を並べ、各残基の寄与と細胞増殖抑制を検証した点が重要である。

結合を救済しても、発現、熱安定性、凝集、polyreactivityが悪化すれば不十分である。近年のmatrixed CDR graftingは複数のVH・VL frameworkを組み合わせ、発現、affinity、物性、機能を順に比較する。配列相同性と機能は単純対応しないため、初期から複数候補を残す[9]。

### 5. 成功の定義は「親和性回復」だけではない

最終候補では`KD`だけでなく、`kon`と`koff`、エピトープ、交差反応性、細胞機能、発現・安定性を確認する。復帰変異が抗原接触を増やしたのか、CDR形状を整えたのか、avidityで見かけ上救済されたのかを区別し、残した非ヒト残基と理由を配列表に記録する。

ヒト化は非ヒト残基数の単純な最小化ではない。結合・機能・物性を保ちながら、説明できる最小限の非ヒト残基を残す多目的設計である。完成候補、基準体、失敗候補が揃って初めて、どの変異が何を回復したかを追跡できる。

実験前に、親抗体比で許容するaffinity低下、機能活性、発現量、単量体率などの判定基準を置くと、都合のよい指標だけを選ぶことを防げる。候補Aは結合が最良、候補Bは安定性が最良という場合、適応疾患、投与量、製剤濃度を踏まえて次段階へ進める複数候補を選ぶ。最終選択は一つのscoreではなく、用途に即した証拠の組合せで行う。

## 図または比較表

```text
donor VH/VL配列
  ↓ CDR定義を固定（Kabat / Chothia / IMGT）
複数のhuman acceptorを選ぶ
  ↓
CDR graftのみの基準体 ── 結合・発現低下なし ─→ 物性・機能を確認
  │
  └ 結合・発現低下あり
        ↓ 構造・配列から候補残基を立てる
   単独／小組合せback mutation
        ↓
   KD・kon・koff＋細胞機能＋developabilityで採否
```

| 候補残基の型 | 低下を起こす仕組み | 優先して見る測定 | 採用判断 |
|---|---|---|---|
| CDR直下・Vernier zone | loopの形・柔軟性が変わる | `koff`、`KD`、構造モデル | 再現性よく結合を救済するか |
| CDR接触残基 | packingや水素結合が失われる | 発現、Tm、速度論 | 結合と安定性を同時に改善するか |
| VH–VL界面 | domain間角度が変わる | Fab速度論、発現、単量体率 | 鎖の組合せ依存性を解消するか |
| 抗原接触framework残基 | paratope表面が欠ける | epitope、alanine scan、構造 | 直接接触の証拠があるか |
| 表面露出残基 | humannessへ影響しやすい | humanness、HLA-II予測 | 機能上不要ならヒト残基を保つ |

## 論文を読むためのポイント

1. **CDR定義を確認する**：Kabat、Chothia、IMGTのどれか。移植境界と番号付けは再現可能か。
2. **acceptor選択の根拠を見る**：全体相同性だけか、canonical残基、VH–VL界面、構造、germline頻度も考慮したか。
3. **変異系列を追う**：親、キメラ、graft-only、各back mutationを同条件で比較したか。
4. **結合値を分解する**：`KD`だけでなく`kon`・`koff`を示し、IgG avidityで差を隠していないか。
5. **機能と物性を見る**：細胞機能、発現、単量体率、Tm、凝集、非特異的結合を評価したか。
6. **残存非ヒト残基を数える**：どの残基を、どの実験根拠で残したか。予測だけで採用していないか。

## 抗体×AIとの接続

AIによるヒト化では、入力をVH・VL配列だけにせず、CDR定義、VH–VL pairing、予測構造、残基の溶媒露出、CDR接触、界面、ヒトrepertoire頻度を含めると、back mutation候補を順位づけしやすい。出力もhumanness単独ではなく、親和性維持、発現、安定性、凝集、polyreactivity、予測T細胞エピトープを並べる必要がある。

学習データでは完成した成功配列だけを集めない。graft-only体、単独変異体、不成功変異体を同じassayで測った系列は、残基変更と表現型の因果を学ぶ貴重なデータである。train/testを同じ親抗体由来の近縁変異体でランダム分割すると性能を過大評価するため、親抗体またはclonotype単位で分ける。AIの提案は候補削減に使い、最終判断はmatched experimental panelで行う。

## 重要用語（8語）

- **CDR grafting**：donor抗体のCDRをヒトacceptor frameworkへ移植するヒト化法。
- **donor抗体**：CDRと抗原結合性の供給元になる非ヒト親抗体。
- **acceptor framework**：donor CDRを受け入れるヒト由来の可変領域骨格。
- **back mutation（復帰変異）**：ヒト化位置をdonor親抗体の残基へ戻し、機能や構造を回復させる変異。
- **Vernier zone**：CDR直下でloopの立体配置を支えるframework残基群。
- **canonical structure**：主にCDR長と特定残基で決まる、抗体loopの代表的な主鎖構造。
- **VH–VL interface**：重鎖・軽鎖可変ドメインが接触し、paratopeの配置へ影響する面。
- **graft-only体**：back mutationを加えず、定義したCDRだけをacceptorへ移した基準ヒト化体。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

CDR配列が親抗体と同じでも、graft-only体の`KD`が悪化する理由を二つ挙げよ。

**模範回答：** acceptor frameworkへの置換により、CDR直下のpackingやVH–VLの向きが変わり、paratopeの形や柔軟性がずれるためである。その結果、抗原との直接接触を変えなくても、とくに解離が速くなることがある。

### 問2

back mutation候補をすべて一度に導入せず、単独または小さな組合せで試す利点は何か。

**模範回答：** 各残基が結合・発現・安定性へ与える因果を切り分け、不要な非ヒト残基を残さずに済む。graft-only体と親・キメラ体を共通対照にすれば、救済量も自己採点できる。

## さらに調べる疑問2〜3問

1. CDR境界をKabatからIMGTへ変えると、同じ抗体で移植残基とback mutation候補はどう変わるか。
2. 単独では効果のない二つのframework変異が、組合せでのみ結合を回復するepistasisをどう探索するか。
3. humanness、HLA-II予測、発現、親和性を多目的最適化するとき、候補順位は重みづけでどれほど変わるか。

## 自分の3行要約

- （1行目）
- （2行目）
- （3行目）

## 未解決の疑問

- （学習後に記入）

## 参考文献

1. Jones PT, et al. [Replacing the complementarity-determining regions in a human antibody with those from a mouse](https://doi.org/10.1038/321522a0). *Nature.* 1986;321:522–525.
2. Riechmann L, et al. [Reshaping human antibodies for therapy](https://doi.org/10.1038/332323a0). *Nature.* 1988;332:323–327.
3. Verhoeyen M, et al. [Reshaping human antibodies: grafting an antilysozyme activity](https://doi.org/10.1126/science.2451287). *Science.* 1988;239:1534–1536.
4. Queen C, et al. [A humanized antibody that binds to the interleukin 2 receptor](https://doi.org/10.1073/pnas.86.24.10029). *Proc Natl Acad Sci U S A.* 1989;86:10029–10033.
5. Chothia C, Lesk AM. [Canonical structures for the hypervariable regions of immunoglobulins](https://doi.org/10.1016/0022-2836(87)90412-8). *J Mol Biol.* 1987;196:901–917.
6. Foote J, Winter G. [Antibody framework residues affecting the conformation of the hypervariable loops](https://doi.org/10.1016/0022-2836(92)91010-M). *J Mol Biol.* 1992;224:487–499.
7. Chiu ML, et al. [Antibody structure and function: The basis for engineering therapeutics](https://doi.org/10.3390/antib8040055). *Antibodies.* 2019;8:55.
8. Carter P, et al. [Humanization of an anti-p185HER2 antibody for human cancer therapy](https://doi.org/10.1073/pnas.89.10.4285). *Proc Natl Acad Sci U S A.* 1992;89:4285–4289.
9. Gupta P, et al. [Matrixed CDR grafting: A neoclassical framework for antibody humanization and developability](https://doi.org/10.1016/j.jbc.2023.105555). *J Biol Chem.* 2024;300:105555.
