---
day: 83
topic: 構造柔軟性とinduced fit――静的構造だけでは見えないもの
created: 2026-11-13
status: unread
---

# Day 083：構造柔軟性とinduced fit

## 今日の問い

PDBの抗体–抗原複合体は一つの完成形を示すが、結合前の分子も同じ形だったのだろうか。抗体と抗原が動く分子であることを踏まえ、lock-and-key、conformational selection、induced fitをどう見分け、静的構造からどこまで結合機構を主張できるだろうか。

## 本文

### 1. 構造は「一枚の写真」、分子は「配座集団」

タンパク質は溶液中で一つの座標に固定されず、側鎖、CDRループ、VH–VLの向きが異なる複数の**配座（conformation）**を行き来する。その存在比と遷移速度を合わせたものが**配座集団（conformational ensemble）**であり、抗原側も同様に動く。

X線結晶構造やcryo-EM構造は、実験とモデル化を経た代表像である。高いB-factor、弱い電子密度、欠損残基は不均一性の手掛かりだが、B-factorには格子の乱れやモデル誤差も混ざる。座標が一つでも溶液中で剛直とは限らない。

### 2. 三つの認識モデルを時間順に考える

**lock-and-key**は結合前から相補的な形がほぼできている近似である。**conformational selection**では、遊離抗体がA、B、Cをあらかじめ往来し、抗原が結合可能なBを選ぶ。**induced fit**では、まず初期複合体を作り、その接触をきっかけにBからB*へ再配置する。

実際は`A ⇄ B; B + Ag ⇄ B·Ag → B*·Ag`のように両者が連続し得る。Fab 17/9では結合に伴いCDR-H3が再配置してpeptideを収めるpocketが生じた[1]。SPE7抗体では既存の複数isomerからligandが一つを利用し、その後さらにisomerizationすることが構造と速度論から示された[2]。

### 3. 遊離型と結合型の重ね合わせだけでは機構を確定できない

apo（遊離型）とholo（結合型）の差は変化の候補を示すが、二つの終点だけでは、holo様配座が元から存在したのか、接触後に生じたのかは分からない。結晶格子やconstructも差を作り得る。同一配列を優先し、CDR主鎖、側鎖、VH–VL orientation、抗原側変化を確認する。

NMRは溶液中の複数状態と交換時間尺度を検出できる。二つの抗体断片では、遊離結合面にミリ秒〜秒の配座交換が観測され、結合後にはCDR外の変化も見つかった[3]。速度論は二段階モデルを、HDX-MSは溶媒露出変化を調べられる。MDは候補配座を提示するがsamplingに依存し、未観測状態の不存在は証明できない。

### 4. 柔らかさは欠点でも万能な利点でもない

柔軟なparatopeは初期接触や交差反応性を助け得るが、結合時に自由度を失えばentropy penaltyを払う。親和性成熟で結合可能形を取りやすくする**preconfiguration**は、この損失を小さくできる。influenza HAを認識するCH65系列では、この機構が親和性向上の大部分を説明した[4]。

ただし成熟抗体が必ず硬くなるわけではない。大規模CDR-H3解析ではnaive抗体と成熟抗体の柔軟性差は小さく、変化は一様でなかった[5]。抗体と抗原の柔軟性を利用して自己抗原との識別を高めた例もある[6]。設計では平均構造だけでなく、配座の存在比と、結合可能形への移行が`kon`、`koff`、特異性、安定性へどう効くかを問う。

## 図または比較表

```text
lock-and-key:          A + Ag  ─────────→ A·Ag
conformational selection: A ⇄ B ⇄ C,  B + Ag → B·Ag
induced fit:           B + Ag → B·Ag ──→ B*·Ag
現実的な混合経路:      A ⇄ B,  B + Ag ⇄ B·Ag → B*·Ag
                         結合前に選ぶ          結合後に整える
```

| 観察 | 支持し得る解釈 | それだけでは決められないこと |
|---|---|---|
| apo/holoでCDR形状が違う | 結合に伴う再配置 | selectionかinduced fitか |
| apoに複数配座がある | conformational selectionの前提 | どの配座から実際に結合したか |
| 結合が二段階速度を示す | encounter後のisomerization | 段階ごとの正確な構造 |
| 結合後にNMR signalが安定化 | 配座交換の減少 | 一つの完全剛直状態になったか |
| MDでholo様配座をsampleする | pre-existing stateの候補 | 実在比率と実際の結合経路 |

## 論文を読むためのポイント

1. **比較対象を揃える**：apo/holoが同一配列、同一Fab/scFv、同等条件かを確認する。
2. **動く単位を特定する**：側鎖、CDR主鎖、VH–VL orientation、抗原、糖鎖のどこが変わるかを分ける。
3. **終点と経路を分ける**：構造差だけで「induced」と断定せず、NMRや速度論が時間順序を支えるかを見る。
4. **柔軟性指標の意味を読む**：B-factor、RMSF、HDX、NMR exchangeは同じ物理量ではなく、時間尺度も異なる。
5. **機能との接続を求める**：変異で配座集団が変わり、`kon`・`koff`・`KD`・交差反応性がどう変化したかを見る。

## 抗体×AIとの接続

単一のapo構造またはholo構造だけを教師にすると、「同じ配列が複数構造を取る」情報が落ちる。モデルが抗原結合形を正しく出しても、それは遊離状態での主要配座や結合経路を当てたことにはならない。学習データにはapo/holo、実験法、温度、pH、construct、結晶接触、局所品質を紐付け、同一抗体の構造をtrain/testへ分散させない。

有用な出力は単一座標だけでなく、CDR ensemble、配座確率、不確実性、抗原によるpopulation shift、変異後の`ΔΔG`や速度論である。ensemble生成モデルやMDを使う場合も、構造多様性が大きいだけで現実的とは限らない。NMR、HDX-MS、apo/holo対、変異体の`kon/koff`で校正し、「正しい平均構造」と「正しい動態」を別々に評価する必要がある。

## 重要用語（8語）

- **conformation（配座）**：結合を切らずに変化できる原子の三次元配置。
- **conformational ensemble**：溶液中で共存し相互変換する配座と存在比の集合。
- **lock-and-key**：結合前から形状相補性がほぼ整っている認識近似。
- **conformational selection**：既存配座の一つへligandが結合し、集団を偏らせる機構。
- **induced fit**：初期接触後に分子が再配置して最終複合体へ進む機構。
- **apo / holo**：それぞれ非結合状態／ligand結合状態の構造。
- **preconfiguration**：結合可能配座を遊離状態であらかじめ取りやすくすること。
- **RMSF**：軌跡中で各原子・残基が平均位置の周囲にどれだけ揺らぐかを表す量。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

同一抗体のapo構造とholo構造でCDR-H3が4 Åずれていた。この一組だけから「抗原がinduced fitを起こした」と結論してよいか。

**模範回答：** 結論できない。構造差は再配置を示すが、holo様の少数配座がapo集団に元から存在して選択された可能性があるため、溶液NMRや速度論など時間順序を示す証拠が必要である。

### 問2

親和性成熟でCDR-H3が硬くなれば、すべての抗体で親和性が上がると予測してよいか。

**模範回答：** 一般化できない。preconfigurationでentropy penaltyが減る例はあるが、柔軟性が初期捕捉や特異性を助ける例もあり、成熟に伴う変化は抗体系列ごとに異なる。

## さらに調べる疑問2〜3問

1. `kon`と`koff`のどちらがconformational selectionとinduced fitを最もよく識別できるか。
2. cryo-EMの3D variability、NMR、HDX-MS、MDで得るensembleはどこまで一致するか。
3. 配座確率まで予測する抗体AIを、どの実験データで校正すべきか。

## 自分の3行要約

- 抗体と抗原は単一構造ではなく、異なる時間尺度で動く配座集団として理解する。
- conformational selectionは結合前の既存配座を選び、induced fitは初期接触後に形を整えるが、両者は共存し得る。
- 静的apo/holo構造は終点の差を示すだけなので、NMR、速度論、HDX-MS、MDと機能測定を統合して経路を判断する。

## 未解決の疑問

治療抗体の設計で、交差反応性を広げる有益な柔軟性と、entropy penaltyや非特異的結合を生む過剰な柔軟性の境界を、少数の実験から定量できるだろうか。

## 参考文献

1. Rini JM, Schulze-Gahmen U, Wilson IA. Structural evidence for induced fit as a mechanism for antibody-antigen recognition. *Science.* 1992;255:959–965. [DOI: 10.1126/science.1546293](https://doi.org/10.1126/science.1546293)
2. James LC, Roversi P, Tawfik DS. Antibody multispecificity mediated by conformational diversity. *Science.* 2003;299:1362–1367. [DOI: 10.1126/science.1079731](https://doi.org/10.1126/science.1079731)
3. Addis PW, et al. Conformational heterogeneity in antibody-protein antigen recognition: implications for high affinity protein complex formation. *J Biol Chem.* 2014;289:7200–7210. [DOI: 10.1074/jbc.M113.492215](https://doi.org/10.1074/jbc.M113.492215)
4. Schmidt AG, et al. Preconfiguration of the antigen-binding site during affinity maturation of a broadly neutralizing influenza virus antibody. *Proc Natl Acad Sci USA.* 2013;110:264–269. [DOI: 10.1073/pnas.1218256109](https://doi.org/10.1073/pnas.1218256109)
5. Jeliazkov JR, et al. Repertoire analysis of antibody CDR-H3 loops suggests affinity maturation does not typically result in rigidification. *Front Immunol.* 2018;9:413. [DOI: 10.3389/fimmu.2018.00413](https://doi.org/10.3389/fimmu.2018.00413)
6. Burnett DL, et al. Conformational diversity facilitates antibody mutation trajectories and discrimination between foreign and self-antigens. *Proc Natl Acad Sci USA.* 2020;117:22341–22350. [DOI: 10.1073/pnas.2005102117](https://doi.org/10.1073/pnas.2005102117)
7. Stanfield RL, et al. Major antigen-induced domain rearrangements in an antibody. *Structure.* 1993;1:83–93. [DOI: 10.1016/0969-2126(93)90024-B](https://doi.org/10.1016/0969-2126(93)90024-B)
