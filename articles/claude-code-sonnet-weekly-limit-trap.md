---
title: "Claude CodeでSonnet 4.6だけ使ってたらSonnetの週制限に引っかかので対策を練った。"
emoji: "⚠️"
type: "tech"
topics:
  - "claude"
  - "ai"
  - "tips"
published: true
---

# Sonnet 4.6だけ使っていたら週制限に引っかかった

Claude Sonnet 4.6が導入されたので、どれどれと思って、週の切り替えのタイミングからそれだけ使っていた。

token消費が抑えられてかつ性能もいい感じだったんだけど、週の途中で下記のようになった。

![週制限に到達したスクリーンショット。All modelsは70%だが、Sonnet onlyが100%に](/images/claude-code-sonnet-weekly-limit-trap/weekly-limit.png)

All modelsの週制限は70%なのに、Sonnet onlyが100%に到達。

Claudeの週制限にはAll modelsとSonnet onlyの2つがあって、Sonnetばかり使っていると、全体の制限に余裕があってもSonnetだけ先に枯渇する。

こうなるとSonnetは使えない(OpusやHaikuを使う必要がある)。

# Subagentが失敗する

Sonnetの週制限に達すると、単にSonnetが使えなくなるだけでは済まない。

Subagent設定次第だが、Sonnetで動こうとするSubagentが失敗する(rate limitですぐexitしちゃう)。

これが地味に面倒。

# 回避策 Opus 4.6 + Effortパラメータ

おそらくベターな運用は、Opus 4.6をベースにしつつEffortパラメータを調整すること。
(モデルの切り替えが面倒くさくなければ、OpusでPlanして、Sonnetで実行みたいなのを丁寧にやるといいかもしれない。)

## Effortパラメータとは

Effortパラメータは、Claudeが応答時にトークンをどの程度積極的に使用するかを制御するパラメータ。

Claude Codeの最近のアプデで導入された(たしか2026年の2月中だったと思う)。

単一のモデルで応答の徹底性とトークン効率のトレードオフを調整できる。

公式ドキュメント
https://platform.claude.com/docs/ja/build-with-claude/effort

### Effortレベル一覧

| レベル | 説明 | ユースケース |
|--------|------|-------------|
| `high` | 高い能力。Claude Codeでのデフォルト(sonnet, opusともに) | 複雑な推論、難しいコーディング、エージェントタスク |
| `medium` | バランス型。適度なトークン節約 | 速度とコストとパフォーマンスのバランスが必要な場合 |
| `low` | 最も効率的。大幅なトークン節約 | 単純なタスク、サブエージェント向け |

※maxもあるけど、Claude Codeでは使えないので省略。

重要なのは、Effortはすべてのトークンに影響するということ。テキスト応答だけでなく、ツール呼び出しや拡張思考も含まれる。低いEffortではツール呼び出しの回数自体が減る。

## なぜOpus + Effort調整が良さそうか

1. Sonnetだけだと、Sonnetの週制限にひっかかる。
2. Opusのデフォルト(High Effort)だと、すぐrate limitになる。

だからOpusのEffortを`medium`や`low`に設定するのが良さそうというわけ。

公式ドキュメントの記載の感じ、コーディングタスクに`low`のメイン使用は考えられてなさそうなので、`medium`が良さそう。

必要に応じて`high`にする。

## Claude Codeでの設定

`/model`をした後、上下キーでモデル選択、「左右キーでEffort選択ができる。」(これがぼちぼち最近のアプデで追加された)

Happy Coding!