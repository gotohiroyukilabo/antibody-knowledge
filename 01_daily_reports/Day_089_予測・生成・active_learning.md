---
day: 89
topic: 予測と生成――affinity、paratope、developability、生成モデル、active learning
created: 2026-11-19
status: unread
---

# Day 089：抗体AIの予測・生成・active learning

## 今日の問い

抗体AIは、既存配列の性質を「予測する」ことと、新しい配列を「生成する」ことをどう使い分けるのか。また、計算上の高得点を、本当に結合し製造できる抗体へ変えるには何が必要か。

## 本文

### 1. 予測モデルは「入力から、定義されたラベルを推定する」

予測モデルは、抗体配列・抗原配列・複合体構造などを入力し、実験ラベルとの関係を学ぶ。重要なのは、**何を入力し、何を正解としたか**で答えられる問いが決まることである。抗体配列だけから「この残基はparatopeか」を推定することはできても、「どの抗原に、どの強さで結合するか」は抗原なしには原理的に特定できない。Parapredは抗原情報を使わず、抗体の超可変領域から接触残基の確率を出すモデルであり、標的特異的な結合予測とは別のtaskである[1]。

affinity予測では、抗体–抗原の組を入力し、`KD`、`log KD`、あるいは親配列に対する変化量`ΔΔG`を出力する。ここでもSPRのKD、displayのenrichment、結合／非結合の分類は交換可能なラベルではない。測定法、濃度、温度、抗原フォーマットが違えば、同じ配列でも値は変わる。モデル性能が高くても、実際には抗原やclonotype、assay batchを記憶しているだけかもしれない。

### 2. paratope・affinity・developabilityは粒度が違う

paratope予測は各残基に確率を付ける**残基単位**task、affinityは抗体–抗原ペアに値を付ける**ペア単位**taskである。developabilityはさらに、発現量、熱安定性、凝集、自己会合、粘度、非特異的結合、化学的liabilityなどの複数taskを含む。「developable／非developable」という1ラベルへ潰すと便利だが、どの試験で何が問題だったかが消える。

したがって候補選抜では、単一の総合点よりも各性質の予測値と不確実性を見る。affinityを改善する疎水性変異が、同時に非特異的結合や凝集を悪化させることもある。Jainらは臨床段階の抗体を12種類の物性assayで比較し、開発適性が単一試験では表せないことを示した[2]。AIでも、複数目的の間にある**Pareto front**、すなわち一方を改善すると他方が悪化し得る候補集合を扱う必要がある。

### 3. 生成モデルは「もっともらしい候補を提案する」

生成モデルは、学習した配列分布から新しい配列をサンプリングする。自己回帰モデルは前の残基から次の残基を順に生成し、infillingモデルはframeworkを固定してCDRなどの空欄を埋める。IgLMは5億5,800万本の抗体配列で学習し、種と鎖型を条件として全長生成や可変長領域のinfillingを行う[3]。この方法は、無作為変異より「抗体らしい」配列空間へ探索を偏らせられる。

しかし、生成確率が高いことは、ヒトらしさや自然配列との整合性を示すにすぎず、目的抗原への結合を保証しない。抗原を入力していない生成器は、とくに標的特異性を知りようがない。またin silicoの溶解性予測で選んだ配列を、同じ予測器で「良好」と評価すれば循環論になる。生成後には、重鎖–軽鎖の整合性、構造衝突、liability、配列新規性、予測不確実性など異なる根拠で絞り、最後は発現・結合・機能を実測する。

### 4. 生成器・予測器・獲得関数を分けて考える

設計系は三役に分けると読みやすい。**生成器**は候補を作り、**予測器（surrogate model）**は未測定候補の性質を近似し、**獲得関数（acquisition function）**は次に実験する候補を選ぶ。高い予測値だけを選ぶと既知領域へ集中するため、active learningでは「良さ」と「不確実性」を組み合わせ、活用（exploitation）と探索（exploration）を両立させる。

```text
初期ライブラリ → assay → 配列・ラベル → 予測器を学習
      ↑                                  ↓
   次ラウンド ← 合成可能性を確認 ← 獲得関数で候補選択
```

1ラウンドで終わらず、測定結果を戻してモデルを更新するのが**design–build–test–learn（DBTL）loop**である。初期データが狭いと、モデルは離れた配列で外挿を誤るため、各ラウンドでは高得点候補だけでなく、多様性を保つ候補、対照、重複測定も含める。Masonらは抗体ライブラリの実験データから特異性を学び、学習時に観測していない変異組合せを提案して実験検証した[4]。Makowskiらもaffinityとspecificityの同時最適化を実験的に示した[5]。成功の根拠は予測値ではなく、提案配列を作って測った結果である。

### 5. 評価の核心は、未知領域での前向き検証

ランダムsplitでは、ほぼ同じclonotypeや同じ抗原の近縁配列がtrainとtestへ分かれ、性能が過大評価される。未知clonotype、未知抗原、時間分割、外部施設のassayなど、利用場面に対応したsplitが必要である。分類ではAUROCだけでなく、不均衡に敏感なprecision–recall、確率のcalibration、上位候補のhit rateを見る。回帰では相関係数だけでなく、誤差、順位、測定再現性の上限を確認する。

さらに重要なのが**prospective validation**である。Hieらは一般protein language modelが提案した少数変異を実際に測り、7抗体中すべてで2ラウンド以内に改善候補を得たが、モデルには抗原情報が入っていなかった[6]。これは有用な候補生成戦略の証拠だが、任意の抗原に対するaffinityを正確に予測した証拠ではない。2026年の盲検前向きベンチマークAIntibodyでも、特定条件で優れた候補は得られた一方、task間の転移やライブラリ外設計には大きなばらつきが残った[7]。AIの役割は実験を消すことではなく、限られた実験枠を情報量の高い候補へ配分することである。

## 図または比較表

| task | 入力 | 出力 | 見落としやすい限界 | 必要な実験 |
|---|---|---|---|---|
| paratope予測 | 抗体配列／構造 | 残基ごとの接触確率 | 抗原なしでは標的固有の接触を決めにくい | 複合体構造、変異解析 |
| affinity予測 | 抗体＋抗原 | KD、ΔΔG、順位 | assay差、近縁配列リーク、外挿 | SPR/BLI、競合・機能assay |
| developability予測 | 配列／構造 | 複数物性 | 単一総合点が失敗理由を隠す | 発現、SEC、DSF、自己会合等 |
| 配列生成 | 親配列、条件、抗原など | 新規候補配列 | 尤度は結合・製造性の保証ではない | 合成、発現、結合、機能 |
| active learning | 既測定データ＋候補集合 | 次に測る候補 | 不確実性推定が外挿域で壊れ得る | 反復DBTL loop |

## 論文を読むためのポイント

1. **taskの定義**：paratope、結合分類、KD、enrichment、developabilityのどれを予測しているか。
2. **条件情報**：抗原、重鎖–軽鎖ペア、assay条件を入力しているか。入力のない情報を推定したと主張していないか。
3. **分割単位**：clonotype、抗原、系列、実験batchを跨いだリークを防いでいるか。
4. **生成と選抜**：何配列を生成し、どの予測器・閾値・多様性制約で、何配列まで絞ったか。
5. **実験検証**：後ろ向きtestだけか、未測定配列の前向き・盲検検証まで行ったか。失敗配列も分母に含むか。

論文の`top-k enrichment`は、「モデル上位k件に、実際のhitが無作為選択より何倍濃縮されたか」を意味する。創薬では全体相関が少し高いことより、限られた合成枠の上位にhitを集められることが重要な場合がある。

## 抗体×AIとの接続

Day 087のデータ設計、Day 088の表現学習、今日の予測・生成は一続きである。ラベルとprovenanceが曖昧なら、高性能なembeddingや生成器も誤った目的を最適化する。実務では、①測定法に対応した予測器、②抗体らしさと多様性を保つ生成器、③affinity・specificity・developabilityを同時に扱う獲得関数、④前向き実験を一つのloopとして設計する。最終評価単位は「モデルのスコア」ではなく、「一定の実験予算で、再現性のある良質候補を何件得たか」である。

## 重要用語（8語）

- **surrogate model**：高価な実験の代わりに、候補の性質を近似する予測モデル。
- **generative model**：学習分布から新しい配列候補を作るモデル。
- **infilling**：配列の前後文脈を保ちながら、指定区間を生成し直す方法。
- **active learning**：次に測ると有益な候補を反復的に選ぶ学習法。
- **acquisition function**：予測値、不確実性、多様性などから次の実験候補を順位付けする規則。
- **calibration**：予測確率と実際の発生頻度が一致する性質。
- **Pareto front**：複数目的で、他を悪化させずに一つを改善できない候補集合。
- **prospective validation**：モデル作成後に、未測定候補を新たに実験して性能を確かめる検証。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

抗体配列だけを入力する生成モデルが「自然らしい」配列を出したとき、それだけで目的抗原に結合すると言えないのはなぜか。

**模範回答：** 生成モデルは自然抗体の配列規則を学んでいても、目的抗原との相補性を入力されていない。結合は抗体–抗原ペアの性質なので、標的を含む評価と実験測定が必要である。

### 問2

active learningで予測スコアが最高の候補だけを毎回測ると、どのような問題が起こるか。

**模範回答：** 既知配列の近傍だけを活用し、不確実だが有望な領域を探索できない。多様性と不確実性を含む獲得関数を使い、測定結果で反復更新する必要がある。

## さらに調べる疑問2〜3問

1. affinity、非特異的結合、発現量を同時最適化するとき、Pareto候補から実験数をどう配分すべきか。
2. 未知抗原への汎化を評価するsplitと、同一抗原内のaffinity maturationを評価するsplitはどう設計し分けるか。
3. ensemble、Gaussian process、深層モデルの不確実性は、抗体配列の外挿域でどこまでcalibrationできるか。

## 自分の3行要約

- 予測taskは入力と実験ラベルで定義され、paratope・affinity・developabilityは異なる粒度を持つ。
- 生成モデルは候補を提案するが、抗体らしさや高い予測値だけでは標的結合と製造性を保証しない。
- 生成・予測・獲得・実験をDBTL loopにし、未知領域での前向き検証によって価値を判断する。

## 未解決の疑問

限られた実験予算の中で、未知抗原への探索、多目的developability、予測不確実性を同時に扱いながら、失敗例も学習資源に変える最適なDBTL loopはどう設計できるだろうか。

## 参考文献

1. Liberis E, et al. Parapred: antibody paratope prediction using convolutional and recurrent neural networks. *Bioinformatics.* 2018;34:2944–2950. [DOI: 10.1093/bioinformatics/bty305](https://doi.org/10.1093/bioinformatics/bty305)
2. Jain T, et al. Biophysical properties of the clinical-stage antibody landscape. *Proc Natl Acad Sci USA.* 2017;114:944–949. [DOI: 10.1073/pnas.1616408114](https://doi.org/10.1073/pnas.1616408114)
3. Shuai RW, Ruffolo JA, Gray JJ. IgLM: infilling language modeling for antibody sequence design. *Cell Systems.* 2023;14:979–989.e4. [DOI: 10.1016/j.cels.2023.10.001](https://doi.org/10.1016/j.cels.2023.10.001)
4. Mason DM, et al. Optimization of therapeutic antibodies by predicting antigen specificity from antibody sequence via deep learning. *Nat Biomed Eng.* 2021;5:600–612. [DOI: 10.1038/s41551-021-00699-9](https://doi.org/10.1038/s41551-021-00699-9)
5. Makowski EK, et al. Co-optimization of therapeutic antibody affinity and specificity using machine learning models that generalize to novel mutational space. *Nat Commun.* 2022;13:3788. [DOI: 10.1038/s41467-022-31457-3](https://doi.org/10.1038/s41467-022-31457-3)
6. Hie BL, et al. Efficient evolution of human antibodies from general protein language models. *Nat Biotechnol.* 2024;42:275–283. [DOI: 10.1038/s41587-023-01763-2](https://doi.org/10.1038/s41587-023-01763-2)
7. Erasmus MF, et al. A blinded, prospective benchmark of in silico antibody discovery anchored to experimental affinity and developability. *Nat Biotechnol.* 2026. [DOI: 10.1038/s41587-026-03238-6](https://doi.org/10.1038/s41587-026-03238-6)
