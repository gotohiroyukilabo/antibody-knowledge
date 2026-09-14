---
day: 25
topic: 体細胞超変異――抗体遺伝子へ変異を導入する仕組み
created: 2026-09-14
status: unread
---

# Day 025：AIDが生む体細胞超変異

## 今日の問い

B細胞は、ゲノムを壊す危険を抑えながら、なぜ抗体可変領域へ高頻度の変異を導入できるのか。また、抗体配列に見つかった生殖細胞系列との差を、どこまで「抗原による選択」の結果と解釈してよいのだろうか。

## 本文

### 1. 完成した抗体遺伝子を、抗原遭遇後にもう一度変える

Day 023〜024で扱ったV(D)J再構成と接合部多様性は、主に骨髄でB細胞が成熟する前に一次レパトアを作る仕組みだった。これに対し**体細胞超変異（somatic hypermutation; SHM）**は、再構成済みの重鎖・軽鎖可変領域へ、抗原刺激後に点変異を蓄積させる過程である。典型的には二次リンパ組織の胚中心で活性化B細胞が増殖するときに進み、子孫細胞は共通のV(D)J接合部を保ちながら、少しずつ異なる可変領域配列をもつ[1,2]。

「somatic」は生殖細胞系列へ受け継がれない体細胞DNAの変化、「hypermutation」は通常のゲノムより桁違いに変異が集中することを表す。標的は主に転写中の再構成済みIg可変領域であり、定常領域を丸ごと置き換えるクラススイッチとは結果が異なる。SHMが作るのは候補変異であって、高親和性そのものではない。結合を改善する変異、悪化させる変異、中立な変異が生じ、その後のB細胞選択が集団の組成を変える。変異の生成と選択を合わせた集団レベルの現象が親和性成熟であり、両者は区別して読む必要がある[1,3]。

### 2. 開始点はAIDによるCからUへの変換

SHMの開始酵素は**activation-induced cytidine deaminase（AID、遺伝子名AICDA）**である。AID欠損マウスでSHMとクラススイッチが強く障害されることが示され、両過程が共通の開始因子を使うことが明らかになった[2]。AIDは転写などで一時的に露出した一本鎖DNA上のデオキシシチジン（C）を脱アミノ化し、デオキシウリジン（U）へ変える[4,5]。DNA中のUは本来異常塩基なので、相補鎖のGとの間にU:Gミスマッチが生じる。

ここで重要なのは、AIDが最終的な20種類のアミノ酸置換を直接書き込むわけではないことである。AIDが作る一次損傷はC→Uだけであり、その損傷をDNA複製・塩基除去修復・ミスマッチ修復がどう処理するかによって、C/GだけでなくA/Tを含む多様な塩基置換へ広がる[3,6]。

### 3. 正確な修復を「あえて変異生成側へ」使う

U:Gミスマッチには三つの代表的な行き先がある。第一に、Uが除去されないまま複製されると、UはTのように読まれ、C:G塩基対の**transition**（C→Tまたは相補鎖上のG→A）として固定され得る。第二に、**UNG（uracil-DNA glycosylase）**がUを除くと、塩基を欠くAP siteができる。そこを低忠実度のtranslesion polymeraseが乗り越えると、C:Gでtransition以外の**transversion**も生じる。第三に、MSH2–MSH6がU:Gを認識して周辺DNAを短く除去し、**DNA polymerase η（Polη）**などが誤りやすいpatch synthesisを行うと、A/T塩基対にも変異が広がる[3,6]。

通常ならDNA修復は元配列を守る装置である。しかし胚中心B細胞では、AIDが作った損傷の一部が高忠実度に戻されず、誤りやすい複製・修復へ渡される。この「損傷の作成」と「変異原性修復」の組合せが、全4塩基に及ぶ置換スペクトルを生む。したがって論文でAID発現量だけを測っても、最終的な変異数や置換型を十分には説明できない。UNG、MSH2/MSH6、Polηなど下流因子と細胞状態も必要である。

### 4. 変異はランダムだが、一様ではない

SHMは特定の有利なアミノ酸を狙って起こるわけではない一方、各塩基が同じ確率で変異するわけでもない。AIDはWRC（W=A/T、R=A/G）のCを好み、反対鎖では対応するGYWとして観測される。Polη由来のA/T変異にもWA/TWなどの文脈依存性がある。さらに転写、可変領域内の位置、鎖、周辺数塩基が変異確率と置換先へ影響する[3,5,7]。このため、CDRに置換変異が多いという観測だけで、直ちに正の選択を証明することはできない。

例えば生殖細胞系列のコドン配置そのものがhotspotをCDRへ置きやすくしていれば、選択がなくても領域差が生じる。YaariらのS5Fモデルは、中心塩基と前後2塩基からなる5-merごとに変異しやすさと置換傾向を推定し、SHMの背景バイアスを定量化した[7]。replacement/silent比やCDR/frameworkの変異数を選択指標として使う論文では、こうした背景モデル、クローン性、同一変異の重複カウントをどう扱ったかを確認する。

### 5. 配列からSHMを数えるには「変異前」を推定する

実験では観測したV領域配列を、生殖細胞系列V・D・Jアレルへアラインし、不一致塩基をSHM候補として数える。たとえば300塩基の比較可能領域に9個の不一致があれば、単純な変異頻度は3%である。しかし、この値は抗体の親和性を直接表さない。9変異のうち結合を改善したのが1個だけかもしれず、複数変異の効果が非加算的なこともある。逆に低変異でも高親和性の抗体はあり得る。

推定した生殖細胞系列が誤っていれば、個人が生まれつき持つ未知アレルをSHMと誤認する。PCR・シーケンス誤り、primerで切り落とされた5′端、短いリード、低品質塩基も不一致数を増やす。同じクローンの子孫では祖先に一度起きた変異を共有するため、配列本数を独立イベント数として数えてはいけない。V/J割当て、参照データベースと版、解析領域、品質管理、clonotype定義、系統樹上での変異配置を確認することが重要である。

### 6. 有用な多様化とゲノム損傷は表裏一体

AIDの活性はIg遺伝子へ濃縮されるが、完全には限定されない。非Ig遺伝子へのoff-target脱アミノ化や誤ったDNA切断は、がん関連遺伝子の変異や染色体転座につながり、B細胞リンパ腫の形成に寄与し得る[8]。細胞はAIDの発現時期、核内滞在、分解、標的化、修復を多段階で制御する。SHMは「DNA修復の失敗」ではなく制御された多様化機構だが、その制御は絶対ではない。抗体の進化能力とゲノム安定性のトレードオフまで見ると、AIDを厳密に制御する理由が理解できる。

## 図または比較表

```text
転写中のIg可変領域で一本鎖DNAが露出
                  ↓ AID: C → U
               U:Gミスマッチ
        ┌─────────┼──────────┐
        ↓         ↓          ↓
   Uを残して複製   UNGでU除去   MSH2–MSH6で認識
        ↓         ↓ AP site  ↓ patch excision
   C/G transition 低忠実度合成  Polηなどで再合成
        ↓         ↓          ↓
       C/G変異（transition・transversion）＋ A/T変異
```

| 過程 | 主な時期・場所 | 配列に起こること | 観測結果の意味 |
|---|---|---|---|
| V(D)J再構成 | 抗原遭遇前、骨髄 | V/D/Jを連結し接合部を作る | cloneの基本配列を定める |
| 体細胞超変異 | 抗原刺激後、主に胚中心 | 再構成済みV領域へ点変異を作る | 選択に出される変異候補を供給する |
| 親和性成熟 | 胚中心反応の反復 | 変異したB細胞の増殖・淘汰 | 集団として親和性が上がる傾向を生む |
| クラススイッチ | 活性化B細胞 | 重鎖定常領域を組換える | 特異性を保ち、effector機能を変える |

## 論文を読むためのポイント

1. **SHMと親和性成熟を分ける**：変異数の増加は、結合親和性の改善を直接意味しない。親和性はSPR、BLIなどの実測で確かめる。
2. **生殖細胞系列推定を確認する**：参照アレル、V/J assignment、比較範囲、未知アレルへの対応がSHM数を左右する。
3. **mutation frequencyと配列本数を混同しない**：一つの祖先変異を多数のクローン子孫が共有する場合、独立した変異イベントは1回である。
4. **選択解析の背景モデルを見る**：CDRのreplacement enrichmentには、hotspot、コドン構成、位置依存性という生成バイアスが混ざる。
5. **実験誤差を確認する**：UMI、technical replicate、塩基品質、PCR酵素、consensus生成、低頻度variantの閾値を見る。

論文の “X% mutated from germline” は、指定した生殖細胞系列配列との塩基不一致率であることが多い。これは変異の機能効果、抗原特異性、親和性を単独では表さない。

## 抗体×AIとの接続

SHM系列は、変異効果予測や抗体最適化モデルにとって魅力的な自然実験である。しかし末梢レパトアに残った配列は、SHMの生成バイアスと抗原・構造・発現による選択を同時に受けた観測値である。頻出置換を「親和性を上げる変異」とそのまま学習させると、hotspotやクローン増殖を機能ラベルと誤認する。親和性を教師にするなら、同一assayで測った変異体と親配列のペア、抗原、重鎖・軽鎖の組合せ、実験条件を保持したデータが望ましい。

データ分割では、同一clonal lineageの祖先と子孫をtrain/testへ分けない。共有V(D)J接合部と共有SHMを手掛かりに、モデルが答えを記憶できるからである。系統単位で分割し、germline復元の不確実性や測定誤差も記録する。生成モデルでは、S5Fのような変異文脈モデルをnull modelとして使うと、「自然に起こりやすい配列」と「機能選択で濃縮された配列」を分けて評価しやすくなる。

## 重要用語（8語）

- **体細胞超変異（SHM）**：抗原刺激後のB細胞で、再構成済みIg可変領域へ高頻度の点変異を導入する過程。
- **AID（AICDA）**：一本鎖DNA上のCをUへ脱アミノ化し、SHMとクラススイッチを開始する酵素。
- **U:Gミスマッチ**：AIDが作るウラシルと相補鎖グアニンの不正な塩基対。
- **UNG**：DNA中のUを除去してAP siteを作るuracil-DNA glycosylase。
- **MSH2–MSH6**：U:Gなどの不一致を認識し、SHMでは変異原性patch repairにつなぐ複合体。
- **Polη**：SHMで特にA/T変異の形成へ大きく寄与する低忠実度DNA polymerase。
- **hotspot motif**：WRC/GYWなど、周辺塩基の影響でSHMが起こりやすい短い配列文脈。
- **germline inference**：観測抗体配列の変異前に相当する生殖細胞系列V(D)J配列・アレルを推定すること。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

AIDはCをUへ変えるだけなのに、SHMでA/T塩基対にも変異が生じるのはなぜか。

**模範回答：** AIDが作ったU:GミスマッチをMSH2–MSH6が認識し、周辺DNAを除去した後、Polηなどが誤りやすい再合成を行うためである。AIDの一次損傷を下流の変異原性修復が多様な置換へ広げる。

### 問2

ある抗体が生殖細胞系列から10%変異していれば、3%変異した抗体より高親和性だと結論できるか。

**模範回答：** 結論できない。変異率は塩基不一致の量であり、各変異の機能効果や抗原依存性を示さないため、同じ条件での結合測定が必要である。

## さらに調べる疑問2〜3問

1. AIDは転写中の多数の遺伝子のうち、どの分子機構でIg可変領域へ優先的に集められるのか。
2. UNG、MSH2/MSH6、Polηの欠損は、SHMの総数と置換スペクトルをそれぞれどう変えるか。
3. germline inferenceの誤りは、clonal lineage系統樹と正の選択解析へどの程度影響するか。

## 自分の3行要約

- （1行目）
- （2行目）
- （3行目）

## 未解決の疑問

- （学習後に記入）

## 参考文献

1. Janeway CA Jr, Travers P, Walport M, Shlomchik MJ. [The generation of diversity in immunoglobulins](https://www.ncbi.nlm.nih.gov/books/NBK27140/). *Immunobiology*. 5th ed. Garland Science; 2001.
2. Muramatsu M, et al. [Class switch recombination and hypermutation require activation-induced cytidine deaminase (AID), a potential RNA editing enzyme](https://doi.org/10.1016/S0092-8674(00)00078-7). *Cell*. 2000;102(5):553–563.
3. Di Noia JM, Neuberger MS. [Molecular mechanisms of antibody somatic hypermutation](https://doi.org/10.1146/annurev.biochem.76.061705.090740). *Annu Rev Biochem.* 2007;76:1–22.
4. Methot SP, Di Noia JM. [Molecular Mechanisms of Somatic Hypermutation and Class Switch Recombination](https://doi.org/10.1016/bs.ai.2016.11.002). *Adv Immunol.* 2017;133:37–87.
5. Dickerson SK, Market E, Besmer E, Papavasiliou FN. [AID Mediates Hypermutation by Deaminating Single Stranded DNA](https://doi.org/10.1084/jem.20030481). *J Exp Med.* 2003;197(10):1291–1296.
6. Neuberger MS, Rada C. [Somatic hypermutation: activation-induced deaminase for C/G followed by polymerase eta for A/T](https://doi.org/10.1084/jem.20062409). *J Exp Med.* 2007;204(1):7–10.
7. Yaari G, et al. [Models of somatic hypermutation targeting and substitution based on synonymous mutations from high-throughput immunoglobulin sequencing data](https://doi.org/10.3389/fimmu.2013.00358). *Front Immunol.* 2013;4:358.
8. Robbiani DF, Nussenzweig MC. [Chromosome translocation, B cell lymphoma, and activation-induced cytidine deaminase](https://doi.org/10.1146/annurev-pathol-020712-164004). *Annu Rev Pathol.* 2013;8:79–103.
