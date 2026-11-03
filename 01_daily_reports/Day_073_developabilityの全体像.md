---
day: 73
topic: developability全体像――良いbinderと良いdrugの違い
created: 2026-11-04
status: unread
---

# Day 073：developabilityの全体像

## 今日の問い

標的へ強く結合し、細胞アッセイでも効く抗体が見つかった。それでも医薬品候補として開発できない場合があるのはなぜで、探索初期に何を確認すべきだろうか。

## 本文

### 1. 良いbinderは出発点であり、良いdrugの十分条件ではない

抗体探索では、まず標的への結合、`KD`、特異性、細胞機能などを測る。この意味で**良いbinder**とは、意図した標的・エピトープに必要な強さと速度論で結合し、望む生物活性を示す分子である。一方、患者へ投与する**良いdrug**には、同じ分子を再現よく製造・精製でき、保存や輸送に耐え、必要濃度で投与でき、体内で予測可能に振る舞うことまで求められる。

**developability（開発適性）**とは、候補が製造可能で、安定かつ安全・有効な医薬品へ進める見込みを、分子の物理化学的性質と製造・製剤・薬物動態上のリスクから評価する考え方である。臨床段階の137抗体を共通のIgG1形式で比較した研究でも、臨床へ進んだ分子が全項目で一様に優れていたわけではなく、一部は非特異的結合、自己相互作用、疎水性などで外れ値を示した[1]。したがってdevelopabilityは合否を決める万能な一数値ではなく、複数のリスクを可視化して候補間のトレードオフを判断する枠組みである。

ここで「薬として良い」と「分子として扱いやすい」も完全な同義ではない。強い薬理作用が低い投与量で得られれば、多少濃縮しにくくても静脈投与で成立する可能性がある。逆に慢性疾患で高用量の皮下注射が必要なら、高濃度でも低粘度・高溶解性であることが重要になる。安全性と有効性は動物・臨床を含む別の証拠が必要であり、developability assayはそれらを直接証明するのではなく、開発を妨げ得る分子リスクを早期に調べる。

### 2. 六つの軸を「原因→測定→開発上の結果」で結ぶ

第一は**発現・製造性**である。重鎖と軽鎖が正しくfolding・assemblyし、高い収量で均一に得られるかを見る。低発現は、培養規模の拡大や精製コストだけでなく、分子自体の不安定性を示す手掛かりにもなる。

第二は**構造安定性**で、熱やpH変化によりunfoldingしにくいかを`Tm`や`Tonset`などで調べる。ただし高い`Tm`だけで長期保存中の安定性が保証されるわけではない。第三の**コロイド安定性**は、抗体同士が引き合い、可逆的自己会合、凝集、沈殿、相分離を起こす傾向である。高濃度では自己会合が粘度を上げ、特に少量を皮下投与したい製剤で充填・注射を難しくする。

第四は**溶解性と高濃度挙動**、第五は**非特異的結合・polyreactivity**である。CDR付近の露出した疎水性patchや偏った電荷は、標的以外のタンパク質・膜・組織との相互作用を増やし得る。Sharmaらは最大60種のIgG1で、粘度やclearance、化学的不安定性と配列・構造由来の物理量の相関を調べた[2]。また、ピコモル親和性と高いpotencyを持ちながら自己会合と不良なPKを示したMEDI1912は、自己会合界面の3変異により結合活性を保ったまま物性と血中滞留が改善した[3]。これは「最強binder」と「最良候補」が一致しない具体例である。

第六は**化学的安定性**で、脱アミド化、異性化、酸化、切断、意図しない糖鎖付加などの配列liabilityを確認する。修飾がCDRや重要な構造部位にあれば、保存中にpotency低下や不均一化を起こし得る。これら六軸は独立ではない。例えば疎水性patchは凝集、非特異的結合、精製挙動へ同時に影響し、変異で疎水性を下げれば親和性が落ちる場合もある。

体内動態もFcだけでは決まらない。SchochらはFcが近いIgG1とそのvariantを用い、Fvの電荷分布が生理的pH付近での過剰なFcRn結合と短い終末半減期に関係することを示した[6]。また標的量が多い、抗体–標的複合体がinternalizeされる、といったtarget-mediated drug dispositionもclearanceを変える。したがって速い消失を見たときは、非特異的な「stickiness」、FcRn、標的依存経路を分けて考える必要がある。

### 3. assay値は条件付きの観測である

初期screenでは少量試料を用い、SECで単量体率、DSF/DSCで熱転移、DLSやAC-SINSで自己相互作用、HICで疎水性、非特異的結合assayでpolyspecificity、加速・強制劣化で凝集や化学修飾を調べる。152抗体を解析した研究は、こうした多項目測定を生物活性と並行して早期に行い、後工程で問題になる候補を順位付けできることを示した[4]。

各assayの読み出しも区別する。SECの高分子量種はすでに生じた可溶性aggregateを捉えるが、将来の凝集速度や可逆的自己会合を単独では表さない。**Tm**は構造が熱でほどける転移点、HIC保持は疎水性相互作用の代理、AC-SINSは特定条件での自己相互作用の代理である。同じ現象を別原理で見る**直交assay**と、加速保存後にも抗原結合・細胞活性が残るかを組み合わせることで、単一測定への過剰な依存を避ける。

ただし測定値はformat、濃度、pH、塩、温度、賦形剤、stress時間に依存する。Fabで良好でもIgG化で自己会合する、低濃度では透明でも高濃度で粘度が急増する、といったことがある。従って論文の「developable」という語だけでなく、何を、どの条件で、どの対照と比較したかを読む。投与経路、必要用量、保存期間、製造工程が違えば許容範囲も変わるため、用途に即したtarget product profileから閾値を決める。

### 4. 早期に落とすだけでなく、設計可能性を残す

実務では、①配列から化学的liability、疎水性・電荷patchを警告し、②少量の精製抗体で直交するassayを測り、③少数候補を高濃度・stress・細胞・PK評価へ進める段階的funnelを使う。RaybouldらのTAPは臨床段階抗体の分布を基に、CDR長、表面疎水性、CDR電荷、VH/VL電荷非対称性をflag化したが、これは実験の代替ではなく優先順位付けである[5]。

問題が一つなら、親和性と機能を確認しながら表面残基を少数変異させ、修復できることがある。複数軸で重大なflagが出る候補は、後工程の処方工夫だけに賭けず、同等活性を持つ別系列へ切り替える判断も必要である。developability評価の目的は「完璧な分子」を探すことではなく、用途上致命的なリスクを早く見つけ、測定根拠をもって改変・選択することである。

## 図または比較表

| 評価軸 | 初期に見る例 | 悪い場合の主な影響 | binder評価だけでは見えるか |
|---|---|---|---|
| 結合・機能 | `KD`、`kon`、`koff`、細胞potency | 効果不足、off-target作用 | 見える |
| 発現・均一性 | 発現量、SEC、CE-SDS | 低収量、精製困難、不均一化 | 見えにくい |
| 構造・化学安定性 | `Tm`、stress後SEC、peptide mapping | 保存中の凝集・活性低下 | 見えない |
| 自己会合・溶解性 | AC-SINS、DLS、PEG沈殿 | 高粘度、沈殿、製剤化困難 | 見えない |
| 非特異的結合 | polyspecificity、陰性細胞・組織結合 | 速いclearance、安全性リスク | 標的選択性だけでは不十分 |
| 高濃度製剤性 | 粘度、濁度、相分離 | 皮下注射・充填の困難 | 見えない |

```text
多数のbinder
  ↓ 配列flag＋少量試料の多項目screen
活性と物性を両立するlead群
  ↓ 高濃度・stress・PK・製造条件で確認
用途の閾値を満たすdevelopment candidate
```

## 論文を読むためのポイント

1. **定義を分解する**：developabilityを何の測定値で定義したか。単なる予測scoreか、実測を含むか。
2. **条件を読む**：抗体format、buffer、pH、濃度、温度、stress時間、対照が揃っているか。
3. **直交測定を探す**：凝集をSECだけ、安定性を`Tm`だけで結論していないか。
4. **用途との接続を見る**：高濃度皮下製剤か静脈投与か、必要用量に合う閾値か。
5. **改変前後を追う**：物性改善変異がaffinity、特異性、細胞機能を損ねていないか。

## 抗体×AIとの接続

developability予測は本質的に**多目的学習**である。入力にはVH/VL配列だけでなく、構造、format、buffer、濃度、温度、assay法を含め、出力は発現量、`Tm`、凝集、粘度、非特異的結合などを別ラベルとして持つべきである。異なる条件の値を同じラベルとして混ぜると、モデルは分子差とassay差を区別できない。

Jainらの臨床段階抗体panelは重要なbenchmarkだが、「臨床に進んだ」という選抜済み集団であり、失敗候補や工程条件が十分に含まれない。AIの高い分類精度を新規系列への予測力と取り違えず、系列・clonotype単位で分割し、適用範囲外の候補には不確実性を示す。予測は実験数を減らす順位付けに使い、最終判断は用途に合った実測panelで行う。

## 重要用語（8語）

- **developability**：抗体候補を製造可能で安定・安全・有効な医薬品へ進められる見込み。
- **manufacturability**：発現、培養、精製、品質管理を再現よく実施できる性質。
- **conformational stability**：foldした立体構造を保ち、unfoldingしにくい性質。
- **colloidal stability**：溶液中で分子同士が過度に引き合わず分散状態を保つ性質。
- **self-association**：抗体分子同士が可逆的または不可逆的に会合すること。
- **polyreactivity**：一つの抗体が複数の無関係な分子へ結合する性質。
- **viscosity**：溶液の流れにくさ。高濃度製剤の製造・注射可能性を左右する。
- **sequence liability**：脱アミド化、酸化などを受けやすい配列上の部位。

## 理解確認問題2問と各問題の簡潔な模範回答

### 問1

ピコモル濃度の`KD`と強い細胞活性を持つ抗体でも、development candidateに選べない理由を二つ挙げよ。

**模範回答：** 高親和性でも、自己会合による凝集・高粘度や、非特異的結合による速いclearanceが起こり得る。結合・機能に加えて、製造、保存、製剤、体内動態を満たす必要がある。

### 問2

in silico developability scoreが良好なら実験評価を省略できるか。

**模範回答：** 省略できない。予測は候補のflag化と順位付けには有用だが、実際の挙動はformatや溶液条件、濃度に依存するため、用途に合った複数の実測assayで確認する。

## さらに調べる疑問2〜3問

1. 静脈投与と皮下投与では、許容できる抗体濃度と粘度の基準をどう変えるべきか。
2. `Tm`、`Tagg`、長期保存中の凝集速度は、どこまで互いを予測できるか。
3. developabilityを改善する変異と抗原結合を維持する変異を、active learningでどう選ぶか。

## 自分の3行要約

- （1行目）
- （2行目）
- （3行目）

## 未解決の疑問

- （学習後に記入）

## 参考文献

1. Jain T, et al. [Biophysical properties of the clinical-stage antibody landscape](https://doi.org/10.1073/pnas.1616408114). *Proc Natl Acad Sci U S A.* 2017;114:944–949.
2. Sharma VK, et al. [In silico selection of therapeutic antibodies for development: viscosity, clearance, and chemical stability](https://doi.org/10.1073/pnas.1421779112). *Proc Natl Acad Sci U S A.* 2014;111:18601–18606.
3. Dobson CL, et al. [Engineering the surface properties of a human monoclonal antibody prevents self-association and rapid clearance in vivo](https://doi.org/10.1038/srep38644). *Sci Rep.* 2016;6:38644.
4. Bailly M, et al. [Predicting Antibody Developability Profiles Through Early Stage Discovery Screening](https://doi.org/10.1080/19420862.2020.1743053). *mAbs.* 2020;12:1743053.
5. Raybould MIJ, et al. [Five computational developability guidelines for therapeutic antibody profiling](https://doi.org/10.1073/pnas.1810576116). *Proc Natl Acad Sci U S A.* 2019;116:4025–4030.
6. Schoch A, et al. [Charge-mediated influence of the antibody variable domain on FcRn-dependent pharmacokinetics](https://doi.org/10.1073/pnas.1408766112). *Proc Natl Acad Sci U S A.* 2015;112:5997–6002.
