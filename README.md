# Research Hub 🔍

**AI調査共有ハブ** - ChatGPT/Gemini調査結果をMarkdownで整理・共有するリポジトリ

## 📚 このリポジトリの目的

3人チームがChatGPTやGeminiで調べた内容をMarkdown形式で共有・整理し、知見を蓄積していくためのハブです。

## 🎯 運用ルール

### フォルダ追加運用

* **テーマが決まったら自分でフォルダを追加していく運用**
* 各テーマは `/topic-name/overview.md` から始める
* 例：`/RPA` や `/Cursor` のようにフォルダを作成していく

### 記事作成ガイドライン

* **1ファイル1テーマ** を原則とする
* **先頭3行で要約** を記載する
* **週次でREADMEにまとめを追加** して全体像を維持する

### テンプレート活用

新しいテーマを追加する際は、`templates/new_topic_template.md` を参考にしてください。

## 📂 リポジトリ構成

```
research-hub/
├─ README.md                     # このファイル
├─ templates/                    # テンプレート集
│  └─ new_topic_template.md     # 新規テーマ用テンプレート
├─ examples/                     # 記事例
│  └─ sample_topic/
│     └─ overview.md            # サンプル記事
├─ docs/                         # GitHub Pages用ドキュメント
│  ├─ index.md                  # トップページ
│  └─ _config.yml               # Just the Docs設定
└─ .gitignore
```

## 🚀 使い方

### 1. 新しいテーマを追加する

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

### 3. GitHub Pagesで確認

公開URLにアクセスして、左サイドバーに新しいテーマが自動追加されていることを確認

## 📋 現在の調査テーマ

### 進行中

* （週次更新：調査中のテーマをここにリストアップ）

### 完了

* **Cursor用MCP最適セットアップ** (2025-10-04)
  * Brave/GitHub/Figma/Serena/Exaの5本構成で検索強化・コード品質向上・デザイン連携を実現
  * 少数精鋭での運用方針と具体的なセットアップ手順を整理

## 👥 コントリビューター

* メンバー1
* メンバー2
* メンバー3

## 📝 ライセンス

MIT License - チーム内での自由な利用と共有を目的としています

---

**Last Updated**: 2025-10-04

