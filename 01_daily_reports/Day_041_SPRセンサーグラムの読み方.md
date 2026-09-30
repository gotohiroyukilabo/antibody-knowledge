---
day: 41
topic: SPRセンサーグラム――kon・koff・KDを読み取る
created: 2026-09-30
status: unread
---

# Day 041：SPRセンサーグラムの読み方

## 今日の問い

SPRのsensorgramから、どのように `kon`、`koff`、`KD` を読み取り、きれいな曲線や小さなKDを過信せずに「この速度定数は信頼できる」と判断すればよいのだろうか。

## 本文

### 1. 曲線の高さではなく、濃度系列と時間変化を読む

SPRのsensorgramは、横軸が時間、縦軸が表面近傍の応答である。analyte注入中のassociation phaseでは結合と解離が同時に進み、注入を止めたdissociation phaseでは新しいanalyteの供給がなくなって複合体が減る。単純な1:1結合なら、応答 `R` の変化は次式で表せる[1,2]。

```text
dR/dt = kon × C × (Rmax − R) − koff × R
KD = koff / kon
```

`C` はanalyte濃度、`Rmax` は理論最大応答である。立ち上がりは `kon` だけでなく `C`、空いた結合部位、同時に起こる解離に依存するため、1本の初期傾斜だけで `kon` を決められない。1:1モデルの見かけのassociation速度は概ね `kobs = kon × C + koff` であり、複数濃度を重ねて濃度依存性を読む。

dissociationでは `C = 0` となり、理想的には `R(t) = R0 × exp(−koff × t)` と減衰する。解離半減期は `t1/2 = ln(2) / koff` なので、`koff` が10分の1なら半減期は10倍である。`KD` は速度定数の比であり、曲線の高さや最大RUではない。

### 2. kon・koff・KDは「目視で測る値」ではなくモデル推定値

reference surfaceとblank injectionを引いた後、複数濃度のassociationとdissociationを同時にモデルへ当てはめる。global fittingは、全濃度に共通する `kon` と `koff` を探し、1本ずつのfitより情報を統合する[2–4]。測定値とfit線の差である**残差**がゼロの周りへランダムに散り、測定ノイズと同程度かを確認する。association開始点やdissociation全体に波・傾きが残れば、系統的な説明不足である[5]。

良いfitは反応機構の証明ではない。1:1、二状態反応、heterogeneous ligandなど複数モデルが同じデータへ合う場合がある。実験設計を検討した研究でも、解析だけで機構を識別できず、注入時間などを変える対照が重要だった[2]。複雑なモデルで残差を小さくする前に、凝集、表面密度、価数、非特異的結合を点検する。

理想的な1:1反応では、各濃度のdissociation曲線を解離開始時の応答で正規化するとほぼ重なる。解離速度が濃度依存に見える、低濃度だけ別の形になる、濃度ごとの個別fitで速度定数が系統的に動く、といった所見は警告である。センサー表面の不均一性やrebindingだけでなく、希釈時の吸着、試料の凝集、濃度調製誤差も候補に含める。

### 3. 同じKDでもsensorgramの形は違う

抗体Aが `kon = 1 × 10^6 M⁻¹s⁻¹`、`koff = 1 × 10⁻³ s⁻¹`、抗体Bがそれぞれ `1 × 10^5` と `1 × 10⁻⁴` なら、どちらも `KD = 1 nM` である。しかしAは速く結合して速く外れ、Bは遅く結合して遅く外れる。解離半減期は約11.6分と116分で、親和性順位だけでは違いが消える。短い接触で標的を捕捉するには速い `kon`、占有を保つには遅い `koff` が有利になり得る。ただし細胞では抗原密度、内在化、二価結合が加わるため、SPRだけで薬効は断定できない。

### 4. kinetic KDとsteady-state KDを照合する

1:1平衡では `Req = Rmax × C / (KD + C)` となる。十分に平衡へ達した濃度系列からsteady-state KDを推定し、`koff / kon` のkinetic KDと概ね整合するか確認できる[6,7]。食い違うなら、平衡未到達、濃度誤差、heterogeneity、モデル不適合を疑う。

濃度系列は予想KDの上下を覆う必要がある。すべて `C ≫ KD` なら応答は飽和付近に集まり、KDの位置を定めにくい。すべて `C ≪ KD` なら曲線はほぼ直線となり、`Rmax` とKDを分離しにくい。さらに式へ入るのは名目上の総濃度ではなく結合可能なanalyte濃度なので、失活や凝集があれば `kon` とKDの推定もずれる。

非常に遅い `koff` は短い観測ではほぼ減衰せず、推定値が測定時間に支配される。高親和性抗体の多施設実験では、1時間のdissociationとglobal fitにより約 `4.5 × 10⁻⁵ s⁻¹` の `koff` を評価した[6]。逆に非常に速い反応では、注入切替や装置の時間分解能が限界になる。数値が表示されたことと、測定可能範囲内で識別できたことは別である。

### 5. 典型的な「読めないsensorgram」を見分ける

流速やligand密度で推定 `kon` が動くなら、表面への供給が律速となるmass transport limitationを疑う[5]。二相性のdissociationは、ligandの配向差、analyte不均一性、二価結合、rebindingなど複数の原因で生じる。IgGを高密度抗原表面へ流すと、片方のFabが外れても他方が残り、見かけの `koff` が遅くなるため、単価affinityではなくavidityを読んでしまう。

判断は、①補正前後の生データ、②濃度依存性、③反復、④fit線、⑤残差、⑥表面密度・流速・測定配置を変えた再現、の順で行う。小さいχ²や高いR²だけを合格印にしない。SPR値は「この試料、この表面、この温度・buffer、このモデル」の推定値である。多施設benchmarkでも、試薬品質、表面設計、参照処理、解析経験が結果の一致度を左右した[8]。

また、注入開始・終了直後だけに鋭い段差があれば、結合よりbufferの屈折率差や流路切替を疑う。baseline driftやreference channelにも同じ形がないかを確認し、除外した区間や濃度を記録する。都合の悪い点を黙って削るのではなく、除外基準と再解析結果を残すことが再現性につながる。

## 図または比較表

```text
応答 R
  │                 ┌──── 高濃度
  │             ┌───┘\
  │         ┌───┘     \     association      dissociation
  │     ┌───┘  中濃度  \        ↑                 ↑
  │  ┌──┘  低濃度       \   kon・C・Rmax・koff   主にkoff
  └──┴────────────────────────────── 時間
     注入開始                    注入終了

理想的な1:1結合では、濃度で立ち上がりが変わり、正規化した解離速度は共通する。
```

| 候補 | kon (M⁻¹s⁻¹) | koff (s⁻¹) | KD | 解離半減期 | sensorgramの特徴 |
|---|---:|---:|---:|---:|---|
| 抗体A | 1 × 10⁶ | 1 × 10⁻³ | 1 nM | 約11.6分 | 速く立ち上がり、比較的速く低下 |
| 抗体B | 1 × 10⁵ | 1 × 10⁻⁴ | 1 nM | 約116分 | ゆっくり立ち上がり、ゆっくり低下 |

## 論文を読むためのポイント

1. **濃度系列**：KDの上下を含む複数濃度か、ゼロ濃度・反復があるか。
2. **観測窓**：特に遅いkoffに対してdissociation時間が十分か。
3. **解析法**：kinetic fitかsteady-state fitか、global fitか、使用モデルと固定・共有パラメータが明記されているか。
4. **fit品質**：生sensorgram、fit線、残差が提示され、残差に系統的パターンがないか。
5. **artifact検証**：ligand密度、流速、測定配置を変えても速度定数が保たれるか。
6. **数値の報告**：単位、有効数字、反復間変動、標準誤差または信頼区間、測定不能値の扱いが示されているか。

“Data fitted a 1:1 model” は、分子が真に1段階で結合する証明ではない。「その条件で1:1モデルと矛盾しなかった」と読むのが安全である。

## 抗体×AIとの接続

`KD` だけをラベルにすると、速いon／速いoffと遅いon／遅いoffを同一視する。可能なら `log10(kon)`、`log10(koff)`、`log10(KD)` を別々に保持し、標準誤差、fit model、濃度範囲、観測時間、表面密度、抗体フォーマット、assay orientationも記録する。測定上限・下限を超えた値は任意の数へ置換せず、打ち切りデータとして残す。

raw sensorgramをAIへ入力する場合、曲線形状には結合機構だけでなく、buffer mismatch、注入切替、drift、装置、実験日が含まれる。同じ濃度系列や同じ表面の反復をtrain/testへ分散させず、相互作用pairと実験runを単位に分割する。予測性能だけでなく、残差パターンや条件変更に対する頑健性を検証し、モデルがartifactを使っていないか確認する。

## 重要用語（8語）

- **kon**：単位濃度あたりの結合開始速度を表すassociation rate constant（M⁻¹s⁻¹）。
- **koff**：形成済み複合体が単位時間あたりに解離する割合を表すdissociation rate constant（s⁻¹）。
- **KD**：`koff / kon` で表される平衡解離定数。小さいほど1:1条件下のaffinityが高い。
- **Rmax**：活性な表面結合部位が占有されたときに期待される最大応答。
- **global fitting**：複数濃度のsensorgramを共通パラメータで同時にfitする解析。
- **residual**：測定応答とモデル予測応答の差。モデル不適合の形を見つける手掛かり。
- **steady-state affinity**：各濃度の平衡応答と濃度の関係から推定するKD。
- **biphasic dissociation**：解離曲線に速い成分と遅い成分が見える状態。単一原因を即断できない。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

抗体AとBのKDはともに1 nMだが、AのkoffはBの10倍である。両者のkonと複合体の持続性はどう違うか。

**模範回答：** KDが同じでAのkoffが10倍なら、AのkonもBの10倍である。Aは速く結合する一方で速く外れ、Bの複合体はAより約10倍長く持続する。

### 問2

1:1モデルのfit線はsensorgramによく重なったが、残差がassociation前半では正、後半では負に偏った。このfitを採用してよいか。

**模範回答：** 数値上の重なりだけでは採用できない。系統的残差はモデルが曲線形状を説明し切れていない徴候なので、補正、mass transport、heterogeneity、avidityや試料品質を確認し、条件変更実験でモデルを検証する。

## さらに調べる疑問2〜3問

1. single-cycle kineticsとmulti-cycle kineticsでは、濃度系列のglobal fitと表面劣化の影響がどう異なるか。
2. kinetic KDとsteady-state KDが一致しないとき、どの対照実験から原因を切り分けるべきか。
3. 非常に遅いkoffをSPRで推定できる測定限界は、観測時間とbaseline driftでどう決まるか。

## 自分の3行要約

- （1行目）
- （2行目）
- （3行目）

## 未解決の疑問

- （学習後に記入）

## 参考文献

1. Karlsson R, Michaelsson A, Mattsson L. [Kinetic analysis of monoclonal antibody-antigen interactions with a new biosensor based analytical system](https://doi.org/10.1016/0022-1759(91)90331-9). *J Immunol Methods.* 1991;145:229–240.
2. Karlsson R, Fält A. [Experimental design for kinetic analysis of protein-protein interactions with surface plasmon resonance biosensors](https://doi.org/10.1016/S0022-1759(96)00195-0). *J Immunol Methods.* 1997;200:121–133.
3. Schuck P. [Reliable determination of binding affinity and kinetics using surface plasmon resonance biosensors](https://doi.org/10.1016/S0958-1669(97)80074-2). *Curr Opin Biotechnol.* 1997;8:498–502.
4. Myszka DG. [Improving biosensor analysis](https://doi.org/10.1002/(SICI)1099-1352(199909/10)12:5%3C279::AID-JMR473%3E3.0.CO;2-3). *J Mol Recognit.* 1999;12:279–284.
5. Schuck P, Zhao H. [The role of mass transport limitation and surface heterogeneity in the biophysical characterization of macromolecular binding processes by SPR biosensing](https://doi.org/10.1007/978-1-60761-670-2_2). *Methods Mol Biol.* 2010;627:15–54.
6. Katsamba PS, Navratilova I, Calderon-Cacia M, et al. [Kinetic analysis of a high-affinity antibody/antigen interaction performed by multiple Biacore users](https://doi.org/10.1016/j.ab.2006.01.034). *Anal Biochem.* 2006;352:208–221.
7. Cytiva. [Kinetics and affinity measurements with Biacore systems](https://cdn.cytivalifesciences.com/api/public/content/digi-33041-pdf). Application guide, accessed 2026-09-30.
8. Rich RL, Papalia GA, Flynn PJ, et al. [A global benchmark study using affinity-based biosensors](https://doi.org/10.1016/j.ab.2008.11.021). *Anal Biochem.* 2009;386:194–216.
