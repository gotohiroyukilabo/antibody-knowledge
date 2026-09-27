---
day: 38
topic: ELISA――簡便な結合測定と固相化によるバイアス
created: 2026-09-27
status: unread
---

# Day 038：ELISAと固相化バイアス

## 今日の問い

ELISAで抗体Aのシグナルが抗体Bより強かったとき、「Aのほうが抗原への親和性が高い」と結論してよいだろうか。プレート表面、検出反応、試料条件が観測値を作る過程を分解して考えよう。

## 本文

### 1. ELISAが測っているもの

ELISA（enzyme-linked immunosorbent assay）は、抗原または抗体の一方を固相へ留め、特異的結合を酵素反応による色や発光へ変換する免疫測定法である。典型的な比色法では、96 well plateへの固相化、blocking、試料または抗体の反応、洗浄、酵素標識試薬の反応、再洗浄、基質添加、吸光度（OD）の読み取り、という順に進む。1971年にEngvallとPerlmannが酵素標識を用いる定量法を報告して以来、放射性標識を使わず、多検体を比較的安価に扱える方法として広く使われてきた[1,2]。

最も重要なのは、装置が直接読んでいるのは結合分子数でも親和性でもなく、**反応後にwellへ残った酵素活性から生じたシグナル**だという点である。観測ODは、固相上に機能的な分子がどれだけ存在するか、抗体濃度、結合・洗浄時間、標識数、酵素反応時間、基質、readerの測定範囲に依存する。したがって「結合が見えた」は支持できても、条件を揃えずに分子固有の強さへ読み替えることはできない。

### 2. 四つの基本形式を目的から選ぶ

direct ELISAでは、固相抗原へ酵素標識一次抗体を直接結合させる。工程は短いが、抗体ごとの標識が必要で、標識が結合性を変える可能性もある。indirect ELISAでは非標識一次抗体を酵素標識二次抗体で検出する。増幅されて感度を得やすい反面、二次抗体の交差反応や、一次抗体のisotype差が信号差になり得る。

sandwich ELISAではcapture抗体が溶液中の抗原を捕まえ、別epitopeを認識するdetection抗体で挟む。複雑な試料から標的を選びやすいが、二抗体が同時に結合できるmatched pairが必要である。competitive ELISAでは試料中analyteが標識体などと限られた結合部位を競うため、多くの場合、analyteが多いほどシグナルは低下する。小分子や一つのepitopeしか使えない対象にも適する。形式が違えば「高シグナル」の意味も違うため、グラフを見る前に何が固相化され、何が標識され、何を競合させたかを図にする。

### 3. 固相化は中立な操作ではない

一般的なplateでは、タンパク質が疎水性相互作用などによりpolystyreneへ受動吸着する。このとき分子はランダムな向きで表面へ付き、結合部位がplate側を向けば抗体から見えない。表面との接触で部分変性し、天然状態のepitopeを失う一方、溶液中では隠れていた部位が露出することもある。吸着された抗原・抗体は、溶液中の同じ分子と同一とは限らない[3,4]。

これは抗体候補比較に二つの逆向きの誤差を作る。抗体Aがnative抗原へ強く結合しても、そのepitopeがplate側へ隠れれば弱く見える。抗体Bが変性で露出するlinear epitopeを認識すれば、ELISAでは強く、nativeな細胞表面抗原には結合しないかもしれない。また、coating濃度を増やすほど機能的抗原が比例して増えるとは限らない。分子の混み合い、配向、部分変性、脱離が変わるからである。Butlerらは吸着法と非吸着的固定法を比べ、固相化により抗体・抗原の機能とepitope accessibilityが大きく変わり得ることを実験的に示した[4]。

対策は「固相化をなくす」ことだけではない。低・中・高のcoating濃度を比較する、capture抗体を介してnative抗原を捕捉する、biotin–streptavidinやtagで向きを制御する、別lotのplateでも再現する、という方法がある。ただし化学修飾やtagも新たな影響を持つ。最終的には、細胞表面抗原ならflow cytometry、可溶性抗原とのsolution-phaseの結合ならSPRやBLIなど、目的に近い直交法で結論を確かめる。

### 4. 曲線を読むときは濃度・背景・飽和を見る

抗体濃度を横軸、ODを縦軸にしたtitration curveは、低濃度の背景域、中間の応答域、高濃度のplateauへ移ることが多い。比較に使えるのは、blankを上回り、検出系が飽和していない範囲である。単一点のODが同じでも曲線全体は異なり得るし、plateauが高いことと半最大点が低濃度側にあることは別の特徴である。反応時間、固相密度、二次抗体、洗浄条件が曲線を動かすため、ELISAのEC50をそのまま溶液中の平衡解離定数KDと呼んではならない。

抗原濃度を定量するsandwich ELISAでは、既知濃度standardを同じplate上で測り、未知試料をcalibration curveの検証済み範囲内へ入れる。血清や培養上清では、内在性抗体、結合タンパク質、脂質などが応答を変えるmatrix effectが起こる。試料を希釈したときに補正後濃度が保たれるdilutional parallelism、spike回収、blank、陰性・陽性対照、technical replicateを確認する。極端な高濃度ではsandwich形成が妨げられ、低い値へ見えるhook effectもある。ICH M10はligand-binding assayについて、selectivity、calibration range、accuracy・precision、dilution linearity、hook effectなどの検証を求めている[5]。

### 5. 抗体候補を公平に比べる実験設計

候補抗体の結合を比べるなら、同じ抗原調製物、plate lot、coating・blocking・洗浄条件、反応時間、温度、濃度系列を用い、抗体の純度・単量体率も確認する。二次抗体を使う場合は、候補のspecies、isotype、light chainに同程度に反応するかを調べる。無抗原well、無一次抗体well、irrelevant antibody、既知陽性抗体を置けば、plate吸着、二次抗体、基質、非特異的結合の寄与を切り分けられる。

結論は測定系の射程に合わせる。「この固相化抗原ELISAの条件でAはBより強い濃度依存シグナルを示した」は妥当だが、「AのKDが低い」「native抗原へ強い」「細胞機能が高い」は追加証拠なしには言えない。ELISAは候補を高速に絞る優れたscreening法であり、弱点は簡便さそのものではなく、観測シグナルの生成過程を省略して解釈することにある。

## 図または比較表

```text
溶液中の抗体–抗原結合
        ↓  固相化（量・向き・部分変性・epitope露出）
plate上でアクセス可能な結合
        ↓  検出（標識数・二次抗体・洗浄）
wellに残る酵素量
        ↓  発色（基質・時間・飽和）
測定OD

注意：OD差 ＝ 分子固有のaffinity差、とは限らない
```

| 形式 | 主に測る対象 | 長所 | 主な注意点 |
|---|---|---|---|
| Direct | 固相抗原への一次抗体結合 | 工程が短い | 抗体ごとの標識、増幅が小さい |
| Indirect | 抗体結合・抗体価 | 二次抗体で増幅、汎用性 | 二次抗体の交差反応、isotype依存 |
| Sandwich | 試料中の抗原濃度 | 複雑試料で選択性を得やすい | matched pair、steric hindrance、hook effect |
| Competitive | 抗原または抗体 | 小分子・単一epitopeにも対応 | 多くは濃度とシグナルが逆方向 |

## 論文を読むためのポイント

1. **assay形式を再構成する**：何を固相化し、何を標識し、シグナルが対象濃度と同方向か逆方向か。
2. **抗原の状態を見る**：全長か断片か、精製タンパク質か細胞由来か、tag・変性・多量体化はあるか。
3. **比較可能性を確認する**：抗体濃度、isotype、標識、二次抗体、反応時間、plate・試薬lotが揃っているか。
4. **曲線と対照を読む**：単一点だけでなく濃度系列、blank、陰性・陽性対照、replicate、飽和域が示されているか。
5. **主張の射程を限定する**：ELISAの結合をKD、native抗原結合、機能へ直接読み替えていないか。
6. **定量法の妥当性を見る**：standard curve、定量範囲、matrix、希釈直線性、回収率、hook effectを検証したか。

“Antibody A showed higher binding than antibody B by ELISA” は、「そのELISA条件で検出シグナルが高かった」という意味である。親和性差を主張するなら、固相密度や検出増幅から独立した速度論・平衡測定が必要になる。

## 抗体×AIとの接続

ELISA値をAIの教師ラベルに使うとき、ODやarea under the curveは純粋なaffinityではなく、抗原調製、coating濃度、plate、blocking、抗体isotype、二次抗体、反応時間を含む**assay由来の複合ラベル**である。異なるcampaignのODをそのまま結合すると、モデルは配列–結合関係ではなく実験batchを学ぶ可能性がある。raw OD、blank補正法、濃度系列、replicate、plate ID、抗原lot、検出試薬をprovenanceとして保存し、plate内対照で正規化する。

データ分割では同一抗体の濃度違い、近縁clone、同一plateのtechnical replicateをtrain/testへ分散させない。候補単位・clonotype単位・assay campaign単位でgroup splitし、可能なら未見lotやflow cytometry、SPR/BLIで外部検証する。モデル出力も「affinity」と過大命名せず、「このELISA条件での応答」または明確に定義したcurve指標とする。

## 重要用語（8語）

- **固相化（immobilization）**：抗原または抗体をplateなどの固体表面へ留める操作。
- **blocking**：未占有表面をタンパク質などで覆い、非特異的吸着を減らす操作。
- **epitope accessibility**：抗体からepitopeへ物理的に到達できる程度。
- **OD（optical density）**：発色産物による吸光度。ELISAの直接の読出し値。
- **titration curve**：試薬濃度を段階的に変えて得る応答曲線。
- **matrix effect**：試料中の標的以外の成分が測定応答を変える現象。
- **dilutional parallelism**：試料の希釈系列がstandardと整合した応答を示すこと。
- **hook effect**：analyteが極端に多いとsandwich形成が減り、見かけの信号が低下する現象。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

固相抗原ELISAで抗体AのODが抗体Bより高かった。AのKDがBより低いと直ちに結論できない理由を二つ挙げよ。

**模範回答：** 固相化による抗原の配向・部分変性で、AとBのepitope accessibilityが異なり得る。またODは標識・二次抗体・洗浄・発色の影響を受けるため、溶液中の平衡定数KDを直接表さない。

### 問2

sandwich ELISAで高濃度試料が予想外に低値を示した。まずどのような確認を行うべきか。

**模範回答：** 同じ試料を複数倍率で希釈し、補正後濃度が一致するかを確認する。希釈で測定値が回復するなら、定量範囲超過やhook effect、matrix effectを疑う。

## さらに調べる疑問2〜3問

1. 抗原を直接吸着する場合と、biotin–streptavidinで配向を制御する場合で、抗体順位はどの程度変わるか。
2. ELISAのEC50とSPR/BLIのKDが一致しないとき、固相密度、avidity、反応時間をどう切り分けるか。
3. plate間batch effectを抑えるため、どの対照と正規化法を事前に固定すべきか。

## 自分の3行要約

- （1行目）
- （2行目）
- （3行目）

## 未解決の疑問

- （学習後に記入）

## 参考文献

1. Engvall E, Perlmann P. [Enzyme-linked immunosorbent assay (ELISA). Quantitative assay of immunoglobulin G](https://doi.org/10.1016/0019-2791(71)90454-X). *Immunochemistry.* 1971;8:871–874.
2. Lequin RM. [Enzyme immunoassay (EIA)/enzyme-linked immunosorbent assay (ELISA)](https://doi.org/10.1373/clinchem.2005.051532). *Clin Chem.* 2005;51:2415–2418.
3. Butler JE. [Solid supports in enzyme-linked immunosorbent assay and other solid-phase immunoassays](https://doi.org/10.1006/meth.2000.1031). *Methods.* 2000;22:4–23.
4. Butler JE, Navarro P, Sun J. [Adsorption-induced antigenic changes and their significance in ELISA and immunological disorders](https://doi.org/10.3109/08820139709048914). *Immunol Invest.* 1997;26:39–54.
5. International Council for Harmonisation. [ICH guideline M10 on bioanalytical method validation and study sample analysis](https://www.ema.europa.eu/en/ich-m10-bioanalytical-method-validation-scientific-guideline). 2022.
6. Engvall E, Jonsson K, Perlmann P. [Enzyme-linked immunosorbent assay. II. Quantitative assay of protein antigen, immunoglobulin G, by means of enzyme-labelled antigen and antibody-coated tubes](https://doi.org/10.1016/0005-2795(71)90132-2). *Biochim Biophys Acta.* 1971;251:427–434.
