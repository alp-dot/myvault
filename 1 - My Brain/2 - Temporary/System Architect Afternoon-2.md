====
## 生成AI活用を前提とした業務システムにおけるアーキテクチャ設計

### 問題

株式会社X製作所（以下、X社）は、創業50年を迎える中堅の特殊産業機械メーカーである。近年、グローバル競争の激化と顧客からの要求水準の高まりを受け、業務効率化と顧客サポート品質の向上が急務となっている。特に、技術サポート部門では、多くの業務プロセスが旧来のシステムと熟練従業員の暗黙知に依存しており、知識継承が課題となっている<sup>1</sup>。これは、いわゆる「2025年の崖」で指摘されるレガシーシステム問題の一側面でもある<sup>3</sup>。

X社は、競争力強化のため、デジタルトランスフォーメーション（DX）の一環として、技術サポート業務の効率化と品質向上、および社内ナレッジ活用の促進を目指している<sup>1</sup>。

**対象業務：** 技術サポートにおけるナレッジ活用

現在、技術サポート担当者は、顧客やフィールドエンジニアからの複雑な機械仕様、トラブルシューティング、保守手順に関する問い合わせに対応している。対応時には、断片化されたナレッジベース（構造化されたデータベースのエントリ、PDF形式の技術マニュアル、社内Wiki、メールアーカイブなどが混在）を検索する必要がある。検索はキーワードベースであり、関連性の低い情報がヒットしたり、文書内の重要な詳細を見逃したりすることが多い。複雑な、あるいは文書化されていない問題については、しばしば上級エンジニアへの相談が必要となり、これが遅延の原因となっている。

既存システムとしては、基本的なチケット管理システム、マニュアルを保管する文書管理システム（DMS）、社内Wikiプラットフォームが存在するが、これらは連携しておらず、意味的な検索機能も欠けている。

**現状の課題**

* **非効率性:** サポート担当者は、複数の情報源から関連情報を探し出すのに多くの時間を費やしている。
* **不整合:** 回答内容は、担当者の情報検索・解釈能力や適切な専門家へのアクセス可否によってばらつきが生じる。
* **知識のボトルネック:** 複雑な問題解決が少数の上級エンジニアに集中し、遅延発生や貴重な暗黙知喪失のリスクとなっている<sup>2</sup>。
* **情報のサイロ化:** ナレッジが散在し、異なるリポジトリ間での更新が不整合である。これは、データが効果的に活用されていないデータ駆動型アプローチにおける課題と共通する<sup>9</sup>。

**生成AI導入の目的**

X社はこれらの課題を解決するため、生成AI技術の導入を決定した。期待される効果は以下の通りである。

* **効率向上:** 正確な技術情報を見つけ、問い合わせを解決するために必要な平均時間を短縮する<sup>14</sup>。
* **品質向上:** ナレッジコーパス全体を活用し、一貫性のある正確かつ包括的な回答を提供する。
* **知識の獲得とアクセシビリティ:** 様々な情報源から情報を統合し、暗黙知を効果的に捉え、アクセスしやすくするシステムを構築する。
* **サポート担当者の能力向上:** AIによる支援を提供することで、若手担当者がより複雑な問い合わせに自律的に対応できるようにする。

**想定されるリスクと懸念事項**

一方で、生成AI導入には以下のようなリスクや懸念事項が想定される。

* **精度とハルシネーション:** 生成AIが不正確または捏造された技術情報（ハルシネーション）を提供するリスク。これは不適切な機械操作や保守につながる可能性がある<sup>18</sup>。製造業の文脈では、誤った技術アドバイスは安全上の重大な結果を招く可能性があるため、特に重要視される。
* **データセキュリティと機密性:** 独自の技術仕様、サポートログ内の顧客データ、内部議論などの機密情報が、AIインターフェースを通じて漏洩したり、モデルによって意図せず学習・漏洩したりしないようにすること<sup>18</sup>。
* **連携の複雑性:** 生成AIソリューションを既存のチケットシステム、DMS、Wiki、ユーザー認証システムなどと連携させる際の技術的課題<sup>23</sup>。
* **プロンプトインジェクション:** 悪意のある者が巧妙なプロンプトを用いてAIを操作し、機密情報を抽出したり、誤動作を引き起こしたりするリスク<sup>18</sup>。
* **コスト:** LLM API呼び出し、ベクトルデータベースのホスティング、埋め込み生成、および潜在的なモデルのファインチューニングに関連するコストの管理<sup>25</sup>。
* **ユーザーの採用とトレーニング:** サポート担当者が新しいツールを信頼し、効果的に活用できるようにするためのトレーニングとワークフロー変更の必要性。
* **バイアス:** 基礎となる知識ソースに古い情報や偏った情報が含まれている場合に、バイアスが生じる可能性<sup>26</sup>。

あなたは、X社のシステムアーキテクトとして、この生成AIを活用した技術サポート業務支援システムの導入プロジェクトを担当することになった。 あなたの経験と考えに基づいて<sup>31</sup>、以下の設問ア～ウに従って論述せよ。

### 設問ア (800字以内) <sup>32</sup>

あなたが担当する生成AIを活用した技術サポート業務支援システムについて、(1)対象とする具体的な業務内容、(2)生成AIを適用する目的とそのように考えた理由、(3)システム導入における最も重要と考える課題又はリスクとその理由を述べよ。

### 設問イ (800字以上1,600字以内) <sup>32</sup>

設問アで述べた目的を達成し、課題・リスクに対応するためのシステムアーキテクチャについて、以下の点を具体的に論述せよ。

(1) 生成AI技術（例：外部LLM API利用、RAG、ファインチューニング）をどのようにシステムに組み込むか、その全体構成（例：AIコンシェルジュ、AIオーケストレータ<sup>23</sup>）。既存の知識文書（マニュアル、Wikiなど）からの情報アクセスと統合には、RAG（検索拡張生成）が一般的に適していると考えられる<sup>25</sup>。ファインチューニングは、特定の応答スタイルやタスクに特化させる場合に有効である<sup>25</sup>。
(2) 既存システム（チケットシステム、DMS、Wiki等）との連携方式。
(3) 主要なデータフロー（例：ナレッジ取込、ベクトル化、プロンプト生成、応答生成、フィードバック）とデータ管理方針。継続的な改善のためには、ユーザーからのフィードバックを収集し、システム改善に活用するループの設計が重要となる。
(4) 非機能要件（特に、回答精度、応答性能、セキュリティ、可用性）をどのように考慮して設計したか。特に、機密情報漏洩やプロンプトインジェクションといった生成AI特有のセキュリティリスク<sup>18</sup>や、システムの可用性・回復力（レジリエンス）<sup>39</sup>に対する考慮が求められる。
(5) なぜそのアーキテクチャを選択したのか、技術選定の理由と比較検討。RAGとファインチューニングの特性を理解し、本業務における適用理由を明確にすることが期待される<sup>25</sup>。

### 設問ウ (600字以上1,200字以内) <sup>32</sup>

あなたが設計したシステムアーキテクチャについて、以下の点を具体的に論述せよ。

(1) 回答精度向上やハルシネーション抑制のために特に工夫した点。例えば、RAGプロセスにおける情報源の明示、回答に対する信頼度スコアリング、不明確な場合に推測せずその旨を回答させる指示などが考えられる<sup>18</sup>。
(2) 情報漏洩対策、プロンプトインジェクション対策など、セキュリティ設計で特に考慮した点。入力プロンプトの検証・無害化、出力フィルタリング、LLMへのアクセス権限の最小化<sup>22</sup> など、多層的な防御策が考えられる<sup>18</sup>。
(3) 潜在的なバイアスなど、倫理的配慮についてどのように対応したか。知識ベースの監査、ユーザーによるバイアス報告機能の実装、多様性を考慮したテストなどが考えられる<sup>26</sup>。
(4) コスト最適化のために考慮した点。LLMの選択、APIコール数の削減策、効率的なデータ処理などが考えられる<sup>25</sup>。
(5) システム導入効果を測定するための主要なKPIとその測定方法。設問ア(2)で述べた目的に直結するKPI（例：平均処理時間短縮率、初回解決率向上、ユーザー満足度）を設定し、具体的な測定方法（例：チケットシステムログ分析、アンケート調査）を示す必要がある。
(6) 今後に向けた課題や機能拡張の展望。

### Works cited

<sup>1</sup> 2025年の崖 | IT業界の未来、トレンドと課題 | Kaopiz - カオピーズ, accessed on April 13, 2025, https://kaopiz.com/ja-news-the-cliff-of-2025-it-trend-and-industry-challenges-and-solutions/
<sup>2</sup> 2025年の崖 レガシーシステムの刷新と効果的なDX推進とは？ | 特集一覧, accessed on April 13, 2025, https://www.mjs.co.jp/topics/lp/cliff2025/
<sup>3</sup> 2025年の崖 | レガシーシステム のリスク回避と改善策を徹底解説 - カオピーズ, accessed on April 13, 2025, https://kaopiz.com/ja-news-legacy-systems-2025-cliff-strategies/
<sup>4</sup> 「2025年の崖」とは？問題視されているレガシーシステムについて分かりやすく解説！ - IT調達ナビ, accessed on April 13, 2025, https://gptech.jp/articles/it-strat-gov-2025nogake/
<sup>5</sup> 「2025年の崖」実態調査--約8割がレガシーシステムを刷新予定 - ZDNET Japan, accessed on April 13, 2025, https://japan.zdnet.com/article/35226119/
<sup>6</sup> 2025年の崖とは？現状の課題や対策を徹底解説 | ドコモビジネス - NTTコミュニケーションズ, accessed on April 13, 2025, https://www.ntt.com/business/services/xmanaged/lp/column/2025.html
<sup>7</sup> ITストラテジスト 午後１問題テーマ一覧（H24〜R06）｜オタリアブログ - note, accessed on April 13, 2025, https://note.com/otariablog/n/n1e411c5c21a4
<sup>8</sup> システムアーキテクト 午後I・午後II 出題 振り返り速報 令和6年春｜スタディルーム by rolerole, accessed on April 13, 2025, https://note.com/studyrolerole/n/n5e74b725edc7
<sup>9</sup> 「形だけデータドリブン経営」からの脱却 ～本質をおさえ成功に導く～［1. 課題編］, accessed on April 13, 2025, https://www.layers.co.jp/solution/datadriven3/
<sup>10</sup> データドリブン経営とは？企業のメリット・課題と成功事例 - Boxsquare, accessed on April 13, 2025, https://www.boxsquare.jp/blog/what-is-data-driven-management
<sup>11</sup> 【データドリブンを徹底説明】全社におけるデータ活用の実施方法や課題の解決法, accessed on April 13, 2025, https://www.nec-solutioninnovators.co.jp/sl/tableau/datacolumn/datadriven/index.html
<sup>12</sup> データドリブン経営とは？よくある課題や成功に導くためのポイントを紹介 - NEC, accessed on April 13, 2025, https://jpn.nec.com/solution/dotdata/tips/data-driven-management/index.html
<sup>13</sup> 【5分解説】データドリブン経営のための2つの課題と Salesforce流解決策, accessed on April 13, 2025, https://www.salesforce.com/jp/blog/jp-sales-datadriven/
<sup>14</sup> 【業種別】生成AIの活用事例10選！導入時のポイントや注意点も解説 - インテック, accessed on April 13, 2025, https://www.intec.co.jp/column/ai-03.html
<sup>15</sup> 国内大手企業での生成AI活用事例とツール12選！！ - freeconsultant.jp for Business, accessed on April 13, 2025, https://mirai-works.co.jp/business-pro/business-column/generative-ai-case-study
<sup>16</sup> 生成AIのビジネス活用事例まとめ！効果的に導入するポイントも解説 - OfficeBot, accessed on April 13, 2025, https://officebot.jp/columns/use-cases/generation-ai-case-study/
<sup>17</sup> 生成AI活用事例5選！業務を大幅に効率化する手法をわかりやすく解説, accessed on April 13, 2025, https://products.sint.co.jp/aisia-ad/blog/generative-ai-case-study/
<sup>18</sup> 生成AIのセキュリティリスクとその対策〜Azure OpenAI Serviceで実現する堅牢なセキュリティ, accessed on April 13, 2025, https://note.com/brainlab/n/n75bd4b1a915a
<sup>19</sup> 生成AIのセキュリティリスクとは？事例や企業の取るべきリスク対策を解説 - Sooon株式会社, accessed on April 13, 2025, https://sooon-web.com/media/knowledge/ai/genai-safety-guide/
<sup>20</sup> 生成AIのリスクを整理する｜３つの観点でリスクと対策を解説 - NRIセキュア, accessed on April 13, 2025, https://www.nri-secure.co.jp/blog/generative-ai-risks
<sup>21</sup> 生成AIによって生じるセキュリティリスクとは？対策も解説 - インターコム, accessed on April 13, 2025, https://www.intercom.co.jp/malion/column/generative-ai-security/
<sup>22</sup> プロンプト泥棒がやってくる！ 〜生成AI時代のセキュリティ対策〜 - Zenn, accessed on April 13, 2025, https://zenn.dev/codeciao/articles/prompt-injection-security
<sup>23</sup> 生成AIが与えるIT戦略へのインパクト, accessed on April 13, 2025, https://www.nri.com/content/900033983.pdf
<sup>24</sup> プロンプトインジェクションとは？生成AIを狙う新たな脅威を徹底解説 - セラク, accessed on April 13, 2025, https://www.seraku.co.jp/pr-site/newtonx/column/20.html
<sup>25</sup> LLMのファインチューニング徹底解説！RAGとの違いや活用のコツをご紹介 - WEEL, accessed on April 13, 2025, https://weel.co.jp/media/about-llm-finetuning/
<sup>26</sup> 生成AIのリスクとは？法的・倫理的・技術的リスクと対策 - SIGNATE Cloud, accessed on April 13, 2025, https://cloud.signate.jp/column/the-risks-of-generative-ai
<sup>27</sup> AI活用における倫理問題とは？実際の事例や解決策をわかりやすく解説, accessed on April 13, 2025, https://www.ai-souken.com/article/ai-ethics-in-usage
<sup>28</sup> 教育における生成AI活用のELSI（倫理的・法的・社会的課題）と未来展望 | 研究プログラム, accessed on April 13, 2025, https://www.tkfd.or.jp/research/detail.php?id=4664
<sup>29</sup> AIバイアスとは何ですか? - IBM, accessed on April 13, 2025, https://www.ibm.com/jp-ja/topics/ai-bias
<sup>30</sup> 生成AIの倫理的課題に教育はどう向き合うべきか？ 有識者と学校関係者が考える - EdTechZine, accessed on April 13, 2025, https://edtechzine.jp/article/detail/11136
<sup>31</sup> システムアーキテクト試験(2)：小論文を攻略｜ナカジマ - note, accessed on April 13, 2025, https://note.com/ma_nakajima/n/n0635bcb277b4
<sup>32</sup> システムアーキテクト 午後Ⅱ（午後2）論文 王道の書き方 | IT資格の歩き方, accessed on April 13, 2025, https://www.seplus.jp/it-exam-guide/guide/prep4writing_a_paper_sa/
<sup>33</sup> 高度情報処理技術者試験のいろいろ｜おやしろ - note, accessed on April 13, 2025, https://note.com/lambda_delta_34/n/na2d0a8329c31
<sup>34</sup> ローカルLLMの性能向上技術 : RAGとファインチューニングの比較ポイント - GMO Developers, accessed on April 13, 2025, https://developers.gmo.jp/technology/47731/
<sup>35</sup> 【論文瞬読】AI最前線、