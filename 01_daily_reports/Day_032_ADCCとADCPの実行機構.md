---
day: 32
topic: ADCCとADCP――抗体が免疫細胞を動員する仕組み
created: 2026-09-21
status: unread
---

# Day 032：ADCCとADCPの実行機構

## 今日の問い

抗体で覆われた標的を、NK細胞はなぜ「殺し」、マクロファージはなぜ「食べる」のか。ADCCとADCPを、共通するFcγ受容体認識と、異なる実行機構・測定法に分けて説明できるだろうか。

## 本文

### 1. 抗体は標的とeffector細胞を橋渡しする

抗体依存性細胞傷害（**ADCC**）と抗体依存性細胞貪食（**ADCP**）は、どちらもIgGが標的表面の抗原へFabで結合し、露出したFcが免疫細胞のFcγ受容体（FcγR）を集めることから始まる。抗体による被覆を**オプソニン化**という。単量体IgGと受容体が一対一で結合しただけではなく、標的上に並んだ複数のFcが受容体を架橋し、ITAM依存性シグナルを閾値以上へ上げることが重要である[1,2]。

ただし、同じ入口から同じ結末になるわけではない。どのeffector細胞が、どの活性化型・抑制型受容体をどれだけ発現し、細胞内にどの実行装置をもつかで出力が変わる。ADCCとADCPは「抗体が直接殺す作用」ではなく、抗体が標的を指定し、宿主細胞が処理を実行する作用である。

### 2. ADCC：NK細胞が標的細胞死を誘導する

治療用IgG1で典型的なADCCのeffectorはNK細胞であり、主要な入口はFcγRIIIA（CD16A）である。抗体で覆われた標的とNK細胞が接触すると免疫シナプスが形成され、CD16Aに会合するFcRγ鎖やCD3ζ鎖のITAMがリン酸化される。下流で細胞骨格が再編され、細胞傷害性顆粒が接触面へ移動する。放出された**perforin**が標的膜でgranzymeの侵入を助け、**granzyme**がapoptosisを促す。NK細胞はIFN-γなども分泌する[2,3]。

ADCCは抗体濃度だけで決まらない。抗原密度、エピトープの膜からの距離、Fcの向き、CD16A密度、V158/F158多型、NK細胞の成熟・活性化状態、effector-to-target（E:T）比、反応時間が結果を変える。標的結合が飽和しても、適切な細胞間配置を作れなければ最大傷害は上がらない。したがって、結合EC50の改善をADCC改善と同一視してはいけない。

### 3. ADCP：食細胞が標的を包み込み分解する

ADCPの代表的effectorは単球・マクロファージである。これらはFcγRI、FcγRIIA、FcγRIIIAなどの活性化型受容体に加え、抑制型FcγRIIBも発現する。標的上のFcが活性化型受容体を十分に架橋すると、Sykを含むシグナルによりアクチンが再編され、膜が標的を包む**phagocytic cup**を形成する。標的はphagosomeへ取り込まれ、lysosomeとの融合、酸性化、酵素・活性酸素などにより分解される[4,5]。

ADCPでは「接着」と「完全な内部化」を分ける必要がある。二次元画像では、マクロファージ表面に付着した標的を取り込みと誤認し得る。pH感受性色素、z-stack、imaging flow cytometry、細胞外蛍光の消光などで内外を区別する。また一個のマクロファージが短時間に処理できる標的数には限界があり、連続負荷後に貪食能が低下する**hypophagia**も報告されている[6]。一時点の平均貪食率だけでは、速度や処理容量を見落とす。

### 4. 二つの機能を決める共通因子と相違点

ADCCとADCPに共通するのは、抗原占有、Fcの集合、FcγR架橋、活性化／抑制シグナルの釣り合いである。一方、ADCCは主に標的細胞死、ADCPは物理的な取り込みと分解を終点とする。マクロファージも標的へ傷害を与え、NK以外の細胞もcytotoxicityへ寄与し得るため、名称だけで細胞種を断定せず、実験で使ったeffectorとreadoutを確認する。

標的側の抵抗機構も異なる。抗原の内在化・sheddingは両方を弱め得る。ADCPではさらに、標的上のCD47が食細胞のSIRPαへ「don't eat me」シグナルを送り、FcγRによる貪食を抑える。したがって作用は `eat me（オプソニン化）` と `don't eat me` の合算で決まる。in vitroで強いFcγR活性を示しても、腫瘍組織へのeffector浸潤や抑制性環境が不十分なら、in vivo効果は限定され得る[4]。

### 5. Fc設計は出力を上げるが、目的に合わせる

IgG1 FcのN297糖鎖からコアフコースを減らすとFcγRIIIA結合が強まり、NK細胞によるADCCが増強され得る。Shieldsらは、低フコースIgG1でFcγRIIIA結合が大きく改善し、複数ドナーのNK細胞または単球を用いた細胞傷害が増えることを示した[7]。Fc点変異でも、特定FcγRへの親和性や活性化型／抑制型受容体の選択性を調整できる。

しかし「FcγR結合を強くするほど良い」は一般則ではない。標的除去が目的ならADCC・ADCP増強は有利になり得るが、受容体を遮断する抗体や組織保護を狙う抗体では正常細胞傷害を増やす危険がある。またFcγRIIIA最適化がマクロファージの複数受容体を介するADCPを同じ割合で高めるとは限らない。Fab、サブクラス、Fc配列、糖鎖、標的抗原、想定effectorを一つの設計問題として扱う。

### 6. assayは「途中の段階」を測っている

ADCCでは、標的細胞からの^51Cr・LDH・蛍光色素の放出、flow cytometryによる生死、NK細胞のCD107a脱顆粒、サイトカイン、CD16Aレポーターなどが使われる。レポーター発光は受容体シグナルを再現性高く測れるが、perforin・granzymeによる実際の殺傷ではない。一次NK細胞は生理的だが、ドナー差、凍結、FcγR多型の影響を受ける[3,8]。

ADCPでは、取り込まれた粒子・細胞の割合、effector一個当たりの取り込み数、phagosome酸性化、残存標的数などを測る。抗体間比較では、抗原発現量、抗体濃度、E:T比、effectorの由来・分化条件、反応時間を揃える。さらにFab同一のFc-silent対照、FcγR阻害、標的陰性細胞を置けば、Fc依存性と抗原特異性を切り分けられる。Clynesらの受容体欠損マウス研究は、抗腫瘍抗体のin vivo作用にFcγRが寄与し、活性化型と抑制型の釣り合いが重要であることを示したが、特定のin vitro readoutだけで臨床機序を断定できるわけではない[9]。

## 図または比較表

```text
標的抗原 ─ Fab─IgG─Fc ─ FcγR架橋
                         │
             ┌───────────┴───────────┐
             ▼                       ▼
       NK細胞（主にCD16A）      マクロファージ（複数FcγR）
       免疫シナプス形成          phagocytic cup形成
       顆粒放出                  包み込み・phagosome化
       perforin / granzyme       lysosome融合・分解
             ▼                       ▼
       ADCC：標的細胞死          ADCP：標的の内部化・消化
```

| 観点 | ADCC | ADCP |
|---|---|---|
| 典型的effector | NK細胞 | 単球・マクロファージ |
| 主要FcγRの例 | FcγRIIIA（CD16A） | FcγRI、FcγRIIA、FcγRIIIA、FcγRIIB |
| 実行機構 | 脱顆粒、perforin・granzyme | アクチン再編、包み込み、phagolysosome分解 |
| 直接の終点 | 標的細胞死 | 標的の内部化・分解 |
| 代表readout | 生死、放出assay、CD107a、レポーター | 内部化率、取り込み数、酸性化、残存標的 |
| 主な注意点 | レポーター活性≠細胞死、ドナー/E:T比 | 付着≠内部化、処理容量と時間依存性 |

## 論文を読むためのポイント

1. **実行細胞を特定する**：PBMC、精製NK細胞、NK細胞株、単球由来マクロファージのどれか。由来・ドナー数・凍結条件も見る。
2. **readoutを機能名と照合する**：FcγRレポーター、脱顆粒、細胞死、取り込み、酸性化を同じ「ADCC/ADCP」として扱っていないか。
3. **assay条件を確認する**：抗原密度、抗体濃度、E:T比、反応時間、血清・補体の有無はそろっているか。
4. **Fc依存性を検証する**：Fc-silent対照、FcγR阻害、受容体欠損で作用が低下するか。
5. **細胞種を越えて一般化しない**：CD16A結合改善から、すべてのeffector機能が増強したと結論していないか。
6. **in vitroとin vivoを分ける**：組織分布、effector浸潤、標的量、抑制性環境を議論しているか。

論文の “enhanced ADCC” がレポーターEC50だけに基づくなら、正確には「その受容体経路の活性化が増えた」と読む。実際の標的細胞死を主張するには、殺傷readoutと適切な対照が必要である。

## 抗体×AIとの接続

ADCC/ADCP予測のラベルには、抗体配列だけでなく、Fc糖鎖、IgGサブクラス、抗原密度、effector細胞、FcγRアレル、E:T比、反応時間、readoutを紐づける。同じ抗体でも条件によりEC50や最大応答が変わるため、レポーター発光、標的死率、内部化率を一列の「Fc activity」へ混ぜない。

データ分割では、同一Fab/Fcの濃度系列や同一ドナー反復をtrain/testへまたがせない。未知抗体、未知標的、未知ドナーのどれへ一般化したいかでgroup splitを変える。機構に沿う設計として、`抗原占有 → FcγR架橋 → 細胞活性化 → 殺傷／貪食` を別タスクにし、各段階の不確実性を残す方法が考えられる。

## 重要用語（8語）

- **ADCC**：抗体で標識された標的へeffector細胞が傷害を与える機構。典型例はNK細胞による標的細胞死。
- **ADCP**：抗体で標識された標的を食細胞が取り込み、分解する機構。
- **オプソニン化**：抗体などが標的表面を覆い、免疫細胞に認識・処理されやすくすること。
- **免疫シナプス**：effector細胞と標的細胞の間に形成される、受容体と実行分子が組織化された接触面。
- **脱顆粒**：NK細胞などが細胞傷害性顆粒を細胞外へ放出する過程。
- **phagocytic cup**：食細胞膜が標的を包み込む際に形成する杯状構造。
- **E:T比**：effector細胞数とtarget細胞数の比。assay出力を大きく左右する。
- **Fc-silent抗体**：FcγRなどへの結合を抑え、Fc依存性機能を低減した対照または治療用抗体。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

CD16Aレポーター活性が2倍になっただけで、「NK細胞によるADCCが2倍になった」と結論できないのはなぜか。

**模範回答：** レポーターは受容体下流の転写シグナルを測るモデルで、NK細胞の免疫シナプス形成、脱顆粒、標的細胞死を直接測っていないからである。一次NK細胞などを用いた殺傷readoutで確認する必要がある。

### 問2

マクロファージと蛍光標識標的が重なって見えたとき、ADCPを証明するために何を追加すべきか。

**模範回答：** 表面付着と細胞内取り込みを区別するため、pH感受性色素、z-stack、細胞外蛍光消光などを用いる。さらにFc-silent対照やFcγR阻害で、抗原・Fc依存性を確認する。

## さらに調べる疑問2〜3問

1. エピトープの膜からの距離は、NK細胞の免疫シナプス形成とADCCをどう変えるか。
2. CD47–SIRPα阻害は、どの抗体・マクロファージ条件でADCP増強と毒性の釣り合いが最も良いか。
3. afucosylationはADCCとADCPを同じ程度に増強するのか、それともeffector細胞・受容体構成で異なるのか。

## 自分の3行要約

- （1行目）
- （2行目）
- （3行目）

## 未解決の疑問

- （学習後に記入）

## 参考文献

1. Nimmerjahn F, Ravetch JV. [Fcγ receptors as regulators of immune responses](https://doi.org/10.1038/nri2206). *Nat Rev Immunol.* 2008;8:34–47.
2. Bruhns P, Jönsson F. [Mouse and human FcR effector functions](https://doi.org/10.1111/imr.12350). *Immunol Rev.* 2015;268:25–51.
3. Vincken R, Armendáriz-Martínez U, Ruiz-Sáenz A. [ADCC: the rock band led by therapeutic antibodies, tumor and immune cells](https://doi.org/10.3389/fimmu.2025.1548292). *Front Immunol.* 2025;16:1548292.
4. Gül N, van Egmond M. [Antibody-dependent phagocytosis of tumor cells by macrophages: a potent effector mechanism of monoclonal antibody therapy of cancer](https://doi.org/10.1158/0008-5472.CAN-15-1330). *Cancer Res.* 2015;75:5008–5013.
5. Kamen L, et al. [Antibody-mediated phagocytosis in cancer immunotherapy](https://doi.org/10.1111/imr.13265). *Immunol Rev.* 2023;319:128–141.
6. Pinney JJ, et al. [Macrophage hypophagia as a mechanism of innate immune exhaustion in mAb-induced cell clearance](https://doi.org/10.1182/blood.2020005571). *Blood.* 2020;136:2065–2079.
7. Shields RL, et al. [Lack of fucose on human IgG1 N-linked oligosaccharide improves binding to human FcγRIII and antibody-dependent cellular toxicity](https://doi.org/10.1074/jbc.M202069200). *J Biol Chem.* 2002;277:26733–26740.
8. Schön MP, et al. [The role of Fc receptors on the effectiveness of therapeutic monoclonal antibodies](https://doi.org/10.3390/ijms22168947). *Int J Mol Sci.* 2021;22:8947.
9. Clynes RA, Towers TL, Presta LG, Ravetch JV. [Inhibitory Fc receptors modulate in vivo cytotoxicity against tumor targets](https://doi.org/10.1038/74704). *Nat Med.* 2000;6:443–446.
