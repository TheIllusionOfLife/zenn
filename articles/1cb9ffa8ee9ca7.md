---
title: "思考フレームワークを詰め込んだSkillでAIの思考力が上がった。"
emoji: "💡"
type: "tech"
topics:
  - "ai"
  - "idea"
  - "claude"
  - "skills"
published: true
published_at: "2026-02-10 06:35"
---

# 思考フレームワーク一覧
AIに相談しながら、下記フレームワークを選出した。

**ビジネス＆戦略（Business & Strategy）**

1. **Business Model Canvas (BMC)** — ビジネスモデルの9つの構成要素を一枚のキャンバスに可視化し、事業の全体像を設計・検証するフレームワーク。
2. **McKinsey 7S** — 組織の戦略・構造・システム・スキルなど7つの要素の整合性を分析し、変革管理やM&Aに活用するフレームワーク。
3. **Three Horizons** — 短期・中期・長期の3つの時間軸でイノベーションポートフォリオとリソース配分を計画するフレームワーク。
4. **Issue Tree** — 問題をMECE（漏れなくダブりなく）に分解し、構造的に根本原因を特定するフレームワーク。
5. **Porter's Five Forces** — 業界の競争環境を5つの力（競合、新規参入、代替品、買い手、売り手）から分析するフレームワーク。
6. **Jobs to be Done (JTBD)** — 顧客が「片付けたい用事」に着目し、真のニーズやプロダクト・マーケット・フィットを見極めるフレームワーク。

**クリエイティブ＆イノベーション（Creative & Innovation）**

7. **SCAMPER** — 既存のアイデアに対して代用・結合・応用・変更・転用・削除・逆転の7操作を適用して改良案を発想するフレームワーク。
8. **Design Thinking** — 共感・定義・発想・プロトタイプ・テストの5段階でユーザー中心の課題解決を行うフレームワーク。
9. **Six Thinking Hats** — 6色の帽子（事実・感情・批判・楽観・創造・統制）で役割を切り替え、バランスの取れた議論と意思決定を促すフレームワーク。
10. **Lateral Thinking** — 前提や常識を意図的に壊し、通常の論理的思考では到達しない斬新なアイデアを生み出すフレームワーク。
11. **TRIZ** — 技術的矛盾を体系的に解消するための40の発明原理を用いたロシア発の創造的問題解決理論。

**問題解決＆システム（Problem-Solving & Systems）**

12. **Cynefin** — 問題を「明確・煩雑・複雑・混沌・無秩序」の5領域に分類し、各領域に適した対処法を選択するセンスメイキング・フレームワーク。
13. **First Principles Thinking** — 既存の前提を全て取り払い、基本的な真理から再構築して本質的な解決策を導き出す思考法。
14. **Inversion（Munger）** — 「成功するには？」ではなく「失敗するには？」と逆から考えることで、リスクや落とし穴を事前に特定するチャーリー・マンガー流の思考法。
15. **Systems Thinking** — フィードバックループや創発的挙動に着目し、システム全体の相互作用と意図しない結果を理解するための思考法。

**AI推論・メタフレームワーク（AI Reasoning / Meta）**

16. **Tree of Thoughts (ToT)** — 複数の思考経路を木構造で並列探索し、多様な入力を統合して最適解を導く推論フレームワーク。
17. **Council of Experts** — 異なる専門家や利害関係者の視点をシミュレートし、多角的な助言を得るための仮想諮問会議フレームワーク。
18. **Chain of Verification (CoVe)** — 生成された主張や提案に対して検証質問を連鎖的に適用し、論理的整合性と信頼性を担保するファクトチェック・フレームワーク。
19. **Skeleton of Thoughts (SoT)** — まず骨格（アウトライン）を生成し、各セクションを並列的に肉付けすることで構造化されたアウトプットを効率的に作成するフレームワーク。
20. **ReAct** — 「思考→行動→観察」のサイクルを繰り返し、外部情報の検索と推論を交互に行うことでデータ駆動の分析を実現するフレームワーク。

合計 20フレームワーク（分析用15 + メタ/統合用5）。

# SKILL設定
ポイント
1.`SKILL.md`には全体のワークフローと思考フレームワークの概要だけを記載し、各フレームワークの詳細は`references`に格納。コンテクスト節約のため。
2. 複数のSubagentを使ってパラレルで思考。効率性とコンテクスト節約のため。
3. どのフレームワークを使うかは固定せず、適したフレームワークを選んで使ってもらう。ドメインによって適切なフレームワークが異なるため。

## SKILL.md
:::details SKILL.md
@[gist](https://gist.github.com/TheIllusionOfLife/1aab24921ded6474702b1faa7f36828d?file=SKILL.md)
:::

## references

:::details business-strategy.md
@[gist](https://gist.github.com/TheIllusionOfLife/1aab24921ded6474702b1faa7f36828d?file=business-strategy.md)
:::

:::details creative-innovation.md
@[gist](https://gist.github.com/TheIllusionOfLife/1aab24921ded6474702b1faa7f36828d?file=creative-innovation.md)
:::

:::details problem-solving.md
@[gist](https://gist.github.com/TheIllusionOfLife/1aab24921ded6474702b1faa7f36828d?file=problem-solving.md)
:::

:::details ai-reasoning.md
@[gist](https://gist.github.com/TheIllusionOfLife/1aab24921ded6474702b1faa7f36828d?file=ai-reasoning.md)
:::

# 実験
## 実験方法
Claude Cowork Opus 4.6に下記プロンプトを投げて比較。
セッションA(スキル使用):
`thinking-frameworks skillを使用して、人類文明がカルダシェフ・スケールのタイプⅠに50年以内に到達する方法を提案してください。回答はすべて日本語で。`

セッションB(スキル不使用。Baselineとして):
`人類文明がカルダシェフ・スケールのタイプⅠに50年以内に到達する方法を提案してください。回答はすべて日本語で。`

## 実験中の様子
スキル使用セッションがSubagentを使って並列思考している様子。
![](https://storage.googleapis.com/zenn-user-upload/b618d86ed990-20260210.png)

## 出力内容
出力されたレポートは下記の通り。
:::details スキル使用.md
@[gist](https://gist.github.com/TheIllusionOfLife/1aab24921ded6474702b1faa7f36828d?file=カルダシェフ・タイプⅠ到達戦略A.md)
:::

:::details スキル不使用.md
@[gist](https://gist.github.com/TheIllusionOfLife/1aab24921ded6474702b1faa7f36828d?file=カルダシェフ・タイプⅠ到達戦略B.md)
:::

## 評価
Webブラウザーで3つのLLMサービスを開き、上記レポートを2つ添付し、下記プロンプトで評価。
`添付したファイルそれぞれをレビューし、スコアを10点満点で算出してください。`

| 対象 | ChatGPT 5.2 Thinking | Claude Opus 4.6 | Gemini 3.0 Pro | 平均 |
|-----------|-----------|----------|-----------|-----------|
| スキル使用 | 8.8 | 8.5 | 9.5 | 8.93 |
| スキル不使用 | 6.6 | 6.5 | 7.5 | 6.87 |

スキル使用の方が平均で2.06ポイント良いという結果に。
各レビュー文章は下記。

:::details chatgpt_5-2_thinking_review.md
@[gist](https://gist.github.com/TheIllusionOfLife/1aab24921ded6474702b1faa7f36828d?file=chatgpt_5-2_thinking_review.md)
:::

:::details claude_opus_4-6_review.md
@[gist](https://gist.github.com/TheIllusionOfLife/1aab24921ded6474702b1faa7f36828d?file=claude_opus_4-6_review.md)
:::

:::details gemini_3-0_pro_review.md
@[gist](https://gist.github.com/TheIllusionOfLife/1aab24921ded6474702b1faa7f36828d?file=gemini_3-0_pro_review.md)
:::

# 結び
試みとしては成功。
LLMの評価としても、主観的にも明らかに良い出力がされるようになった。
skillはMCPと違ってコンテクストのオーバーヘッドが少ないので、とりあえずこのまましばらく運用予定。

## 今後
1. Agent teamsの仕組みでsubagent同士がコミュニケーションできるようにする。
2. codexやgemini cliのレビューを挟む。
3. フレームワークの追加削除。
4. フレームワーク適用ワークフロー改善。
5. subagentのプロンプト改善。