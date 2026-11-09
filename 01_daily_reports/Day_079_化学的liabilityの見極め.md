---
day: 79
topic: 化学的liability――脱アミド化、酸化、異性化、切断
created: 2026-11-09
status: unread
---

# Day 079：化学的liabilityの見極め

## 今日の問い

抗体配列に脱アミド化や酸化の「危険モチーフ」が見つかったとき、直ちに候補を落とすべきだろうか。反応の種類、修飾部位、生成速度、機能への影響をどう結びつけ、実際の開発リスクを判断すればよいだろうか。

## 本文

### 1. 化学的liabilityは、共有結合が時間とともに変わる弱点である

**化学的liability**とは、製造・保存・投与後に抗体のアミノ酸残基やペプチド結合が反応しやすい性質である。代表例はAsn脱アミド化、Asp異性化、Met・Trp酸化、主鎖切断で、一次構造へ変化が残る。凝集や変性は主に会合・高次構造の変化だが、両者は連動し、酸化や脱アミド化が電荷や局所構造を変えて凝集を促すこともある[1,2]。

「修飾あり」と「医薬品として重大」は同義ではない。残基と場所、実条件での生成速度、抗原結合・Fc機能・PKへの影響、工程や製剤での制御可能性を組み合わせ、管理すべき**critical quality attribute（CQA）**かを判断する。

ここで、細胞内で酵素により作られる糖鎖やC末端Lys除去と、保存中にも進み得る非酵素反応を区別する。同じcharge variantとして見えても生成機序は異なる。また、修飾率が低くてもCDRの接触残基なら重要であり、高くても機能から遠い部位なら許容できる可能性がある。変化量だけでなく、品質との因果を示すことが要点である。

### 2. Asn脱アミド化は「配列モチーフ＋立体環境」で決まる

Asn側鎖は、しばしば五員環の**succinimide（コハク酸イミド）**を経て加水分解され、AspとisoAspを生じる。脱アミド化では質量が約+0.984 Da変わり、通常は負電荷が増すため、peptide mapping LC–MSやイオン交換で追跡できる。

NG、NS、NT、NNは警告モチーフだが、存在だけでは速度を決められない。37抗体の可変領域を調べた研究では、後続残基の大きさ、局所の柔軟性、二次構造がhotspot判別に重要だった[3]。露出した柔軟なCDRで起こればループ形状や抗原接触を変え得るが、遠い部位では同じ修飾率でも影響が小さい場合がある。pH、温度、時間にも依存するため、配列検索はscreenであって実測の代替ではない。

さらに、脱アミド化は試料調製中にも進む。長時間・高pHの酵素消化で生じた変化を製品由来と誤認しないよう、消化時間を短くし、未stress対照を同時処理する必要がある。+0.984 Daは同位体ピーク差に近いため、高分解能MSと保持時間、fragment ionを合わせて部位を定量する。

### 3. Asp異性化は質量差がほぼなく、主鎖のつながりを変える

Aspもsuccinimideを経てisoAspへ変わる。両者は同じ元素組成なのでintact massだけでは区別しにくいが、isoAspでは結合が側鎖側へ移り、主鎖にメチレン基一つ分の「寄り道」が入る。DG、DS、DTなどが典型的な警告配列だが例外もある。CDR-H2のDHKをもつ一抗体では、Asp55異性化が20%の試料で抗原結合活性が54%まで低下した一方、ラットPKに有意な悪化はなかった[4]。同じ修飾でも評価軸ごとに影響が違う。

### 4. 酸化は酸素だけでなく、光・金属・過酸化物にも左右される

抗体ではMetとTrpが代表的な酸化部位である。Met sulfoxideは+16 Da、Trpは複数の生成物を生じ、CDR酸化なら抗原との疎水・芳香族相互作用を失わせ得る。速度は溶媒露出度、周辺残基、溶存酸素、光、微量金属、原料・容器由来の過酸化物、温度に左右される[2]。

FcのMet252とMet428は重要な観察部位である。酸化variantを分離した研究では、両重鎖のMet252が酸化した分子でFcRn親和性低下、マウスでの消失加速と半減期短縮が見られたが、片側だけの酸化では未修飾体との有意差がなかった。Met428酸化の影響も同じではなかった[5]。「総酸化率」ではなく、部位別・分子別の状態を機能へ接続する必要がある。

対策も原因に合わせる。光酸化には遮光、金属触媒にはキレート剤、過酸化物には原料・surfactantの品質管理やscavengerを検討する。ただし添加剤そのものが別の分解物を生まないか、抗体活性や患者安全性へ影響しないかも確認し、実際の容器施栓系で検証する。

### 5. 切断は小さなfragmentを生み、結合価やFc機能を失わせる

切断には非酵素的加水分解、Asp周辺の反応、ヒンジのβ-elimination、残存proteaseなどがある。柔軟なヒンジからFab、Fc、Fab–Fcなどが生じると、二価結合、effector機能、PKが変わり得る。50°C・pH 6.5で一抗体を4日処理した研究では57%がfragment化し、主にヒンジ切断がSEC、SDS-PAGE、MSで確認された[6]。ただし、この強制劣化速度を冷蔵寿命へ直接外挿してはいけない。

切断点が同じでも、化学的加水分解と宿主細胞由来proteaseでは対策が異なる。還元・非還元CE-SDSとMSで鎖間disulfideの状態と切断点を確認し、培養・精製直後から増えているのか、保存中に増えるのかという時間情報で原因工程を絞る。

### 6. 評価は「予測→強制劣化→実時間保存→機能」の順で深める

まず配列からmotifや露出Met/Trpをflagし、構造モデルでSASA、柔軟性、周辺配置を見る。次にpH・熱・光・酸化剤による**forced degradation**で経路と分析法を確立する。peptide mapping LC–MS/MSは部位と率、intact/subunit MSは分子種、イオン交換は電荷variant、SEC・CE-SDSはfragment、SPR・細胞assay・FcRn/FcγR結合は機能影響を測る。

強制劣化は弱点探索には速いが、実製品と異なる生成物も作る。ICH Q5Cは、生物活性と物理化学・生化学・免疫化学的方法を組み合わせ、保存期間を長期・実時間・実条件データで支えるよう求める[1]。hotspot置換後は親和性と特異性を再測定する。製剤ではpH、温度、遮光、酸素、金属キレート剤などを検討し、工程・容器由来の原因も管理する。目標は修飾ゼロではなく、臨床使用期間を通じて意味のある品質と機能を保つことである。

分析法は互いの盲点を補う。例えばIEXの酸性peak増加だけでは、脱アミド化と糖鎖・末端修飾を区別できない。逆にpeptide mappingだけでは、その修飾をもつ完全分子の結合価や活性が分からない。peak分取、部位別MS、構造測定、機能assayを結びつけることで初めて、観測したvariantをCQA候補として説明できる。

## 図または比較表

| liability | 主な化学変化・手掛かり | 機能リスクの例 | 主な確認法 |
|---|---|---|---|
| Asn脱アミド化 | Asn→Asp/isoAsp、約+0.984 Da、酸性variant増加 | CDRなら親和性・potency低下 | peptide mapping LC–MS/MS、IEX、結合assay |
| Asp異性化 | Asp→succinimide→isoAsp、質量差ほぼなし | CDR loop形状・結合面の変化 | 特化したpeptide mapping、IEX、potency |
| Met/Trp酸化 | Met sulfoxideは+16 Da、複数のTrp酸化物 | CDR結合低下、FcRn/FcγR機能変化 | LC–MS/MS、intact/subunit MS、受容体結合 |
| 切断 | 主鎖・ヒンジ切断、低分子量種増加 | 二価性、Fc機能、PKの低下 | SEC、CE-SDS/SDS-PAGE、MS、機能assay |

```text
配列上のflag → 構造・露出度 → 条件別の生成速度 → 部位別修飾率 → 機能影響
      危険候補          反応しやすさ          実際の量          CQAか判断
```

## 論文を読むためのポイント

1. **試料履歴**：未処理、強制劣化、実時間保存のどれか。pH、温度、光、酸化剤、時間は現実的か。
2. **解析単位**：総variant量か、残基別修飾率か、同一分子に何個あるかまで分かるか。
3. **分析artifact**：消化・還元・試料調製中に脱アミド化、酸化、異性化を新たに作っていないか。
4. **場所と機能**：CDR、framework、Fc、ヒンジのどこか。抗原結合だけでなくFcRn、FcγR、細胞potencyも適切に測ったか。
5. **速度の外挿**：高温・高濃度酸化剤の結果から、実時間保存を無条件に予測していないか。
6. **対策の代償**：hotspot変異後に親和性、特異性、発現、安定性、新しいliabilityを再評価したか。

## 抗体×AIとの接続

化学liability予測は、配列中のmotif検出だけならrule-basedで始められるが、精度を上げるには残基ごとのSASA、柔軟性、二次構造、周辺電荷を加える必要がある。Sydowらは、37抗体のMSデータと構造特徴からAsn/Asp degradation hotspotを分類した[3]。別の最大60抗体の研究では、分子動力学由来のTrp溶媒露出時間が酸化と関連した[7]。

教師ラベルは「修飾あり/なし」ではなく、残基番号、反応種類、修飾率、pH、温度、時間、製剤、分析法、検出限界を保存する。強制劣化値と実時間値、総酸化率と部位別酸化率を混ぜない。同一抗体の条件違いや近縁variantをtrain/testへまたがせると系列を記憶するため、親抗体・clonotype単位で分割する。最終出力も単一のdevelopability scoreではなく、修飾速度、抗原結合、Fc機能、凝集などを別目的として示すのが望ましい。

## 重要用語（8語）

- **chemical liability**：時間と条件に依存して共有結合性の化学変化を起こしやすい弱点。
- **脱アミド化**：Asn側鎖のアミドがAsp/isoAspへ変わる反応。
- **異性化**：ここでは主にAspが同じ質量のisoAspへ変わり、主鎖結合様式が変化する反応。
- **succinimide**：Asn脱アミド化やAsp異性化で生じ得る環状中間体。
- **酸化**：Met、Trpなどが酸化生成物へ変わる反応。
- **fragmentation**：ペプチド鎖の切断による低分子量種の生成。
- **forced degradation**：強いstressで劣化経路を短時間に調べる試験。
- **CQA**：製品の安全性・有効性・品質を保証するため、適切な範囲に管理すべき属性。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

CDRにNG motifがある候補は、脱アミド化リスクだけを理由に直ちに除外すべきか。

**模範回答：** 直ちに除外はしない。NGは警告flagだが、立体構造、露出度、pH・温度別の修飾速度、抗原結合への影響を実測し、変異や製剤で制御できるかを含めて判断する。

### 問2

Met252酸化が15%検出され、抗原結合が不変なら、品質リスクはないと言えるか。

**模範回答：** 言えない。Met252はFcにあるため抗原結合試験では影響を見落とし得る。部位・分子別酸化状態を確認し、FcRn/FcγR結合、PK関連機能、実時間での増加を評価する。

## さらに調べる疑問2〜3問

1. 強制劣化条件で生じたvariantのうち、実時間保存でも同じ経路をたどるものをどう見分けるか。
2. isoAspを通常Aspから定量的に区別するMS/MS・酵素法には、どのような測定artifactがあるか。
3. hotspot除去変異と製剤対策の優先順位を、機能維持と製造コストを含む多目的最適化でどう決めるか。

## 自分の3行要約

- 化学的liabilityの重大性は、配列motifではなく、部位、速度、条件、機能影響の組合せで決まる。
- 脱アミド化・異性化・酸化・切断は、MSを中心とする部位解析と直交的な機能assayで結びつけて読む。
- 強制劣化は弱点探索、実時間保存は寿命の根拠であり、両者を同じラベルとして扱わない。

## 未解決の疑問

投与後に生体内で進む化学修飾を、製剤中の保存安定性試験とどこまで統合して臨床上のCQAへ結びつけられるのか。

## 参考文献

1. ICH. [Q5C: Stability Testing of Biotechnological/Biological Products](https://database.ich.org/sites/default/files/Q5C%20Guideline.pdf). 1995.
2. Gupta S, Jiskoot W, Schöneich C, Rathore AS. Oxidation and Deamidation of Monoclonal Antibody Products: Potential Impact on Stability, Biological Activity, and Efficacy. *J Pharm Sci.* 2022;111:903–918. [DOI: 10.1016/j.xphs.2021.11.024](https://doi.org/10.1016/j.xphs.2021.11.024)
3. Sydow JF, et al. Structure-based prediction of asparagine and aspartate degradation sites in antibody variable regions. *PLoS ONE.* 2014;9:e100736. [DOI: 10.1371/journal.pone.0100736](https://doi.org/10.1371/journal.pone.0100736)
4. Yi M, et al. Identification and characterization of an unexpected isomerization motif in CDRH2 that affects antibody activity. *mAbs.* 2023;15:2215364. [DOI: 10.1080/19420862.2023.2215364](https://doi.org/10.1080/19420862.2023.2215364)
5. Stracke J, et al. A novel approach to investigate the effect of methionine oxidation on pharmacokinetic properties of therapeutic antibodies. *mAbs.* 2014;6:1229–1242. [DOI: 10.4161/mabs.29601](https://doi.org/10.4161/mabs.29601)
6. Ravuluri S, Bansal R, Chhabra N, Rathore AS. Kinetics and characterization of non-enzymatic fragmentation of monoclonal antibody therapeutics. *Pharm Res.* 2018;35:142. [DOI: 10.1007/s11095-018-2415-4](https://doi.org/10.1007/s11095-018-2415-4)
7. Sharma VK, et al. In silico selection of therapeutic antibodies for development: viscosity, clearance, and chemical stability. *PNAS.* 2014;111:18601–18606. [DOI: 10.1073/pnas.1421779112](https://doi.org/10.1073/pnas.1421779112)
