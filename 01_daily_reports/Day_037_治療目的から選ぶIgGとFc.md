---
day: 37
topic: 統合ケース――治療目的に応じてIgGサブクラスとFcを選ぶ
created: 2026-09-26
status: unread
---

# Day 037：治療目的から選ぶIgGとFc

## 今日の問い

同じ抗原へ結合するFabがあるとき、標的細胞を除去する抗体と、細胞を残してシグナルだけを遮断する抗体では、なぜ異なるIgGサブクラスとFc設計が必要なのか。架空の候補を使い、治療仮説から分子設計と検証実験へ落とし込もう。

## 本文

### 1. Fc選択は「標的をどうしたいか」から逆算する

Fabは標的を見分け、FcはFcγ受容体（FcγR）、C1q、FcRnとの相互作用を通じて、免疫細胞の動員、補体活性化、血中滞留を変える。設計の出発点は「IgG1かIgG4か」ではなく、**結合後に標的細胞を除去するのか、残すのか、どれだけ長く曝露するのか**である。IgG1〜4はヒンジ、FcγR・補体への結合傾向などが異なるが、サブクラス名だけで最終機能は決まらない[1,2]。

同じ抗原Xへ結合するFabを考える。疾患AではX高発現の病的細胞を除去したいが、正常細胞もXを低発現する。疾患BではX受容体陽性の正常細胞を残し、可溶性Xのシグナルだけを遮断したい。前者ではFc作用が薬効、後者では毒性になり得る。「標的の所在×望む細胞運命」を最初の設計変数にする。

設計は二層に分けると整理しやすい。第1層はIgG1、IgG2、IgG4などの骨格で、基本的なヒンジとFc特性を選ぶ。第2層はFc点変異、糖鎖、FcRn改変で、必要な機能だけを調節する。サブクラスを選んだ後も、Fabの抗原結合、抗原表面での配置、製造時の糖鎖が加わるため、「骨格名から作用を断定しない」ことが統合ケースの要点である。

### 2. ケースA：病的細胞を除去するならIgG1を基準にする

病的細胞の除去では、広いFcγRと相互作用しADCC・ADCPを起こしやすいIgG1が出発点になる。IgG3も強いeffector機能を示すが、長いヒンジ、アロタイプ依存の半減期、製造・安定性まで比較する必要がある[1]。

野生型IgG1で除去が不足するときは律速段階を分ける。NK細胞ADCCが不足するなら、脱フコース化やFcγR結合増強が候補になる。脱フコースIgG1は主にFcγRIII結合とADCCを高め、C1qやFcRnへの効果は同じではない[3]。CDCが必要なら、C1q結合だけでなく、抗原密度、epitope位置、Fc六量体化、補体沈着、細胞死まで見る[4]。二つの経路を最大化しても、生体内で単純な足し算になるとは限らない。

増強Fcは、抗体が十分に結合した正常細胞も攻撃し得る。病的／正常細胞の抗原密度分布と濃度反応曲線を比較し、「有効濃度で病的細胞を除去し、正常細胞への作用を許容できるか」を判断する。最大活性ではなく治療域が目標である。

例えばFcγRIIIa結合が10倍強くても、病的細胞上のXが少なければFcγRを十分に架橋できない。一方、正常細胞でXが多ければ毒性だけが増える可能性がある。精製受容体へのKDは機序の一部であり、抗原密度を変えた標的細胞、FcγRIIIa-V158/F158の双方、複数ドナーのeffector細胞で濃度反応を比較して初めて治療上の利点を判断できる。

### 3. ケースB：細胞を残すならFcを静音化する

可溶性Xの中和や受容体遮断が目的で、X受容体陽性細胞を残したいなら、IgG2、安定化IgG4、effector-silent IgG1が候補になる。IgG4は補体活性が低いが、FcγR結合はゼロではなく、天然型ではFab-arm exchangeも起こり得る。S228Pは交換を抑える代表的改変である[5]。IgG2にもFcγRIIa結合とヒンジ異性体があり、「低effector＝無作用」ではない。

IgG1の開発基盤を使うなら、LALA-PGのようにFcγR・C1q作用を抑え、FcRn相互作用を保つ設計も選べる[6]。ただし “silent” はassay条件つきの結論である。各FcγRとC1qへの結合、ADCC・ADCP・CDC、サイトカイン放出を想定濃度と抗原高密度条件まで測る。同時に中和・遮断能と、意図しない受容体架橋を確認する。

特に受容体抗体では、FcγRを介した抗体の集合が受容体を作動させることがある。遮断が目的なら、リガンド競合試験だけでなく、FcγR陽性細胞を加えた条件でも下流シグナルが生じないことを確かめる。逆に作動性抗体では、この架橋が薬効に必要かを意図的に検証する。

### 4. 半減期は独立した設計軸として重ねる

投与間隔を延ばすなら、YTEやLSのようなFcRn改変を追加できる。設計目標は酸性endosomeで捕捉され、中性の細胞表面で放出されるpH依存性である。YTEは酸性でのFcRn結合と霊長類での半減期を高めた[7]。ただし長い曝露は毒性も長引かせ、標的依存性消失（TMDD）が強ければPKは十分に伸びない。pH 6.0／7.4の結合、細胞recycling、in vivo PKを段階的に結ぶ。

FcRn改変はADCCやCDCの代用品ではなく、Fc静音化も長い半減期を保証しない。サブクラス、FcγR/C1q、糖鎖、FcRnを別の軸として選び、最後に一分子として抗原結合、発現量、安定性、凝集、非特異的結合、PK、安全性を再評価する。

### 5. 候補を絞る実験順序

同一Fabの少数パネルを作る。ケースAなら野生型IgG1、FcγR増強型、必要ならCDC増強型、ケースBならIgG2、S228P-IgG4、silent IgG1が候補である。まず単量体率、糖鎖、抗原結合を揃え、次に各FcγRアレル、C1q、FcRnへの結合、続いて一次NK細胞・マクロファージ・補体での機能、病的／正常細胞の安全域、最後にPKとin vivo薬効を調べる。

ここで同じFabを使うことは、Fcの寄与を切り分けるための対照設計である。しかしサブクラス変更でヒンジの長さや可動性も変わるため、可溶性抗原への親和性が同じでも、細胞表面での二価結合量が一致するとは限らない。各候補についてFab断片の結合と、完全長IgGの細胞結合を別々に測り、Fc機能試験へ投入される抗体量を揃える。

この順序なら、Fab結合量、受容体結合、細胞機能の差を混同しにくい。FcγRやFcRnには種差があるため、ヒト受容体・ヒトeffector細胞のデータを併用する[2,8]。判断は単一の強い数値ではなく、作用機序を支える因果証拠と安全性・物性のtrade-offで行う。

## 図または比較表

```text
抗体が標的へ結合した後、何を起こしたいか？
  ├─ 病的細胞を除去
  │    └─ IgG1を基準 → ADCC/ADCP不足ならFcγR軸、CDC不足ならC1q軸を検討
  ├─ 細胞を残して中和・遮断
  │    └─ IgG2／安定化IgG4／silent IgG1 → 残存effector作用を実測
  └─ 曝露期間を延長
       └─ 上記設計にFcRn軸を追加 → pH依存性、recycling、PKを確認

共通ゲート：抗原結合 → 分子品質 → 機能 → 正常細胞安全域 → PK・in vivo
```

| 治療目的 | 出発候補 | 強化／抑制する軸 | 決定的な機能試験 | 見逃しやすいリスク |
|---|---|---|---|---|
| 病的細胞の除去 | IgG1 | FcγR、必要ならC1q | ADCC、ADCP、CDC | 正常細胞除去、経路間干渉 |
| 可溶性因子の中和 | IgG2、S228P-IgG4、silent IgG1 | FcγR・C1qを抑制 | 中和＋残存effector assay | Fc残存活性、凝集による架橋 |
| 受容体遮断 | silent Fc候補 | FcγR・C1qと架橋を抑制 | 遮断、reporter、サイトカイン | 受容体作動、標的細胞減少 |
| 長期予防・維持 | 上記候補＋YTE/LS | FcRnのpH依存性 | recycling、PK、薬効 | 放出不良、TMDD、毒性長期化 |

## 論文を読むためのポイント

1. **作用機序を一文にする**：結合、中和、遮断、細胞除去、補体、受容体作動のどれか。
2. **標的細胞の運命を確認する**：除去したい細胞と保護すべき細胞、その抗原密度は示されているか。
3. **サブクラスと改変を分ける**：IgG骨格、Fc変異、糖鎖、FcRn変異を正確に記載しているか。
4. **証拠の階段を見る**：受容体結合だけでなく、細胞機能、正常細胞安全域、PK・薬効へつながるか。
5. **比較条件を揃える**：同一Fab、抗原結合量、単量体率、糖鎖、濃度、effector細胞、補体源が比較可能か。
6. **種差を読む**：抗体、FcγR、FcRn、補体、effector細胞の種は何か。

“IgG1 was selected for potent effector function” とあっても、どのeffector経路が治療に必要かは別問題である。逆に “effector-null” は変異名だけでなく、測った受容体、検出限界、濃度域を伴って初めて評価できる。

## 抗体×AIとの接続

IgG/Fc選択を予測するAIでは、配列だけを入力して「最良Fc」を一つ返す設計は不十分である。少なくとも標的が可溶性か細胞表面か、除去／保持したい細胞、抗原密度、epitope位置、FcγRアレルと発現細胞、補体条件、糖鎖、pH、投与目的を条件として持たせる。出力もFcγR結合、ADCC、ADCP、CDC、FcRn結合、PK、物性、安全性に分けたmulti-task問題になる。

学習データでは同一FabのFcパネルが因果比較に有用だが、同じFabや同一変異セットがtrain/testへまたがるとリークする。Fab系列、標的、Fc設計、assay campaignでgroup splitし、未見の標的または新しい機能試験で外部検証する。最終選択は単一スコア最大化ではなく、最低安全基準を満たした候補のPareto frontから行い、AI提案を直交する結合・細胞・物性・PK試験で確かめる。

## 重要用語（8語）

- **作用機序（MoA）**：抗体が治療効果を生む因果経路。
- **サブクラス選択**：IgG1〜4の定常領域差を治療目的へ対応させる設計。
- **effector-silent**：FcγR・C1qを介する作用を実用上十分に抑えたFc状態。
- **FcγR増強**：免疫細胞受容体への結合やシグナルを高め、ADCC・ADCPを強める設計。
- **脱フコース化**：Fc糖鎖のcore fucoseを減らし、主にFcγRIIIa結合とADCCを高める方法。
- **Fc六量体化**：抗原表面でFcが環状に集合し、C1q結合を促す過程。
- **治療域**：有効性が得られ、毒性が許容される曝露・濃度の範囲。
- **Pareto front**：複数の目的で、どれかを改善すると他が悪化する非劣解の集合。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

病的細胞Xを除去する抗体で、FcγRIIIa結合を高めたのにADCCが改善しなかった。次に確認すべき要因を三つ挙げよ。

**模範回答：** 標的細胞の抗原密度・抗体占有、effector細胞のFcγRIIIa発現／アレル、抗体の糖鎖・凝集・抗原結合を確認する。受容体への精製系結合だけでは、細胞上の架橋と傷害能を保証できない。

### 問2

正常細胞上の受容体を遮断する抗体にIgG4を選べば、Fc安全性試験を省略できるか。

**模範回答：** 省略できない。IgG4にも残存FcγR結合とFab-arm exchangeの問題があり、安定化変異の確認に加え、FcγR・C1q結合、細胞傷害、サイトカイン放出、意図しない架橋を実測する必要がある。

## さらに調べる疑問2〜3問

1. 同じ抗原でもepitopeの膜からの距離はADCC、ADCP、CDCの優先順位をどう変えるか。
2. FcγR増強と脱フコース化を組み合わせたとき、正常細胞に対する治療域はどう評価すべきか。
3. effector-silent変異とFcRn半減期延長変異の併用は、物性とPKへ独立に作用するか。

## 自分の3行要約

- （1行目）
- （2行目）
- （3行目）

## 未解決の疑問

- （学習後に記入）

## 参考文献

1. Vidarsson G, Dekkers G, Rispens T. [IgG subclasses and allotypes: from structure to effector functions](https://doi.org/10.3389/fimmu.2014.00520). *Front Immunol.* 2014;5:520.
2. Bruhns P, Jönsson F. [Mouse and human FcR effector functions](https://doi.org/10.1111/imr.12350). *Immunol Rev.* 2015;268:25–51.
3. Shields RL, et al. [Lack of fucose on human IgG1 N-linked oligosaccharide improves binding to human FcγRIII and antibody-dependent cellular toxicity](https://doi.org/10.1074/jbc.M202069200). *J Biol Chem.* 2002;277:26733–26740.
4. Diebolder CA, et al. [Complement is activated by IgG hexamers assembled at the cell surface](https://doi.org/10.1126/science.1248943). *Science.* 2014;343:1260–1263.
5. Silva JP, et al. [The S228P mutation prevents in vivo and in vitro IgG4 Fab-arm exchange](https://doi.org/10.1074/jbc.M114.600973). *J Biol Chem.* 2015;290:5462–5469.
6. Schlothauer T, et al. [Novel human IgG1 and IgG4 Fc-engineered antibodies with completely abolished immune effector functions](https://doi.org/10.1093/protein/gzw040). *Protein Eng Des Sel.* 2016;29:457–466.
7. Dall'Acqua WF, Kiener PA, Wu H. [Properties of human IgG1s engineered for enhanced binding to the neonatal Fc receptor (FcRn)](https://doi.org/10.1074/jbc.M604292200). *J Biol Chem.* 2006;281:23514–23524.
8. Saunders KO. [Conceptual approaches to modulating antibody effector functions and circulation half-life](https://doi.org/10.3389/fimmu.2019.01296). *Front Immunol.* 2019;10:1296.
