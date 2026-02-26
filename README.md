# Zenn CLI

Zenn のコンテンツを管理するための CLI ツール。

- [📘 公式ガイド](https://zenn.dev/zenn/articles/zenn-cli-guide)

## セットアップ

```bash
npm install zenn-cli
npx zenn init
```

## プレビュー

```bash
npx zenn preview
```

`localhost:8000` でプレビューが起動する。ポート変更も可能：

```bash
npx zenn preview --port 3000
```

## 記事（Article）の管理

### ディレクトリ構成

```
.
└─ articles
   ├── example-article1.md
   └── example-article2.md
```

### 記事の作成

```bash
npx zenn new:article
```

オプション付き：

```bash
npx zenn new:article --slug article-slug --title "タイトル" --type tech --emoji ✨
```

- **slug**: 12〜50文字、`a-z0-9`・ハイフン・アンダースコアのみ

### Frontmatter

```yaml
---
title: ""
emoji: "😸"
type: "tech"  # "tech" または "idea"
topics: []    # タグ（最大5つ）
published: true
---
```

### 公開日時の指定

```yaml
published: true
published_at: 2050-06-12 09:03  # YYYY-MM-DD or YYYY-MM-DD hh:mm（JST）
```

### 記事の公開・更新

`published: true` に設定し、GitHub リポジトリに push する。連携ブランチへの push で自動デプロイされる。

コミットメッセージに `[ci skip]` または `[skip ci]` を含めるとデプロイをスキップできる。

### 記事の削除

ダッシュボードから行う。リポジトリからファイルを削除しても zenn.dev 上の記事は削除されない。

## 本（Book）の管理

### ディレクトリ構成

```
.
└─ books
   └── my-awesome-book
       ├── config.yaml
       ├── cover.png       # カバー画像（500×700px 推奨）
       ├── chapter1.md
       ├── chapter2.md
       └── chapter3.md
```

### 本の作成

```bash
npx zenn new:book
npx zenn new:book --slug book-slug
```

- **slug**: 12〜50文字、`a-z0-9`・ハイフン・アンダースコアのみ

### config.yaml

```yaml
title: "本のタイトル"
summary: "本の紹介文"
topics: ["markdown", "zenn", "react"]  # 最大5つ
published: true
price: 0          # 無料: 0 / 有料: 200〜5000（100円刻み）
toc_depth: 0      # 目次の深さ（0〜3）
chapters:
  - chapter1
  - chapter2
  - chapter3
```

`chapters` で並び順を指定する。記載されていないチャプターは同期されない。

### チャプターファイル

```yaml
---
title: "チャプターのタイトル"
free: true  # 有料本で無料公開するチャプターに指定
---
ここからチャプター本文
```

- ファイル名: `a-z0-9`・ハイフン・アンダースコア（1〜50文字）+ `.md`
- 最大チャプター数: **100**

### ファイル名で並び順を管理する方法

```
books/my-awesome-book/
├── config.yaml
├── 1.intro.md
├── 2.foo.md
└── 3.bar.md
```

この場合 `config.yaml` の `chapters` は空にする。

### 本の公開・更新・削除

記事と同様、push で公開・更新。削除はダッシュボードから行う。

## 画像の挿入

1. Zenn のアップロードページ（要ログイン）
2. GitHub リポジトリに配置
3. 外部サービス（Gyazo 等）のリンク
