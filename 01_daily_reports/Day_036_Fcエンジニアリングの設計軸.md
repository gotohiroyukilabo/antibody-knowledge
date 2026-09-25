---
day: 36
topic: Fc engineering――活性・安全性・半減期を変える設計
created: 2026-09-25
status: unread
---

# Day 036：Fcエンジニアリングの設計軸

## 今日の問い

抗原をつかむFabを変えずに、Fcのアミノ酸を置換すると、なぜ免疫細胞の動員、補体活性化、血中半減期を別々に調節できるのか。目的に合うFc設計と、その効果・副作用を検証する考え方を学ぼう。

## 本文

### 1. Fc engineeringは「出力先」を選ぶ設計である

IgGのFabは抗原を認識し、Fcは主にFcγ受容体（FcγR）、補体成分C1q、胎児性Fc受容体FcRnと相互作用する。**Fc engineering**とは、定常領域のアミノ酸置換などにより、これらの相互作用を目的に合わせて強めたり弱めたりすることだ。同じ抗原特異性を保ちながら、ADCC・ADCP・CDC・血中滞留を変えられる点が重要である[1]。

ただし「強いFc」が常に良いわけではない。腫瘍細胞を除去する抗体では免疫細胞の動員が有利になり得る一方、可溶性リガンドを中和するだけの抗体や、正常細胞上の受容体を遮断する抗体では、標的細胞の破壊や炎症を避けるためFcを静音化したい。最初に決めるべきなのは変異名ではなく、治療仮説上どの細胞を残し、どの細胞を除去し、どれだけ長く曝露するかである。

Fcの代表的な相互作用面は完全には同じでない。FcγRとC1qは主にlower hinge〜CH2領域、FcRnはCH2–CH3境界を認識する。この空間的な違いを利用して機能を調節できるが、変異はFcの構造、糖鎖、熱安定性、凝集性にも波及し得る。したがってFc設計は、一つの結合定数だけでなく分子全体の多目的最適化として扱う。

### 2. FcγR結合を高めてADCC・ADCPを増強する

標的細胞表面に結合したIgGが免疫細胞上の活性化型FcγRを架橋すると、NK細胞のADCCやマクロファージのADCPが起こる。Lazarらが報告したS239D/I332Eや、G236A/S239D/A330L/I332E（GASDALIE）などは、FcγRへの結合選択性を変え、in vitroの細胞傷害を高める代表例である[2]。ここで見るべきなのはFcγRIIIaへのaffinityだけでなく、活性化型受容体と抑制型FcγRIIbのどちらへどれだけ結合するかという**A:I比**である。

効果は抗体単独の定数では決まらない。抗原密度、epitopeの位置、FcγRの発現細胞、FcγRIIIa多型、effector-to-target比によって変わる。また、Fc配列改変とDay 35で扱った脱フコース化は別の設計層であり、併用すれば効果が加算・非加算になる可能性がある。SPRなどの受容体結合、reporter assay、一次NK細胞やマクロファージを用いたADCC・ADCPを段階的に対応づける必要がある。

増強は安全性の代償も生む。正常組織にも標的があればon-target/off-tumorの細胞除去が強まり、過剰な免疫複合体形成やサイトカイン放出につながり得る。ヒトと実験動物ではFcγRの種類、発現、IgGへの親和性が異なるため、動物で安全だったという事実だけでヒトのFc作用を保証できない[1]。

### 3. C1q結合とFc六量体化を高めてCDCを増強する

C1qは、抗原表面で近接した複数のFcへ多価結合すると古典経路を開始する。E345KやE430Gのような置換は、抗原結合後のFc–Fc相互作用とIgG六量体形成を促し、C1q結合とCDCを高める[3]。これは溶液中で無条件に集合させる設計ではなく、標的表面での配置を利用する設計である。

CDC増強も抗原密度、膜からのepitope距離、補体制御分子、血清条件に依存する。C1q結合だけを測って「細胞が死ぬ」と結論せず、C4/C3沈着、膜侵襲複合体、最終的な細胞死まで確認する。ADCC増強変異とCDC増強変異を組み合わせても、二つの経路が生体内で単純に足し算になるとは限らない。補体沈着がFcγRとの接触を妨げるなど、経路間の干渉も評価対象である。

### 4. 不要なエフェクター機能を静音化する

作用機序が中和や受容体遮断なら、FcγRとC1qへの結合を下げる方が安全な場合がある。古典的なLALA（L234A/L235A）にP329Gを加えた**LALA-PG**は、FcγRとC1qの相互作用を強く抑えつつ、FcRn相互作用とFc安定性を保つよう設計された例である[4]。N297AなどでFc糖鎖を除く方法も受容体結合を低下させるが、糖鎖はCH2構造を支えるため、配列変異型と同じ分子特性になるとは限らない。

「effector-silent」は絶対的な名称ではなく、検出限界と条件を伴う主張である。高濃度、受容体高発現、抗原の密集条件でも残存活性がないか、FcγRI、FcγRIIa/b、FcγRIIIa、C1qを個別に調べる。さらに細胞assayで意図した遮断活性が保たれ、意図しない細胞除去やサイトカイン放出が減ることを示す。

### 5. FcRnを調節して半減期を変える

IgGは細胞へ取り込まれた後、酸性endosome（およそpH 6）でFcRnに結合して分解を免れ、細胞表面の中性pH（約7.4）で離れて血中へ戻る。YTE（M252Y/S254T/T256E）は酸性条件のFcRn結合を高め、カニクイザルで元抗体より約4倍長い半減期を示した[5]。LS（M428L/N434S）もFcRn結合と半減期を高める代表的設計である[6]。

重要なのは「FcRnへ強く結合する」ではなく、**酸性で捕捉され、中性で放出されるpH依存性**である。pH 7.4でも強く結合すると、細胞表面で放出されず、かえってclearanceが増える場合がある[7]。pH 6.0と7.4の両方で結合を測り、細胞recycling、動物PK、最終的にはヒトPKをつなげて評価する。

半減期延長は投与間隔を延ばし得るが、効力や安全性を自動的に改善するわけではない。標的依存性消失（TMDD）、抗薬物抗体、非特異的結合、病態、抗原量もPKを変える。長い曝露は有害作用も長引かせ得るため、作用機序、用量、回復可能性まで含めて選ぶ。FcγR、C1q、FcRnの各軸を個別に測り、最後に同一分子として統合評価することがFc engineeringの基本である。

## 図または比較表

```text
治療目的
  ├─ 標的細胞を除去したい
  │    ├─ FcγR結合を調節 ─→ ADCC / ADCP
  │    └─ Fc六量体化・C1q ─→ CDC
  ├─ 中和・遮断だけを行いたい
  │    └─ FcγR・C1qを低下 ─→ effector-silent
  └─ 曝露時間を変えたい
       └─ pH依存的FcRn結合 ─→ recycling・半減期

すべての枝で：抗原結合、安定性、凝集、糖鎖、PK、安全性を再確認
```

| 設計軸 | 代表的な置換例 | 狙う変化 | 必須の確認 | 主なリスク |
|---|---|---|---|---|
| FcγR増強 | S239D/I332E、GASDALIE | ADCC・ADCP増強 | 各FcγR結合、一次細胞assay | 正常細胞除去、炎症 |
| CDC増強 | E345K、E430G | Fc六量体化、C1q・CDC増強 | 補体沈着、細胞死 | 非標的補体活性、経路干渉 |
| Fc静音化 | LALA-PG | FcγR・C1q作用の低減 | 全FcγR、C1q、残存細胞活性 | 静音化不足、構造変化 |
| 半減期延長 | YTE、LS | 酸性pHでFcRn結合増強 | pH 6/7.4結合、recycling、PK | 中性での放出不良、長引く毒性 |

## 論文を読むためのポイント

1. **治療仮説を先に読む**：標的細胞の除去、中和、補体活性化、長期曝露のどれが必要か。
2. **番号体系と変異セットを確認する**：EU numberingか、単一変異か組合せか、両重鎖に入るか。
3. **受容体を分けて見る**：FcγRIIIaだけでなく活性化型・抑制型FcγR、C1q、FcRnを個別に測っているか。
4. **結合から機能へ証拠をつなぐ**：SPRのaffinity差だけでなく、ADCC・ADCP・CDC・recyclingへ続くか。
5. **条件依存性を読む**：抗原密度、受容体多型、effector細胞、血清、pH、動物種が明記されているか。
6. **分子品質を確認する**：Fabの抗原結合、糖鎖、発現量、熱安定性、凝集、非特異的結合が保たれているか。

論文中の “enhanced” や “silenced” は比較対象とassay条件に依存する。野生型比のfold changeだけでなく、絶対値、濃度域、検出限界、ヒト作用機序に近い細胞系まで読む。

## 抗体×AIとの接続

Fc変異効果のAIモデルでは、入力を変異配列だけにしない。IgGサブクラス、Fc糖鎖、抗原密度、FcγRアレル、細胞種、pH、assay形式、動物種を条件として持たせる。同じS239D/I332Eでも、FcγRIIIa結合値とADCC値は別ラベルであり、異なる条件の数値を無批判に混ぜるとモデルは生物学ではなくassay差を学ぶ。

野生型と変異体のペアデータには、差分学習やmulti-task学習が向く。出力をFcγR群・C1q・FcRnの結合、ADCC・ADCP・CDC、pH依存性、Tm、凝集、PKに分ければ、目的関数間のtrade-offを可視化できる。ランダム分割では同一Fabや近縁Fcセットがtrain/testにまたがりやすいため、Fab系列・変異セット・assay campaign単位のgroup splitと、未見の標的または実験系による外部検証が必要である。AIの提案は、受容体結合だけでなく直交する機能・物性・安全性試験で検証して初めて設計候補になる。

## 重要用語（8語）

- **Fc engineering**：Fc配列などを改変し、受容体結合、補体、PKを目的に合わせて調節する技術。
- **A:I比**：活性化型FcγRと抑制型FcγRIIbへの相対的な結合傾向。
- **GASDALIE**：G236A/S239D/A330L/I332EからなるFcγR作用増強変異セット。
- **Fc六量体化**：抗原表面で6分子のIgG Fcが会合し、C1qの多価結合を支える過程。
- **effector-silent**：FcγR・C1qを介する細胞傷害や補体作用を極力抑えたFc設計。
- **LALA-PG**：L234A/L235A/P329GによりFcγR・C1q作用を強く下げる代表的変異セット。
- **YTE／LS**：酸性条件でのFcRn結合を高め、半減期延長に用いられる代表的Fc変異。
- **TMDD**：標的への結合・内在化・分解が薬物消失を左右するtarget-mediated drug disposition。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

可溶性サイトカインを中和するが、サイトカイン受容体陽性の正常細胞は除去したくない抗体では、どのFc方針が妥当か。また何を測って確認するか。

**模範回答：** FcγRとC1qを抑えるeffector-silent設計が候補になる。抗原中和能を保つことに加え、各FcγR・C1qへの結合、ADCC・ADCP・CDC、サイトカイン放出の残存を実使用濃度域で確認する。

### 問2

pH 6.0でFcRn結合が強くなったFc変異体について、それだけでは半減期延長を断定できない理由を説明せよ。

**模範回答：** 血中へ戻るにはpH 7.4でFcRnから放出される必要があり、中性でも結合が強いと再循環が阻害され得るためである。両pHの結合、細胞recycling、in vivo PKを順に確認する。

## さらに調べる疑問2〜3問

1. FcγRIIIaのV158/F158多型は、同じFc増強変異のADCC効果をどの程度変えるか。
2. ADCC増強変異と脱フコース化を併用したとき、効果と物性は相加的になるか。
3. YTEやLSによる半減期延長は、標的量が多くTMDDが強い抗体でも維持されるか。

## 自分の3行要約

- （1行目）
- （2行目）
- （3行目）

## 未解決の疑問

- （学習後に記入）

## 参考文献

1. Saunders KO. [Conceptual Approaches to Modulating Antibody Effector Functions and Circulation Half-Life](https://doi.org/10.3389/fimmu.2019.01296). *Front Immunol.* 2019;10:1296.
2. Lazar GA, et al. [Engineered antibody Fc variants with enhanced effector function](https://doi.org/10.1073/pnas.0508123103). *Proc Natl Acad Sci USA.* 2006;103:4005–4010.
3. de Jong RN, et al. [A Novel Platform for the Potentiation of Therapeutic Antibodies Based on Antigen-Dependent Formation of IgG Hexamers at the Cell Surface](https://doi.org/10.1371/journal.pbio.1002344). *PLoS Biol.* 2016;14:e1002344.
4. Schlothauer T, et al. [Novel human IgG1 and IgG4 Fc-engineered antibodies with completely abolished immune effector functions](https://doi.org/10.1093/protein/gzw040). *Protein Eng Des Sel.* 2016;29:457–466.
5. Dall'Acqua WF, Kiener PA, Wu H. [Properties of human IgG1s engineered for enhanced binding to the neonatal Fc receptor (FcRn)](https://doi.org/10.1074/jbc.M604292200). *J Biol Chem.* 2006;281:23514–23524.
6. Zalevsky J, et al. [Enhanced antibody half-life improves in vivo activity](https://doi.org/10.1038/nbt.1601). *Nat Biotechnol.* 2010;28:157–159.
7. Ramdani Y, et al. [Monoclonal Antibody Engineering and Design to Modulate FcRn Activities: A Comprehensive Review](https://doi.org/10.3390/ijms23179604). *Int J Mol Sci.* 2022;23:9604.
