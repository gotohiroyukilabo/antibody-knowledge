---
day: 34
topic: FcRn――IgGの長い血中半減期を支えるリサイクル
created: 2026-09-23
status: unread
---

# Day 034：FcRnが支えるIgG再利用

## 今日の問い

血中のIgGは細胞へ取り込まれても、なぜ多くが分解を免れて再び循環へ戻れるのか。FcRnのpH依存的な結合・選別・放出を説明し、FcRn結合を強めれば常に抗体の半減期が延びるわけではない理由まで考えよう。

## 本文

### 1. FcRnはIgGを「作る」のではなく、分解から救う

**FcRn（neonatal Fc receptor）**は、IgGと血清アルブミンを細胞内で回収し、リソソーム分解から保護する受容体である。名前は新生児期の母体IgG輸送から付いたが、成人でも血管内皮細胞や造血系細胞などに発現し、IgG恒常性を支える。構造は典型的なFcγ受容体ではなく、FCGRTがコードするMHCクラスI様のα鎖とβ2-microglobulinからなるヘテロ二量体である[1]。

IgGの血中半減期が一般的な血清タンパク質より長く、ヒトIgG1ではおおむね数週間に及ぶ主要因がFcRnである。β2-microglobulinを欠き機能的FcRnを失ったマウスではIgG異化が著しく速くなることから、FcRnが単なる輸送体ではなく保護受容体であることが遺伝学的に示された[2]。ただし半減期はFcRnだけの性質ではなく、標的抗原、非特異的結合、免疫原性、分子安定性などの総和で決まる。

### 2. リサイクルは「取り込み→酸性で捕捉→選別→中性で放出」の循環である

血中IgGは主にfluid-phase pinocytosisによって、周囲の液体とともに非特異的に細胞へ取り込まれる。初期・sorting endosomeが酸性化して約pH 6になると、IgG FcのCH2–CH3境界にあるHis310やHis435などがプロトン化され、FcRnとの結合が安定化する。1分子のIgG Fcには二つのFcRnが結合し得る。FcRnに捕捉されたIgGは分解経路から選別され、リサイクル小胞に乗って細胞表面へ戻る。一方、結合しなかったタンパク質は後期endosomeからlysosomeへ進み、分解されやすい[1,3]。

小胞が細胞膜と融合すると、細胞外の約pH 7.4にさらされる。ヒスチジンの脱プロトン化によってFcRn–IgG結合が弱まり、IgGは血中へ放出される。この**pHスイッチ**により、細胞表面でIgGを捕まえ続けず、酸性endosome内だけで救出できる。Oberらの生細胞イメージングは、FcRn結合IgGと非結合IgGの分離がsorting endosomeで起こることを可視化した[3]。一個のIgGはこの循環を何度も通るため、1回ごとの救出が全身レベルの長い滞在時間につながる。

### 3. recyclingとtranscytosisを区別する

同じ側の膜へ戻す過程が**recycling**、極性をもつ上皮細胞の反対側へ運ぶ過程が**transcytosis**である。胎盤を介した母体IgG輸送や粘膜でのIgG移動には後者が関わるが、血中半減期の説明では前者が中心である。またFcRnはIgGに結合した抗原の運命にも影響する。抗原が酸性endosomeでもFabから離れなければ、抗体と一緒に循環へ戻され、抗原半減期まで延びることがある。したがって「抗体濃度が長く保たれる」と「標的を速く除去する」は同じ目標ではない。

### 4. 半減期延長変異では酸性での捕捉と中性での放出を両方見る

FcのFcRn結合面を改変し、酸性pHでの結合を強めれば救出確率を上げられる。代表例はM252Y/S254T/T256Eの**YTE**変異と、M428L/N434Sの**LS**変異である。YTEを導入した抗RSV抗体は、pH 6でヒト・カニクイザルFcRnへの結合が約10倍強まり、中性pHでは効率よく放出され、サルで半減期が約4倍になった[4]。健康成人で親抗体と比較した試験でも、clearanceが71〜86%低下し、終末相半減期は19〜34日から70〜100日へ延びた[5]。LS変異もpH 6でFcRn親和性を高め、サルの抗VEGF抗体で半減期を9.7日から31.1日へ延長した[6]。

しかし設計目標は「どのpHでも最強に結合」ではない。pH 7.4でも強く結合すると細胞表面で放出できず、再取り込みや分解が増えて、かえってclearanceが速くなり得る。そこで論文ではpH 6.0のKDやkoffだけでなく、pH 7.4での残留結合または解離を確認する。さらに同じ酸性pH親和性でも、測定形式、受容体の固定方向、avidity、温度で見かけ値は変わる。FcRn結合assayは機序を支持するが、PKそのものではない。

### 5. FcRn結合が良くてもPKが悪い場合がある

抗体が細胞表面抗原へ強く結合して内在化・分解される**target-mediated drug disposition（TMDD）**は、特に低濃度域で非線形clearanceを生む。抗体表面の疎水性・電荷patchによる非特異的取り込み、凝集、proteolysis、anti-drug antibody（ADA）もFcRn救出より速い消失経路になり得る。Fabやhingeを含むFcから離れた領域の変化も、分子全体の性質を通じてPKへ影響する。したがって、同じFcRn結合値を持つ候補でも、標的発現量や投与量が違えば半減期は一致しない[7]。

動物からヒトへの外挿にも注意が必要である。マウスFcRnはヒトIgGへヒトFcRnより強く、広い種のIgGに結合するため、通常マウスで長く残ることだけではヒトPKを保証できない。ヒトFcRnトランスジェニックマウスやカニクイザルを用いても、内因性IgG濃度、標的生物学、ADAは種間で異なる[7]。in vitro結合、細胞内recycling、複数種のPK、最終的なヒトデータを証拠の階段として読む。

### 6. 論文ではhalf-lifeだけでなくclearanceと曝露を見る

終末相半減期は濃度低下の傾きを表す要約値で、分布容積とclearanceの両方に依存する。FcRn改変の効果を評価するときは、親抗体との配列・Fab・製剤条件を揃え、`t1/2`、全身clearance、AUC、濃度–時間曲線を併読する。半減期が延びても活性が失われていないか、組織移行や安全性が変わらないかも必要である。臨床上の価値は単に長い数字ではなく、有効濃度をより長く維持して投与間隔や投与量を適正化できるかで決まる。

## 図または比較表

```text
血中 IgG（pH 7.4）
    │ fluid-phase pinocytosis
    ▼
酸性 sorting endosome（約pH 6）
    ├─ FcRnに結合 ─→ recycling小胞 ─→ 細胞表面（pH 7.4）
    │                                      └→ 解離して血中へ
    └─ 非結合 ─────→ late endosome ─────→ lysosomeで分解
```

| 評価項目 | 半減期延長を支持する所見 | 注意点 |
|---|---|---|
| FcRn結合（pH 6.0） | KD低下、特にkoff低下 | 強すぎても効果は頭打ちになり得る |
| 放出（pH 7.4） | 結合が弱い、速やかに解離 | 中性でも強い結合は逆効果になり得る |
| 細胞assay | lysosome回避、recycling増加 | 過剰発現細胞は生体を再現しない場合がある |
| in vivo PK | clearance低下、AUC・t1/2増加 | TMDD、ADA、非特異的結合、種差を切り分ける |

## 論文を読むためのポイント

1. **二つのpHを見る**：pH 6の捕捉だけでなく、pH 7.4で放出できるか。
2. **比較条件を見る**：親抗体とFab、投与量、製剤、標的結合性が揃っているか。
3. **PK指標を分ける**：`t1/2`だけでなくclearance、AUC、分布容積、濃度–時間曲線を確認する。
4. **線形性を見る**：用量でclearanceが変わるならTMDDの寄与を疑う。
5. **動物種を見る**：使ったFcRnはヒト、マウス、サルのどれか。野生型マウスの結果を直接ヒトへ外挿していないか。
6. **直交検証を見る**：無細胞結合、細胞recycling、in vivo PKが同じ機序を支持するか。

論文中の “enhanced FcRn binding” は、測定pHと測定形式を補って読む。酸性pHでの親和性向上は半減期延長の必要条件になり得るが、十分条件ではない。

## 抗体×AIとの接続

抗体PK予測の教師ラベルには、種、FcRn配列、投与経路・用量、採血時点、標的発現、ADA、Fc変異、pH別FcRn結合、clearance、AUCを紐づける。`half-life`だけを混ぜると、線形PKとTMDD、ヒトとマウス、親抗体とFc改変体を同じ問題として学習してしまう。

ランダムsplitでは、同一FabにYTEやLSだけを入れ替えた系列がtrain/testへ分かれ、モデルが系列を記憶しやすい。Fab系列または親抗体単位でgroup splitし、未知系列への一般化を測る。機構に沿って「pH 6捕捉」「pH 7.4放出」「非特異的clearance」「PK」を別タスクにすれば、長期滞留を予測した理由と失敗箇所を説明しやすい。

## 重要用語（8語）

- **FcRn**：酸性endosomeでIgGとalbuminを捕捉し、分解から救うMHCクラスI様受容体。
- **FCGRT**：FcRnのα鎖をコードする遺伝子。
- **β2-microglobulin**：FcRn α鎖と会合し、機能的受容体を構成する軽鎖。
- **recycling**：取り込んだ分子を同じ側の細胞表面へ戻す輸送。
- **transcytosis**：極性細胞の一方から取り込み、反対側へ放出する輸送。
- **pH依存結合**：酸性でFcRnへ結合し、中性で解離するIgG救出のスイッチ。
- **clearance**：単位時間あたりに薬物が除去されたとみなせる血漿容積。低下すると曝露が増えやすい。
- **TMDD**：薬物が標的へ結合して内在化・分解されることで生じる、飽和可能な消失経路。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

FcRnが血中pH 7.4ではなく、酸性endosome内でIgGへ結合することにはどんな利点があるか。

**模範回答：** 血中ではIgGを拘束せず、細胞へ非特異的に取り込まれた後だけ分解経路から救出できる。表面へ戻ると中性pHで解離するため、同じIgGを循環へ再放出できる。

### 問2

pH 6でFcRn親和性が高い候補抗体Aが、親抗体より短い半減期を示した。検討すべき原因を二つ挙げよ。

**模範回答：** pH 7.4でもFcRnから解離しにくく再循環が阻害された可能性と、TMDD・非特異的結合・ADAなどFcRn以外のclearanceが増えた可能性を検討する。

## さらに調べる疑問2〜3問

1. YTEやLS変異はFcγ受容体結合や補体活性など、半減期以外のFc機能をどう変え得るか。
2. FcRn阻害薬は病原性IgGを減らす一方、感染防御抗体やalbuminへどのような影響を与えるか。
3. pH依存的に抗原を放すrecycling antibodyは、通常抗体と比べて抗原消失をどう変えるか。

## 自分の3行要約

- （1行目）
- （2行目）
- （3行目）

## 未解決の疑問

- （学習後に記入）

## 参考文献

1. Roopenian DC, Akilesh S. [FcRn: the neonatal Fc receptor comes of age](https://doi.org/10.1038/nri2155). *Nat Rev Immunol.* 2007;7:715–725.
2. Ghetie V, et al. [Abnormally short serum half-lives of IgG in beta 2-microglobulin-deficient mice](https://doi.org/10.1002/eji.1830260327). *Eur J Immunol.* 1996;26:690–696.
3. Ober RJ, et al. [Visualizing the site and dynamics of IgG salvage by the MHC class I-related receptor, FcRn](https://doi.org/10.4049/jimmunol.172.4.2021). *J Immunol.* 2004;172:2021–2029.
4. Dall'Acqua WF, et al. [Properties of human IgG1s engineered for enhanced binding to the neonatal Fc receptor (FcRn)](https://doi.org/10.1074/jbc.M604292200). *J Biol Chem.* 2006;281:23514–23524.
5. Robbie GJ, et al. [A novel investigational Fc-modified humanized monoclonal antibody, motavizumab-YTE, has an extended half-life in healthy adults](https://doi.org/10.1128/AAC.01285-13). *Antimicrob Agents Chemother.* 2013;57:6147–6153.
6. Zalevsky J, et al. [Enhanced antibody half-life improves in vivo activity](https://doi.org/10.1038/nbt.1601). *Nat Biotechnol.* 2010;28:157–159.
7. Liu L. [Pharmacokinetics of monoclonal antibodies and Fc-fusion proteins](https://doi.org/10.1007/s13238-017-0408-4). *Protein Cell.* 2018;9:15–32.
