# Research Hub 🔍

**AI調査共有ハブ** - ChatGPT/Gemini調査結果をMarkdownで整理・共有するリポジトリ

## 📚 このリポジトリの目的

3人チームがChatGPTやGeminiで調べた内容をMarkdown形式で共有・整理し、知見を蓄積していくためのハブです。

## 🎯 運用ルール

### フォルダ追加運用
- **テーマが決まったら自分でフォルダを追加していく運用**
- 各テーマは `/topic-name/overview.md` から始める
- 例：`/RPA` や `/Cursor` のようにフォルダを作成していく

### 記事作成ガイドライン
- **1ファイル1テーマ** を原則とする
- **先頭3行で要約** を記載する
- **週次でREADMEにまとめを追加** して全体像を維持する

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

## 🌐 GitHub Pages公開設定

### 設定手順
1. リポジトリの **Settings** タブに移動
2. 左サイドバーから **Pages** を選択
3. **Source** セクションで以下を設定：
   - **Deploy from a branch** を選択
   - **Branch**: `main` / `/docs` を選択
   - **Save** ボタンをクリック
4. 数分後、公開URLが表示されます

### 公開URL
```
https://jokerjunya.github.io/research-hub/
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
- （週次更新：調査中のテーマをここにリストアップ）

### 完了
- （週次更新：完了した調査をここにリストアップ）

## 👥 コントリビューター

- メンバー1
- メンバー2
- メンバー3

## 📝 ライセンス

MIT License - チーム内での自由な利用と共有を目的としています

---

**Last Updated**: 2025-10-04

