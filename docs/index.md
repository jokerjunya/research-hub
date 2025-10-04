---
layout: default
title: Home
nav_order: 1
description: "AI調査共有ハブ - ChatGPT/Gemini調査結果をMarkdownで整理・共有"
permalink: /
---

# Research Hub 🔍
{: .fs-9 }

AI調査共有ハブ - ChatGPT/Gemini調査結果をMarkdownで整理・共有するサイトです
{: .fs-6 .fw-300 }

[GitHub リポジトリを見る](https://github.com/jokerjunya/research-hub){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[テンプレートを使う](https://github.com/jokerjunya/research-hub/blob/main/templates/new_topic_template.md){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## このサイトについて

このサイトは、3人チームがChatGPTやGeminiで調べた内容をMarkdown形式で共有・整理し、知見を蓄積していくためのハブです。

### 主な特徴

- **テーマごとにフォルダ管理**: `/RPA`、`/Cursor` のように自由にフォルダを追加
- **自動ナビゲーション生成**: 左のサイドバーにフォルダを追加すると自動で反映
- **テンプレート活用**: 統一フォーマットで記事を作成
- **GitHub Pages**: 常に最新の状態が公開される

## 使い方

### 1. 新しいテーマを追加
左のサイドバーにフォルダを追加していくことで、自動でナビゲーションに反映されます。

```bash
# 例：RPAについて調査する場合
mkdir RPA
cp templates/new_topic_template.md RPA/overview.md
# RPA/overview.md を編集
```

### 2. ファイルをコミット
```bash
git add RPA/
git commit -m "feat: add RPA research overview"
git push origin main
```

### 3. 自動公開
GitHub Actionsにより自動的にこのサイトに反映されます（数分程度）。

## 記事作成ガイドライン

- **1ファイル1テーマ** を原則とする
- **先頭3行で要約** を記載する
- **週次でREADMEにまとめを追加** して全体像を維持する

## テンプレート

新しいテーマを追加する際は、[テンプレート](https://github.com/jokerjunya/research-hub/blob/main/templates/new_topic_template.md)を参考にしてください。

---

## 最近の更新

- **2025-10-04**: リポジトリ初期セットアップ
- （週次更新）

## コントリビューター

- メンバー1
- メンバー2  
- メンバー3

---

**このサイトはJust the Docsテーマを使用しています**

