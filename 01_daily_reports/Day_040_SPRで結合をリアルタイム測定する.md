---
day: 40
topic: SPRの原理――結合と解離をリアルタイムで測定する
created: 2026-09-29
status: unread
---

# Day 040：SPRで結合をリアルタイム測定する

## 今日の問い

SPRは蛍光標識なしで抗体と抗原の結合・解離をリアルタイムに追える。それでは装置が実際に検出している物理量は何で、得られた曲線のどこまでを「分子固有の結合性」と解釈してよいのだろうか。

## 本文

### 1. SPRが見ているのは金膜近傍の屈折率変化

表面プラズモン共鳴（surface plasmon resonance; SPR）は、金などの薄い金属膜へ偏光を当て、金属中の自由電子の集団振動である表面プラズモンを励起する現象を利用する。特定の入射角または波長で反射光が最小になる共鳴条件は、金膜に接する溶液側の屈折率に敏感である[1]。

抗体測定では、一方を**ligand**としてセンサーチップ表面へ固定し、他方を**analyte**として流す。analyteが結合すると金膜近傍の局所屈折率が変わり、装置はその変化をresponse unit（RU）などへ変換して時間に対して描く。これがsensorgramである。抗原―抗体相互作用を標識なしで連続測定できることが大きな利点である[2,3]。

ただしSPRは結合部位を撮像せず、分子を一個ずつ数えない。RUは表面近傍の質量変化に概ね比例するので、同じモル数でも大きなanalyteほど応答が大きくなりやすい。最大RUをそのまま「結合の強さ」とは解釈できない。

### 2. 1回の測定サイクルを4段階に分ける

まずrunning bufferでbaselineを作る。既知濃度のanalyteを注入すると、結合と既存複合体の解離が同時に進む。正味の結合量が増える区間がassociation phaseである。注入を止めてbufferへ戻すと新規供給がなくなり、主に複合体の減少を追うdissociation phaseとなる。必要なら残存analyteを外すregenerationを行い、表面を次の測定へ戻す[4]。

単純な1:1相互作用を `A + B ⇄ AB` とすれば、association rate constant `kon`（M⁻¹s⁻¹）とdissociation rate constant `koff`（s⁻¹）から `KD = koff / kon` となる。同じKDでも「速く結合して速く外れる」抗体と「遅く結合して遅く外れる」抗体があり得る。SPRはこの時間軸を分けられるが、速度定数は複数濃度の曲線へ反応モデルを当てはめた推定値である。良いfitだけでは、そのモデルが実際の機構として正しいとは証明できない[4,5]。

### 3. 「ラベルフリー」は「無摂動」ではない

蛍光色素や酵素標識が不要なので、標識による結合阻害や標識率差を避けられる。一方、少なくとも片方を表面へ提示する。一般的なamine couplingでは複数の一級アミンを介して固定するため、方向が不均一になり、paratopeやepitopeが隠れたり構造が変わったりし得る。biotin–streptavidinやcapture法は方向を制御しやすいが、タグやcapture分子の影響が加わる[6]。

抗体と抗原のどちらを固定するかという**assay orientation**も重要である。IgGを流し、表面の抗原密度が高いと、二つのFabによるavidityや、外れた分子が近傍へ再結合するrebindingで解離が遅く見えることがある。単価に近いkineticsを測るには、抗体をcaptureして単量体抗原を流す、ligand密度を下げるなどの設計が必要になる。「ラベルフリー」は「測定による摂動がない」という意味ではない。

### 4. sensorgramには結合以外の信号も入る

試料とrunning bufferの塩濃度、DMSO、glycerolなどが違うと、注入中に溶液全体の屈折率が変わり、結合がなくてもbulk responseが出る。空表面または無関係ligandを置くreference channelをactive channelから引き、さらにbufferのみのblank injectionを引くdouble referencingは、非特異的応答、注入ノイズ、driftを減らす基本操作である[5]。ただし大きな非特異的結合を計算で救う方法ではなく、bufferを合わせ、凝集体を除き、適切なreferenceを作ることが先である。

analyteはbulk溶液から表面へ拡散して初めて結合できる。結合が非常に速い、ligand密度が高い、流速が低いと、分子反応でなく表面への供給が律速となるmass transport limitationが生じ、観測associationが本来のkonより遅く見える[7]。低密度表面と高めの流速を使い、流速を変えても推定値が保たれるかを調べる。解離分子のrebindingは見かけのkoffも遅くする。

### 5. SPRが支持する主張の範囲を守る

質の高い実験では、濃度系列、zero-analyte blank、reference surface、反復、十分な観測時間を設ける。ligand活性、理論的Rmaxと実測応答の整合、再生による表面劣化も確認する。高いligand密度は信号を増すが、crowding、avidity、mass transportを悪化させるため、最大信号より解釈可能性を優先する[4,5]。

濃度系列は推定KDの上下を覆い、低濃度から高濃度まで曲線形状の情報を含むようにする。高濃度だけなら表面がすぐ飽和し、konを識別しにくい。低濃度だけなら信号対雑音比が不足する。非常に遅い解離を評価するには長いdissociation時間が必要で、短い観測窓からkoffを外挿すると不確実性が大きい。条件は測りたい速度域に合わせて設計する。

SPRが直接支持するのは「指定した固定化、buffer、温度、流速、濃度範囲、モデル下の表面結合」である。可溶性抗原への単価結合を、細胞膜上のavidityや機能へそのまま外挿してはいけない。native抗原への結合はflow cytometry、機能はcell-based assayで補い、結果が違えば抗原構造、価数、密度、輸送の違いを考える。

## 図または比較表

```text
プリズム／光学系
      ↓ 偏光
===================  金薄膜
ligand ligand ligand  ← センサー表面へ固定
   ↑ analyteが結合     ← flow中に注入
-------------------  running buffer

結合で金膜近傍の屈折率が変化
      ↓
共鳴角（または波長）が移動
      ↓
時間–応答曲線（sensorgram）として記録
```

| sensorgramの区間 | 表面で起きる主なこと | 読み取れる情報 | 主な注意点 |
|---|---|---|---|
| baseline | bufferのみが流れる | 表面・装置の安定性 | drift、前試料のcarryover |
| association | analyteの結合と解離が同時進行 | 濃度依存の立ち上がり | bulk response、mass transport |
| dissociation | 新規供給が止まり複合体が減る | 解離の速さ | rebinding、観測時間不足 |
| regeneration | 残存analyteを除く | 表面の再利用性 | ligand失活、再生不十分 |

## 論文を読むためのポイント

1. **測定配置を見る**：抗体と抗原のどちらがligand／analyteか、analyteは単価か多価か。
2. **表面を評価する**：固定化法、ligand density、Rmax、固定化後の活性が報告されているか。
3. **溶液条件を見る**：温度、buffer、添加剤、流速、濃度系列、association・dissociation時間が明記されているか。
4. **補正を確認する**：reference surfaceとblank injectionによるdouble referencingがあるか。
5. **artifactを疑う**：mass transport、rebinding、avidity、非特異的結合、凝集、surface heterogeneityを検討したか。
6. **主張の範囲を守る**：SPRのKDを細胞結合EC50や機能的potencyと同一視していないか。

“Binding was measured by SPR” だけでは不十分である。測定配置と表面設計が違えば、同じ抗体でも異なる見かけのkineticsが得られる。sensorgram、残差、反復、対照まで見て初めて速度定数の妥当性を評価できる。

## 抗体×AIとの接続

SPR由来のkon、koff、KDを教師ラベルにするなら、数値だけでなく、抗体／抗原配列、分子フォーマット、assay orientation、固定化法、ligand density、温度、buffer、流速、濃度系列、fit model、reference処理、装置をprovenanceとして保持する。同じ「KD」でも、steady-state解析とkinetic解析、IgGとFab、単量体抗原と多量体抗原ではラベルの意味が異なる。

同一抗体の濃度系列や反復を別サンプルとして無作為分割すると、train/testリークになる。相互作用pairまたはclonotype単位でまとめ、可能なら別実験日・別表面で外部検証する。sensorgramそのものを時系列入力に使う場合も、モデルが結合機構ではなくbulk shiftや装置batchを学習していないかを、blank・reference・条件変更データで監査する必要がある。

## 重要用語（8語）

- **SPR**：金属表面の電子集団振動と光の共鳴を利用し、表面近傍の屈折率変化を検出する方法。
- **ligand**：SPR測定でセンサーチップ表面へ固定またはcaptureされる結合相手。
- **analyte**：流路から注入され、表面のligandとの相互作用を測られる分子。
- **sensorgram**：SPR応答を時間に対して示した曲線。
- **RU**：センサー表面近傍の屈折率変化を表す応答単位。親和性そのものではない。
- **association phase**：analyte注入中に、結合と解離の差し引きで応答が変化する区間。
- **dissociation phase**：bufferへ戻した後、主に複合体の解離を追う区間。
- **mass transport limitation**：溶液から表面へのanalyte供給が遅く、観測速度を制限する状態。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

抗体Aは抗体Bより最大RUが2倍だった。この結果だけで、AのKDがBより小さいと言えるか。

**模範回答：** 言えない。最大RUは結合量、分子量、表面活性、固定化密度などに依存し、KDそのものではない。同じ条件の濃度系列を測り、適切なモデルまたは平衡応答から親和性を評価する必要がある。

### 問2

ligand密度を下げ、流速を上げると推定konが大きくなった。元の測定では何が疑われるか。

**模範回答：** 表面へのanalyte供給が律速となるmass transport limitationが疑われる。元の遅い立ち上がりは分子固有の結合速度ではなく、輸送過程を含んでいた可能性がある。

## さらに調べる疑問2〜3問

1. 抗体をligandにする配置と抗原をligandにする配置で、avidityとRmaxはどう変わるか。
2. single-cycle kineticsとmulti-cycle kineticsは、再生による表面劣化をどう扱い分けるか。
3. SPRとBLIでは、物質移動、検出原理、スループットの違いがkinetics推定へどう影響するか。

## 自分の3行要約

- （1行目）
- （2行目）
- （3行目）

## 未解決の疑問

- （学習後に記入）

## 参考文献

1. Homola J. [Surface Plasmon Resonance Sensors for Detection of Chemical and Biological Species](https://doi.org/10.1021/cr068107d). *Chem Rev.* 2008;108:462–493.
2. Fägerstam LG, Frostell Å, Karlsson R, et al. [Detection of antigen-antibody interactions by surface plasmon resonance. Application to epitope mapping](https://doi.org/10.1002/jmr.300030507). *J Mol Recognit.* 1990;3:208–214.
3. Karlsson R, Michaelsson A, Mattsson L. [Kinetic analysis of monoclonal antibody-antigen interactions with a new biosensor based analytical system](https://doi.org/10.1016/0022-1759(91)90331-9). *J Immunol Methods.* 1991;145:229–240.
4. Cytiva. [Kinetics and affinity measurements with Biacore systems](https://cdn.cytivalifesciences.com/api/public/content/digi-33041-pdf). Application guide, accessed 2026-09-29.
5. Myszka DG. [Improving biosensor analysis](https://doi.org/10.1002/(SICI)1099-1352(199909/10)12:5%3C279::AID-JMR473%3E3.0.CO;2-3). *J Mol Recognit.* 1999;12:279–284.
6. O'Shannessy DJ, Brigham-Burke M, Peck K. [Immobilization chemistries suitable for use in the BIAcore surface plasmon resonance detector](https://doi.org/10.1016/0003-2697(92)90589-Y). *Anal Biochem.* 1992;205:132–136.
7. Myszka DG, Morton TA, Doyle ML, Chaiken IM. [Kinetic analysis of a protein antigen-antibody interaction limited by mass transport on an optical biosensor](https://doi.org/10.1016/S0301-4622(96)02230-2). *Biophys Chem.* 1997;64:127–137.
