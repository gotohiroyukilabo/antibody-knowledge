---
day: 18
topic: CDRとframework――抗原結合部位を支える構造
created: 2026-09-07
status: unread
---

# Day 018：CDRとframework

## 今日の問い

抗体の可変ドメインをCDRとframeworkに分けると、抗原結合を担う「先端」と、それを支える「足場」はどのように協働するのか。なぜCDR配列だけを見ても結合性を完全には説明できないのか。

## 本文

### 1. 1本の可変ドメインはCDRとframeworkが交互に並ぶ

重鎖可変ドメインVHと軽鎖可変ドメインVLは、いずれも`FR1–CDR1–FR2–CDR2–FR3–CDR3–FR4`という順序で記述される。CDR（complementarity-determining region）は各鎖3本、VHとVLを合わせて6本ある。これらのループが可変ドメインの一端に集まり、抗原に向き合う面の中心をつくる。framework region（FR）はその間を埋める4領域で、免疫グロブリンフォールドのβシート骨格を構成する。つまり、CDRとFRは別々のドメインではなく、同じVドメイン内で交互につながる配列区分である。[Chiu et al., 2019](https://doi.org/10.3390/antib8040055)

「CDR＝結合、FR＝無関係な土台」という二分法は便利だが不完全である。多くの抗原接触残基はCDRにある一方、CDR外から抗原に直接触れる残基もある。またFRは、CDRループの根元を固定し、VHとVLの相対的な向きを定め、結合面の形と運動性へ間接的に影響する。したがってパラトープは、6本のCDRを中心としつつ、必要に応じて周辺FR残基まで含む三次元的な表面として捉えるのがよい。[Sela-Culang et al., 2013](https://doi.org/10.3389/fimmu.2013.00302)

### 2. CDRは「高可変領域」から見いだされたが、境界は一つではない

KabatのCDRは、多数の抗体配列を並べたときに変異が集中する区間を基礎に定義された。その後Chothiaらは立体構造を調べ、ループの構造的境界と挿入位置を考慮した定義を提案した。IMGTは免疫グロブリンとT細胞受容体を共通の座標で比較できるよう、保存残基とギャップを用いた独自の番号付けを整備している。たとえばIMGTではCDR1を27–38、CDR2を56–65、組換え後のCDR3を105–117番として扱う。[IMGT Scientific chart](https://www.imgt.org/IMGTScientificChart/Nomenclature/IMGT-FRCDRdefinition.html)

このため、論文に「HCDR1の変異」と書かれていても、番号付けがKabat、Chothia、IMGTのどれかで残基範囲がずれることがある。Hはheavy chain、Lはlight chainを表し、HCDR2とL-CDR2のように表記法も一定しない。配列、変異位置、CDR長を論文間で比較するときは、採用した番号付け方式とCDR定義を必ず確認する。単純な配列の通し番号も、シグナルペプチドを含むかどうかでずれるため注意が必要である。[Abhinandan and Martin, 2008](https://doi.org/10.1016/j.molimm.2008.05.022)

### 3. frameworkはCDRの形を支える構造部品である

FRの主な役割はVドメインのβサンドイッチを保つことである。内部の疎水性残基は折りたたみと熱安定性に、保存されたシステインはドメイン内ジスルフィド結合に、VH–VL界面の残基は二つのドメインの会合角度に寄与する。FRを大きく変えると、発現量や凝集性が変わるだけでなく、CDRの位置関係がずれてaffinityや特異性まで変わり得る。

実際、Vドメイン全体の飽和変異解析では、埋もれたFR位置には変異を許容しにくいものがある一方、抗原から離れたFR変異がVH–VL間の運動性を変えて結合を改善する例も示された。これは「抗原に直接触れない残基は結合に無関係」ではないことを意味する。ただし、一つの抗体で有効なFR変異を別の抗体へそのまま移せるとは限らない。効果はCDR配列、VH/VLの組合せ、抗原との結合様式という文脈に依存する。[Koenig et al., 2017](https://doi.org/10.1073/pnas.1613231114)

### 4. 5本のCDRには反復する構造があるが、配列だけでは決まらない

古典的な構造解析では、HCDR3を除く5本のCDRの主鎖構造は無数ではなく、限られた「canonical structure」に分類できることが示された。どの形を採りやすいかはループ長だけでなく、CDR内および隣接FRの特定残基によるパッキングや水素結合に左右される。[Chothia and Lesk, 1987](https://doi.org/10.1016/0022-2836(87)90412-8) その後、300超の非冗長抗体構造を用いた再クラスタリングにより、非H3ループにも同じ長さで複数の配座群があることや、配列から割り当てにくい群があることが整理された。[North et al., 2011](https://doi.org/10.1016/j.jmb.2010.10.030)

この原理が抗体構造予測を比較的扱いやすくする。保存されたFRには既知構造のテンプレートを当て、非H3 CDRには長さと配列に合うループ構造を探せるからである。一方HCDR3は長さと配列の多様性が特に大きく、抗原結合面の中央に位置しやすいため、予測の難所となる。HCDR3の由来と難しさはDay 19で詳しく扱う。

### 5. CDR graftingは「ループだけ移せば終わり」ではない

CDR graftingは、非ヒト抗体のCDRをヒト抗体由来FRへ移植して、抗原結合をなるべく保ちながらヒト化する方法である。1980年代の実験は、超可変ループを移すことで抗原結合活性を移植できることを示した。[Riechmann et al., 1988](https://doi.org/10.1038/332323a0) しかし、移植先FRがCDRの形やVH–VL配向を十分に再現しなければaffinityが低下する。このとき、CDRを支えるドナー側FR残基を戻すback mutationが検討される。

設計では、まずドナーとアクセプターの番号付けをそろえ、CDRに直接接するFR、VH–VL界面、埋もれたコア、抗原接触の可能性があるFRを構造上で確認する。そのうえで、親抗体、単純CDR graft、back mutation候補を同じformatで発現させ、発現量、単分散性、熱安定性、`KD`・`kon`・`koff`、必要なら細胞機能を比較する。結合だけ回復しても不安定なら、良い設計とは言えない。

### 6. 読解では「領域ラベル」から実際の残基と証拠へ降りる

論文で「CDR変異によりaffinityが向上した」とあれば、どの鎖の何番残基か、番号付け方式、変異が抗原へ直接接触するか、構造は実測かモデルかを確認する。逆にFR変異なら、安定化、VH–VL配向、CDRの配座、直接接触のどれが想定機構かを分ける。結晶構造の距離だけで因果を確定せず、復帰変異、速度論、発現・安定性測定が仮説を支えるかを見る。

要するにCDRは抗原認識の主役、FRは舞台装置というより、主役の姿勢と動きを決める共演者である。配列上の境界は解析に必要だが、機能は境界をまたぐ。抗体工学では、CDR配列、FRの構造文脈、VH/VLペア、assayを一つの系として評価する必要がある。

## 図または比較表

```text
配列（VHまたはVL）
N末端  FR1 ─ CDR1 ─ FR2 ─ CDR2 ─ FR3 ─ CDR3 ─ FR4  C末端
          \_______ 免疫グロブリン型βシート骨格 _______/
                    ↑ 3本のループが一端へ突出

VHのCDR 3本 ＋ VLのCDR 3本
              ↓ 空間的に集合
        パラトープ（抗原結合面）
              ↑
  FRがループの根元・VH/VL配向・安定性を支える
```

| 観点 | CDR | framework（FR） |
|---|---|---|
| 各Vドメイン内の数 | 3領域 | 4領域 |
| 主な構造 | βシート間をつなぐ表面ループ | 保存性の高いβシート骨格 |
| 主な役割 | 抗原表面との形・化学的相補性 | 折りたたみ、CDR支持、VH–VL配向 |
| 抗原への接触 | 多くの接触残基が存在 | 一部は直接接触し得る |
| 工学上の注意 | 境界が番号付け方式で異なる | 置換で結合性とdevelopabilityの両方が変わり得る |

## 論文を読むためのポイント

1. CDR/FRの区切りがKabat、Chothia、IMGTなどのどの方式か確認する。
2. 変異を「HCDR3」のような領域名だけでなく、元残基・変異後残基・番号で特定する。
3. 抗原接触の主張が複合体の実測構造、計算モデル、変異実験のどれに基づくか分ける。
4. FR変異では結合値だけでなく、発現、熱安定性、凝集、VH–VL配向も確認する。
5. CDR grafting前後でVH/VL、抗体format、assay条件が対応しているかを見る。

## 抗体×AIとの接続

CDRだけを入力するモデルは計算量を減らせるが、FR由来の構造文脈、VH–VL配向、直接接触を失う。目的が抗原結合なら、ペアのVH/VL全長と抗原情報を使い、CDRマスクを追加特徴量として与える設計が自然である。CDR境界の方式がデータごとに違えば、同じ残基がCDRとFRに別ラベルされるため、前処理で番号付けを統一しなければならない。

学習・評価の分割でも、同じFRに異なるCDRを移植した系列や、同じCDRを近縁FRへ載せた系列を無作為に分けると、モデルが共有配列を記憶しやすい。scaffold、clonotype、抗原を目的に応じてグループ化する必要がある。またattentionや変異スコアがCDRへ集中しても、それだけで接触や因果を証明したことにはならない。構造上の距離、実験的な変異効果、独立抗原で検証する。

## 重要用語5〜8語

- **CDR**：可変ドメイン内の相補性決定領域。各鎖3本あり、抗原結合面の中心をつくる。
- **framework region（FR）**：CDRを挟む4領域。Vドメインの骨格、安定性、ループ配置を支える。
- **パラトープ**：抗体側の抗原結合表面。CDR中心だがFR残基を含むこともある。
- **番号付け方式**：挿入・欠失を含む抗体残基を対応づける規則。Kabat、Chothia、IMGTなどがある。
- **canonical structure**：主に非H3 CDRで反復して観察されるループ主鎖配座の型。
- **VH–VL配向**：重鎖・軽鎖可変ドメインの相対的な角度と位置関係。
- **CDR grafting**：ある抗体のCDRを別のFRへ移植する抗体工学手法。
- **back mutation**：機能回復のため、移植後のFR残基をドナー抗体型へ戻す変異。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

CDR配列が同じなら、異なるframework上でも同じaffinityになるとは限らないのはなぜか。

**模範回答：** FRはCDRの根元、VH–VL配向、ドメインの安定性を決めるため、同じCDRでも三次元配置や運動性が変わり得る。FR自身が抗原へ接触する場合もあるので、同一条件で実測する必要がある。

### 問2

二つの論文で「HCDR1の30番残基」を比較するとき、最初に何を確認すべきか。

**模範回答：** Kabat、Chothia、IMGTなど、両論文の番号付け方式とCDR境界を確認する。同じ数字や領域名でも、方式が違えば対応する残基が異なる可能性がある。

## さらに調べる疑問2〜3問

1. Kabat、Chothia、IMGTで6本のCDR境界は具体的にどこまでずれるか。
2. CDR graftingでback mutation候補を選ぶ構造基準と実験基準は何か。
3. FRを固定してCDRだけを多様化するライブラリは、どのような探索バイアスを生むか。

## 自分の3行要約

- VHとVLには各3本のCDRと4つのFRがあり、6本のCDRが抗原結合面の中心をつくる。
- FRは単なるスペーサーではなく、折りたたみ、CDR配座、VH–VL配向を介して結合性を左右する。
- 論文やAIデータでは、番号付け方式を統一し、CDRとFRを構造文脈の中で評価する。

## 未解決の疑問

抗原が未知でも、配列だけから「CDRを支えるために保持すべきFR残基」と「改変してもよいFR残基」を、抗体系列を越えてどこまで一般化して予測できるだろうか。

## 参考文献

1. Chiu ML, Goulet DR, Teplyakov A, Gilliland GL. [Antibody Structure and Function: The Basis for Engineering Therapeutics](https://doi.org/10.3390/antib8040055). *Antibodies (Basel).* 2019;8:55.
2. Sela-Culang I, Kunik V, Ofran Y. [The Structural Basis of Antibody–Antigen Recognition](https://doi.org/10.3389/fimmu.2013.00302). *Front Immunol.* 2013;4:302.
3. IMGT®. [Definition of the FR-IMGT and CDR-IMGT regions](https://www.imgt.org/IMGTScientificChart/Nomenclature/IMGT-FRCDRdefinition.html). Accessed 2026-09-07.
4. Abhinandan KR, Martin ACR. [Analysis and improvements to Kabat and structurally correct numbering of antibody variable domains](https://doi.org/10.1016/j.molimm.2008.05.022). *Mol Immunol.* 2008;45:3832–3839.
5. Chothia C, Lesk AM. [Canonical structures for the hypervariable regions of immunoglobulins](https://doi.org/10.1016/0022-2836(87)90412-8). *J Mol Biol.* 1987;196:901–917.
6. North B, Lehmann A, Dunbrack RL Jr. [A new clustering of antibody CDR loop conformations](https://doi.org/10.1016/j.jmb.2010.10.030). *J Mol Biol.* 2011;406:228–256.
7. Koenig P, Lee CV, Walters BT, et al. [Mutational landscape of antibody variable domains reveals a switch modulating the interdomain conformational dynamics and antigen binding](https://doi.org/10.1073/pnas.1613231114). *Proc Natl Acad Sci USA.* 2017;114:E486–E495.
8. Riechmann L, Clark M, Waldmann H, Winter G. [Reshaping human antibodies for therapy](https://doi.org/10.1038/332323a0). *Nature.* 1988;332:323–327.
