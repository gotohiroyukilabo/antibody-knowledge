---
day: 35
topic: Fc糖鎖――糖鎖構造がエフェクター機能へ与える影響
created: 2026-09-24
status: unread
---

# Day 035：Fc糖鎖が調節する抗体機能

## 今日の問い

抗原を認識するアミノ酸配列が同じでも、Fcに付く糖鎖が違うとADCC、CDC、体内動態はなぜ変わるのか。糖鎖構造を「一つの飾り」ではなく、分布をもつ機能調節因子として読めるようになろう。

## 本文

### 1. IgGは「同じ配列、複数の糖鎖状態」をもつ

ヒトIgGの各重鎖には、FcのCH2ドメインに保存された**Asn297（N297、EU numbering）**があり、通常ここへN結合型糖鎖が一つずつ付く。中心はGlcNAcとmannoseからなる二本鎖型coreで、core fucose、bisecting GlcNAc、galactose、sialic acidなどが追加される[1]。糖鎖を除くとFcのC'E loopが変形し、FcγRIIa、FcγRIIb、FcγRIIIaへの結合が大きく損なわれる。糖鎖は飾りではなく、受容体結合面を整える構造要素である[2]。

糖鎖はDNA配列だけでは決まらない。発現細胞の酵素、培地、pH、培養時間などにより、同じ配列から異なる**glycoform**が生じる。一つの製剤もG0F、G1F、G2F、高mannose型などの混合物であり、糖鎖は相対存在量の分布として測る。このmicroheterogeneityは正常だが、機能や安全性に影響する場合は管理すべきcritical quality attribute（CQA）となる[3]。

さらに、左右の重鎖が同じ糖鎖をもつとは限らない。例えばG0F/G1Fのような非対称な組合せもあり、遊離糖鎖の割合だけでは「一分子内で何と何が対になったか」が失われる。測定値がglycan、glycopeptide、intact IgGのどの階層から得られたかは、解釈できる範囲を決める。

### 2. core fucoseはFcγRIIIaとADCCを強く調節する

最も再現性の高い構造–機能関係は**afucosylation（脱フコース化）**である。N297糖鎖の根元にcore fucoseがないIgG1は、fucoseをもつIgG1よりFcγRIIIaへ強く結合し、NK細胞によるADCCを増強する。Shieldsらは、脱フコース化がFcγRI、C1q、FcRnへの結合をほぼ変えず、FcγRIIIへの結合とADCCを選択的に高めることを示した[4]。IgG側のcore fucoseの有無が、FcγRIIIa側のN162糖鎖との接触を変えるためである。

ただし、これはあらゆるFc機能の増強を意味しない。C1q依存のCDCを直接高める設計とは異なり、ADCC値も抗原密度、effector-to-target比、FcγRIIIa多型、使用細胞で変わる。糖鎖分析と受容体結合に加え、想定するeffector細胞で機能が再現されるかを見る。

結合試験では単量体FcγRIIIaへのaffinityと、細胞表面で多数の抗体・受容体が作るavidityも区別する。前者は分子機構を比較しやすいが、後者には受容体発現量や免疫複合体の配置が加わる。したがって、SPRなどの結合差が細胞傷害の差へ定量的にそのまま移るとは限らない。

### 3. galactoseは補体活性化の「並び方」に効く

末端galactoseが0、1、2個の代表的glycoformをG0、G1、G2と表す。末尾のFはcore fucoseを示す。IgG1のgalactosylationを高めると、標的表面でFc同士が会合して六量体を作りやすくなり、C1q結合、C4/C3沈着、CDCが増える[5,6]。単独Fcの性質だけでなく、複数IgGが作る高avidity配置を介した効果である。

ただし最終出力は、IgGサブクラス、抗原密度、epitopeの膜からの距離、抗体の配向、補体制御因子にも依存する。IgG2やIgG4へgalactoseを加えるだけでは、IgG1やIgG3と同等の補体固定能は得られなかった[5]。糖鎖効果はFc配列と抗原上の幾何学との相互作用として読む。

### 4. sialic acid、bisecting GlcNAc、高mannoseは同じ軸では語れない

Sialic acidはgalactose末端へ付く。Fc sialylationが高用量IVIGの抗炎症作用に寄与するというモデルは有力だが、再現しない実験系もある。疾患モデル、投与条件、Fab糖鎖の混入、精製法で結論が異なるため、「sialylation＝抗炎症」と一般化せず、単クローンIgGか多クローンIVIGか、Fc特異的な測定かを確認する[7]。

Bisecting GlcNAcとADCCの関連も、core fucoseとの共変動を切り分ける必要があり、脱フコース化ほど一貫しない[1]。高mannose型は加工途中のglycoformで、ヒトへ投与された治療用IgGではM5がcomplex型より速く消失することが示された[8]。糖鎖設計ではeffector functionだけでなくclearanceも考える。

重要なのは、fucose、galactose、sialic acid、mannoseを一本の「良い糖鎖スコア」に潰さないことである。各特徴は異なる分子相手と過程に効き、目的が腫瘍細胞の除去か、補体回避か、長い曝露かで望ましい分布は変わる。作用機序に不要なeffector functionを過度に高めれば、安全性上の不利益にもなり得る。

### 5. 糖鎖プロファイルと機能試験を対応づける

代表的な分析は、PNGase Fで切り出した糖鎖をHILIC-FLDやMSで定量する方法、酵素消化後のglycopeptideをLC-MSで測る方法、intact／subunit mass法である。遊離糖鎖解析は分布の定量に向き、glycopeptide解析は付加部位の情報を保つ。FDAの比較研究でも、HILIC-FLD、LC-MS、intact mass、NMRという直交法がlot間・製造者間差を整合的に捉えた[3]。

組成だけでは作用機序を証明できない。脱フコース率にはFcγRIIIa結合とADCC、galactosylationにはC1q・補体沈着・CDC、高mannose率にはPKを対応させる。さらに配列、凝集、抗原結合、製剤条件を揃える。平均値が同じでも左右二本の糖鎖の組合せや少量glycoformは異なり得るため、単一の要約値だけで機能を説明しない。

## 図または比較表

```text
各重鎖のN297
    │ N結合型糖鎖
    ▼
core（GlcNAc・mannose）
    ├─ core fucoseなし ─→ FcγRIIIa結合↑ ─→ NK細胞ADCC↑
    ├─ terminal galactose↑ → Fc六量体化↑ ─→ C1q・CDC↑
    ├─ terminal sialic acid → 免疫調節（文脈依存・議論あり）
    └─ high mannose↑ ─────→ clearance増加の可能性
```

| 糖鎖特徴 | 代表表記 | 主に確認する機能 | 読むときの注意 |
|---|---|---|---|
| core fucoseあり／なし | G0F 対 G0 | FcγRIIIa結合、ADCC | 他のFcγRやCDCへ同じ効果とは限らない |
| galactose 0／1／2個 | G0、G1、G2 | C1q、C4/C3沈着、CDC | サブクラスと抗原上の配置に依存 |
| sialic acid付加 | S1、S2など | 炎症制御、Fc受容体、補体 | Fc/Fab部位と実験系を区別する |
| high mannose | M5、M6など | clearance、PK | 少量でもlot比較と経時変化を見る |

## 論文を読むためのポイント

1. **部位を確認する**：N297 Fc糖鎖か、可変領域に新生したFab糖鎖か。
2. **単一構造か分布かを見る**：平均galactosylationだけでなく、各glycoformの相対量が示されているか。
3. **交絡を確認する**：afucosylationとbisecting GlcNAcなど、複数特徴が同時に変わっていないか。
4. **機序に合うassayを選ぶ**：FcγRIIIa結合だけでADCC、C1q結合だけでCDCを断定していないか。
5. **比較品を確認する**：同一Fab・同一Fc配列で、抗原結合、凝集、濃度、製剤条件が揃っているか。
6. **製造情報を見る**：宿主細胞、培養条件、lot、精製法、分析法が糖鎖差を説明しないか。

論文中の “afucosylated antibody” は完全にfucoseがゼロとは限らない。実際のafucosylated glycoform比率、定量法、受容体アレル、機能試験条件まで読んで初めて比較できる。

## 抗体×AIとの接続

糖鎖をAIへ入力するとき、抗体配列だけから決まる特徴として扱ってはいけない。宿主細胞、培地、培養日数、pH、精製工程、lot、分析法をprovenanceとして持ち、G0F、G1F、G2F、afucosylated、高mannoseなどの割合ベクトルとして表現する。出力も「ADCCが高い」という曖昧なラベルではなく、FcγRIIIaアレル、effector細胞、E:T比、抗原密度を伴う連続値にする。

同一クローンの複数lotをランダムにtrain/testへ分けると、モデルは配列や製造所を記憶し、未知抗体への性能を過大評価し得る。目的に応じて抗体系列、製造process、lotをgroup splitし、外部processで検証する。配列・糖鎖分布・process条件を統合したmultimodalモデルは有望だが、相関した糖鎖特徴から因果を主張するには、酵素的remodelingなどで一特徴だけを変えた実験が必要である。

## 重要用語（8語）

- **N297糖鎖**：IgG Fcの各重鎖Asn297に付く保存されたN結合型糖鎖。
- **glycoform**：同じタンパク質配列をもち、糖鎖構造だけが異なる分子種。
- **microheterogeneity**：一つの抗体試料に複数glycoformが共存する性質。
- **core fucose**：N型糖鎖の根元のGlcNAcへα1,6結合するfucose。
- **afucosylation**：core fucoseを欠く状態。主にFcγRIIIa結合とADCCを増強する。
- **galactosylation**：糖鎖末端へgalactoseが付く修飾。IgG1の補体活性化を高め得る。
- **high-mannose型**：mannoseを多く残す未成熟寄りのN型糖鎖。PKへ影響し得る。
- **CQA**：安全性・有効性・品質を保証するため範囲や分布を管理すべき品質特性。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

同一配列のIgG1で脱フコース率だけが高い候補は、どの結合と機能が特に増えると予測するか。また直接には予測できない機能を一つ挙げよ。

**模範回答：** FcγRIIIa結合とNK細胞ADCCの増強を予測する。C1q依存のCDCはcore fucoseの有無だけでは直接予測できず、galactosylationや抗原上のIgG配置も調べる必要がある。

### 問2

二つの製造lotでADCCが異なるとき、糖鎖が原因だと支持するために最低限どのデータを組み合わせるべきか。

**模範回答：** 各lotの部位特異的glycoform分布、特に脱フコース率を定量し、同条件のFcγRIIIa結合試験と細胞ADCC試験を対応づける。抗原結合、凝集、濃度などの非糖鎖要因が同等であることも確認する。

## さらに調べる疑問2〜3問

1. 脱フコース化抗体の高いADCCは、低抗原密度やFcγRIIIa低親和性アレルでも維持されるか。
2. 培養温度、pH、糖前駆体、培養期間は、どの酵素経路を介してFc糖鎖分布を変えるか。
3. 左右二本のFc糖鎖が非対称なIgGを、現在の分析法はどこまで定量できるか。

## 自分の3行要約

- （1行目）
- （2行目）
- （3行目）

## 未解決の疑問

- （学習後に記入）

## 参考文献

1. Wang TT. [IgG Fc Glycosylation in Human Immunity](https://doi.org/10.1007/82_2019_152). *Curr Top Microbiol Immunol.* 2019;423:63–75.
2. Subedi GP, Barb AW. [The Structural Role of Antibody N-Glycosylation in Receptor Interactions](https://doi.org/10.1016/j.str.2015.06.015). *Structure.* 2015;23:1573–1583.
3. U.S. Food and Drug Administration. [The Big Protein Project: Development and Assessment of Modern Protein Glycosylation Characterization Techniques](https://www.fda.gov/science-research/fda-science-forum/big-protein-project-development-and-assessment-modern-protein-glycosylation-characterization). 2023.
4. Shields RL, et al. [Lack of fucose on human IgG1 N-linked oligosaccharide improves binding to human FcγRIII and antibody-dependent cellular toxicity](https://doi.org/10.1074/jbc.M202069200). *J Biol Chem.* 2002;277:26733–26740.
5. Peschke B, et al. [Fc-Galactosylation of Human Immunoglobulin Gamma Isotypes Improves C1q Binding and Enhances Complement-Dependent Cytotoxicity](https://doi.org/10.3389/fimmu.2017.00646). *Front Immunol.* 2017;8:646.
6. de Jong SE, et al. [Fc Galactosylation Promotes Hexamerization of Human IgG1, Leading to Enhanced Classical Complement Activation](https://doi.org/10.4049/jimmunol.2100399). *J Immunol.* 2021;207:1545–1554.
7. Schwab I, Nimmerjahn F. [Role of sialylation in the anti-inflammatory activity of intravenous immunoglobulin—F(ab′)2 versus Fc sialylation](https://doi.org/10.1111/cei.12527). *Clin Exp Immunol.* 2014;178 Suppl 1:97–99.
8. Goetze AM, et al. [High-mannose glycans on the Fc region of therapeutic IgG antibodies increase serum clearance in humans](https://doi.org/10.1093/glycob/cwr027). *Glycobiology.* 2011;21:949–959.
