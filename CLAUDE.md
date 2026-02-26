# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

Zenn CLI content repository for publishing articles and books to zenn.dev. Content is written in Markdown and deployed automatically via GitHub integration on push.

## Commands

```bash
npx zenn preview          # Local preview at localhost:8000
npx zenn new:article      # Create new article (options: --slug, --title, --type, --emoji)
npx zenn new:book         # Create new book (options: --slug)
```

## Content Structure

- `articles/*.md` 個別の記事ファイル。YAMLフロントマター付き
- `books/<slug>/` 本のディレクトリ。`config.yaml`、チャプター`.md`ファイル、`cover.png`を含む
- `images/<article-slug>/` 記事固有の画像。`/images/<article-slug>/<file>`で参照

## Article Conventions

- フロントマターのフィールド: `title`, `emoji`(1文字), `type`(`tech` or `idea`), `topics`(最大5), `published`(boolean)
- Slug: 12-50文字、`a-z0-9`とハイフン/アンダースコア
- 言語: 日本語で執筆
- 画像: `images/<article-slug>/`に配置し`/images/<article-slug>/<filename>`で参照
- 公開日時指定: フロントマターで`published_at: YYYY-MM-DD hh:mm`(JST)
- 削除はzenn.devのダッシュボードから行う。リポジトリからファイルを削除しても公開記事は削除されない

## Writing Style

- Markdownの強調構文(`**太字**`、`*斜体*`)は使用しない
- ダブルクオーテーション(")は使用しない(ただしFront MatterのYAML値は公式ルールに従いダブルクオーテーションで囲む)
- コロン(:)、セミコロン(;)は使用しない
- カギカッコ(「」)による強調はしない
- emダッシュ(—)は使用しない
