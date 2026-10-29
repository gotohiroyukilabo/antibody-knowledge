---
day: 70
topic: 特異性engineering――negative selectionと交差反応性の抑制
created: 2026-10-29
status: unread
---

# Day 070：negative selectionで特異性を設計する

## 今日の問い

目的抗原への結合を保ちながら、よく似た抗原や細胞表面成分への不要な結合を、ライブラリ選択の段階でどう減らせるだろうか。

## 本文

### 1. 特異性は「結合する相手」と「結合しない相手」の組で決まる

抗体の特異性は、目的抗原に強く結合することだけでは定義できない。たとえば疾患関連タンパク質Aを認識しても、相同タンパク質B、非修飾型、別の立体構造状態、正常細胞にも結合すれば、診断の偽陽性や治療のoff-target作用につながる。ここで**交差反応性**は、ある抗体が目的抗原以外の定義可能な分子にも結合する性質である。一方、**polyreactivity／非特異的結合**は、多種類の無関係な分子、膜成分、核酸などへ広く結合する傾向を指す。原因も試験法も異なるため、同じ「specificity」という一語でまとめない。

設計の最初に、`結合すべき集合 P`と`避ける集合 N`を明示する。Nには最も近いparalog、species ortholog、翻訳後修飾のない抗原、標的陰性細胞、タグ・ビーズ・担体などを入れる。交差反応性が常に悪いわけではなく、複数の病原体variantやヒト・実験動物orthologを共に認識させたい場合は、それらをPに入れる[7,8]。したがって特異性engineeringとは、結合範囲を狭める作業ではなく、用途に合う境界を作る多目的最適化である。

### 2. positive selectionだけでは「紛らわしいbinder」が残る

positive selectionは、目的抗原へ結合したphage、yeast、mammalian cellなどを回収する操作である。しかし目的抗原とoff-targetが共有する表面を認識するcloneも一緒に濃縮される。さらに、固定化表面、biotin、蛍光色素、streptavidin、磁気beadへ結合するcloneが見かけ上の陽性になることもある。

Griffithsらは、胎児ヘモグロビンHbFに対する通常のphage panningでは、成人ヘモグロビンHbAにも結合する高親和性cloneが優勢になることを示した。各roundの前にlibraryを可溶性HbAとpreincubationすると、交差反応cloneがHbAに占有され、固定化HbFへ結合しにくくなった。その結果、親和性は低くてもHbFを識別するcloneが得られた[1]。この例は、目的抗原への結合だけを最大化すると、必要な選択性が探索空間の中で負けることを示す。

### 3. negative selectionは不要な表現型を先に除く

**negative selection**（counter-selection、subtractive selection、depletion）は、Nへ結合するvariantを回収対象から外す操作である。phage displayでは、libraryをoff-targetや標的陰性細胞へ先に接触させ、結合しなかった上清だけを目的抗原へ進める。可溶性off-targetを大量に加えて交差反応cloneを占有するcompetitive deselectionも使える。細胞panningでは、標的発現細胞と遺伝的背景が揃ったtarget-negative／knockout細胞をNにすると、共通表面分子へのbinderを減らしやすい。

yeast displayとFACSでは、目的抗原を色A、off-targetを色Bで同時に提示し、`A高・B低・display陽性`の細胞を選べる。Gaoらは、目的の構造状態へのpositive selectionと別状態へのnegative selectionを組み合わせるtwo-state selectionを示した[2]。McMahonらは、agonist結合型β2ARへの結合を残し、antagonist結合型、蛍光色素、検出抗体への結合を除くcounter-selectionで、活性型選択的nanobodyを取得した。round間で蛍光色素を交換し、色素binderの濃縮も防いでいる[3]。

ただしNを強くしすぎると、目的抗原とoff-targetの差を認識できる有用cloneまで失う。初期roundはlibrary多様性を保つため比較的緩くし、濃縮後にoff-target濃度を上げる、目的抗原濃度を下げる、解離選択を加えるなど段階的に圧力を強める。投入細胞・phage数がlibrary coverageを満たすこと、各roundでpositive/negative集団をsequencingすることも重要である。

### 4. 親和性向上と特異性維持は別の目的関数である

目的抗原への`KD`だけで順位を付けると、界面の共通部分への相互作用を強めて交差反応性も上げることがある。Liらはphospho-tau抗体をyeast displayで親和性成熟し、20倍超の親和性改善を得たが、高親和性variantの多くが非リン酸化peptideにも結合した。一方、親和性と元の高い特異性を両立するvariantも存在した[4]。したがって「高親和性化すれば必ず特異性が落ちる」のではなく、両方を測って選ぶ必要がある。

定義したoff-targetに対する選択性は、同じformat・条件で測った`KD`を用い、概念的に `selectivity ratio = KD(off-target) / KD(target)` と表せる。値が大きいほど目的抗原を優先する。ただしoff-targetが測定範囲内で結合しない場合は下限値にしかならない。さらに、定義済み抗原への選択性が高くても、未知の分子へのpolyreactivityは残り得る。可溶性膜／細胞質タンパク質、核酸、insulinなどのpolyspecificity reagentで別に評価する。臨床段階抗体の大規模な物性比較でも、非特異的相互作用を含む複数の指標を並行評価する重要性が示されている[6]。Kellyらは、CDR-H3中の特定の残基・motifが非特異性と関連し、それらを減らしたsynthetic libraryから多様なbinderを取得できることを示した[5]。

### 5. 濃縮の成功を「精製抗体の特異性」と取り違えない

display上の二色分離は候補抽出であり、最終証明ではない。蛍光強度は抗体表示量、抗原標識率、抗原価数、gate、濃度に依存する。候補を複数選び、可溶性Fab/IgGとして発現して、SPR/BLIの濃度系列、競合assay、標的陽性・陰性細胞、近縁抗原panelで直交検証する。治療抗体なら、結合だけでなく細胞機能と組織交差反応性も用途に応じて確認する。

抗原panelは「手元にあるもの」ではなく、生物学的リスクから決める。近縁paralog、目的epitopeを欠くmutant、非修飾体、別species、標的陰性組織、検出試薬を含める。標識を入れ替えて同じ結果になるか、IgG化でavidityにより弱いoff-target結合が顕在化しないかも見る。最終的な主張は「特異的である」ではなく、「試験した条件とpanelの範囲で、どの程度識別したか」と書く。

### 6. specificity landscapeを反復して更新する

実務では、変異library作製、P/N同時選択、配列解析、個別clone検証を1周で終えない。親和性は保つが交差反応するclone、特異性は高いが弱いcloneを比較し、両者を分ける残基を次のfocused libraryへ反映する。標的のどの部分がoff-targetと異なるかを構造やepitope mappingで確かめれば、差分表面へ相互作用を寄せる設計ができる。選択圧、抗原panel、formatを記録した反復ループによって初めて、配列変化と特異性変化を因果的に読める。

## 図または比較表

```text
変異library
    ↓  negative selection：off-target・陰性細胞・タグへのbinderを除く
未結合集団
    ↓  positive selection：目的抗原へのbinderを回収
target陽性 / off-target陰性の候補
    ↓  配列解析・focused library
精製Fab/IgGで抗原panel・細胞機能・polyreactivityを検証
```

| 選択法 | 残したい表現型 | 主な長所 | 主な落とし穴 |
|---|---|---|---|
| positive selectionのみ | target結合 | 単純で濃縮しやすい | 共通epitope・タグbinderも残る |
| 事前depletion | off-target非結合 | phage・細胞panningで実装しやすい | 強すぎると希少な有用cloneを失う |
| 可溶性競合deselection | target優先結合 | 近縁抗原間の識別に向く | 競合濃度と反応順序に依存 |
| 二色FACS | target高・off-target低 | 1細胞で両表現型を同時に選べる | 標識・avidity・gateの影響を受ける |
| two-state selection | 望む構造状態だけに結合 | conformation選択性を作れる | 状態の純度と安定性が必要 |

## 論文を読むためのポイント

1. **特異性の分母を特定する**：何に結合しないことを目標にしたのか。近縁抗原、陰性細胞、試薬controlが明記されているか。
2. **選択の順序と濃度を読む**：negativeとpositiveのどちらが先か、P/Nの濃度・価数・接触時間はどうか。
3. **標識artifactを疑う**：fluorophoreやtagを交換したか、bead-only、secondary-only controlがあるか。
4. **affinityとselectivityを分ける**：targetの`KD`だけでなくoff-targetの濃度系列または競合データがあるか。
5. **format差を確認する**：scFv/Fabで選び、IgGでavidityや非特異性を再評価したか。
6. **panelの妥当性を見る**：都合のよい少数抗原だけで「specific」と一般化していないか。
7. **機能で閉じる**：結合差が目的細胞での作用差、安全域、診断識別能へつながったか。

## 抗体×AIとの接続

特異性予測では、target binderだけを正例として集めても学習できない。各抗体について、targetと「よく似ているが結合してほしくない抗原」を対にしたhard negative、抗原濃度、assay、format、標識、検出限界を保存する必要がある。入力は抗体配列だけでなく抗原配列・構造とのpairで表し、出力も単一のbinding scoreではなくtarget affinity、off-target affinity、polyreactivityを分ける。

positive/negative sort由来のNGS頻度は大規模ラベルになるが、gate依存のenrichmentであって`KD`そのものではない。同じ親抗体の近縁variantをrandom splitするとリークが起きるため、親抗体・clonotype・抗原family単位で分割する。AIで候補を提案する場合も、`target結合を最大化し、off-target結合と不確実性を最小化する`多目的問題として扱い、Pareto front上の多様な候補を実験へ戻すのがよい。

## 重要用語（8語）

- **specificity engineering**：望む抗原集合への結合を保ち、避ける集合への結合を減らす抗体設計。
- **cross-reactivity**：一つの抗体が、目的抗原以外の定義可能な抗原にも結合する性質。
- **polyreactivity**：多数の無関係な分子へ広く結合する傾向。
- **negative selection**：off-targetへ結合するlibrary memberを除く選択工程。
- **counter-selection**：望ましくない表現型に反対向きの選択圧をかけること。negative selectionとほぼ同義で使われる。
- **competitive deselection**：可溶性off-targetで交差反応cloneを占有し、targetへの回収を妨げる方法。
- **hard negative**：targetと似ていてモデルや抗体が誤認しやすいが、結合してほしくない抗原例。
- **selectivity ratio**：同条件の`KD(off-target) / KD(target)`などで表す、二抗原間の識別度。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

目的抗原へのpositive selectionだけでは、なぜ高い特異性を保証できないのか。

**模範回答：** 目的抗原とoff-targetの共通部分を認識するcloneや、タグ・beadへ結合するcloneも回収されるからである。避ける抗原・試薬へのnegative selectionと、個別cloneの抗原panel試験が必要になる。

### 問2

二色FACSで`target高・off-target低`のcloneを選んだ後、なぜ精製IgGで再検証するのか。

**模範回答：** display上の蛍光は表示量、標識、gate、抗原価数に依存し、IgG化するとavidityや分子物性も変わる。精製IgGの濃度系列と細胞系で同じ識別が再現して初めて、用途に近い特異性を評価できる。

## さらに調べる疑問2〜3問

1. 近縁paralogが多数ある場合、どのoff-targetをnegative selectionへ入れると最も情報効率がよいか。
2. targetとoff-targetの同時FACSにおいて、抗原濃度比とgateはselectivity landscapeをどう変えるか。
3. 配列・構造AIは、実験で一度も測っていない未知off-targetへの交差反応をどこまで予測できるか。

## 自分の3行要約

- （1行目）
- （2行目）
- （3行目）

## 未解決の疑問

- （学習後に記入）

## 参考文献

1. Griffiths AD, et al. [Directing phage selections towards specific epitopes](https://doi.org/10.1093/protein/9.11.1043). *Protein Eng.* 1996;9:1041–1050.
2. Gao J, Sidhu SS, Wells JA. [Two-state selection of conformation-specific antibodies](https://doi.org/10.1073/pnas.0812952106). *Proc Natl Acad Sci U S A.* 2009;106:3071–3076.
3. McMahon C, et al. [Yeast surface display platform for rapid discovery of conformationally selective nanobodies](https://doi.org/10.1038/s41594-018-0028-6). *Nat Struct Mol Biol.* 2018;25:289–296.
4. Li D, et al. [Directed evolution of a picomolar-affinity, high-specificity antibody targeting phosphorylated tau](https://doi.org/10.1074/jbc.RA118.003557). *J Biol Chem.* 2018;293:12081–12094.
5. Kelly RL, et al. [Reduction of Nonspecificity Motifs in Synthetic Antibody Libraries](https://doi.org/10.1016/j.jmb.2017.11.008). *J Mol Biol.* 2018;430:119–130.
6. Jain T, et al. [Biophysical properties of the clinical-stage antibody landscape](https://doi.org/10.1073/pnas.1616408114). *Proc Natl Acad Sci U S A.* 2017;114:944–949.
7. Fagète S, et al. [Specificity tuning of antibody fragments to neutralize two human chemokines with a single agent](https://doi.org/10.4161/mabs.1.3.8527). *mAbs.* 2009;1:288–296.
8. Linciano S, et al. [Guidelines, Strategies, and Principles for the Directed Evolution of Cross-Reactive Antibodies Using Yeast Surface Display Technology](https://doi.org/10.1007/978-1-0716-2285-8_14). *Methods Mol Biol.* 2022;2491:251–262.
