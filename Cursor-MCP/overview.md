# Cursor用MCP最適セットアップ（5本構成）

> **要約**：  
> Brave/GitHub/Figma/Serena/Exaの5本構成で、検索強化・コード品質向上・デザイン連携・Git運用を少数精鋭で実現。  
> 役割を厳密に分離することで、MCPの競合を避けつつ、開発フロー全体を効率化する最適構成。

---

## 📌 概要

このドキュメントでは、Cursorエディタで使用するMCP（Model Context Protocol）の最適な構成を提案します。**少数精鋭の5本構成**により、以下を同時に満たします：

- 🔍 **検索強化**：最新情報の即座な取得
- 💻 **コード品質向上**：安全な編集と構造理解
- 🎨 **デザイン連携**：FigmaとUIコードの整合性維持
- 🔧 **Git運用効率化**：PR/Issue操作の自動化

自動操作（RPA/ブラウザ操作）はCursor標準機能の成熟を待ち、現時点では導入を見送ります。

---

## 🎯 5本スタック（役割と導入意図）

| 種別 | MCP | ねらい / 効きどころ | 最低限の運用ポイント |
|---|---|---|---|
| **検索** | **Brave Search MCP** | 汎用Web検索の主力。ニュース/技術/APIドキュメント探索を高速化。 | APIキー管理。利用頻度が高いので**常時オン**にする価値あり。 |
| **Git** | **GitHub MCP** | PR/Issue/レビューを自然言語から操作。ブランチ運用の"日常オペ"を短縮。 | `toolsets` を絞ってノイズ/負荷を低減（例：`repos`,`pull_requests`）。 |
| **デザイン** | **Figma MCP** | 無料プラン前提でOK。デザイン→コードの文脈をCursorに供給して精度UP。 | デザイン資産の読み取り権限に注意。必要ファイルだけ共有。 |
| **コード解析** | **Serena** | LSPベースでシンボル操作。大規模コードの理解・局所修正・安全な置換に強い。 | 似た"コード解析系"を同居させないと発火率が安定。 |
| **コーディング支援** | **Exa MCP（exa‑code）** | コード検索/実装例/ベストプラクティスの即時参照で**エラー回避＆設計の裏付け**。 | **exa‑codeのみ**を有効化し、一般検索はBraveに任せる（役割分離）。 |

---

## 🧭 推奨ワークフロー（Claude 4.5 Sonnet前提）

1. **要件・方針を作る** → Brave で最新情報・仕様確認  
2. **ドラフト実装** → Claudeがコード生成  
3. **構造点検/安全編集** → Serena で参照範囲を把握しつつ変更  
4. **実装の裏取り** → Exa（exa‑code）で"正しい書き方/例"を提示  
5. **PR化＆レビュー** → GitHub MCPでPR作成・レビュー定型コメント  
6. **見た目/コンポーネント整合** → Figmaの情報を参照（トークン/コンポーネント名）

> **役割分離の原則**：Brave=汎用検索 / Exa=コード例の精度確保 / Serena=安全な編集 / Figma=UI文脈 / GitHub=最終反映

---

## ⚙️ `.cursor/mcp.json`（セットアップテンプレート）

### 方針：リモートMCP主体（URL）で軽量運用

### 1) リモートMCP版（URL接続）

```json
{
  "mcpServers": [
    { "name": "brave",  "url": "<BRAVE_MCP_URL>",  "apiKey": "${BRAVE_API_KEY}" },
    { "name": "github", "url": "<GITHUB_MCP_URL>", "toolsets": ["repos", "pull_requests"] },
    { "name": "figma",  "url": "<FIGMA_MCP_URL>",  "apiKey": "${FIGMA_TOKEN}" },
    { "name": "serena", "url": "<SERENA_MCP_URL>" },
    { "name": "exa",    "url": "<EXA_MCP_URL>",    "toolsets": ["exa-code"] }
  ]
}
```

> `<…_URL>` は各リポジトリ/配布元の案内に従って設定。`toolsets` は**役割を最小化**するための重要オプション。

### 2) ローカル起動版（command/args）

```json
{
  "mcpServers": [
    { "name": "brave",  "command": "npx", "args": ["mcp-brave", "start"],  "env": {"BRAVE_API_KEY": "${BRAVE_API_KEY}"} },
    { "name": "github", "command": "npx", "args": ["mcp-github", "start"], "env": {"GITHUB_TOKEN": "${GITHUB_TOKEN}"} },
    { "name": "figma",  "command": "npx", "args": ["mcp-figma", "start"],  "env": {"FIGMA_TOKEN": "${FIGMA_TOKEN}"} },
    { "name": "serena", "command": "serena-mcp", "args": [] },
    { "name": "exa",    "command": "npx", "args": ["mcp-exa", "start", "--tools", "exa-code"], "env": {"EXA_API_KEY": "${EXA_API_KEY}"} }
  ]
}
```

> `npx`での起動例はあくまで**一例**。実配布に合わせてコマンド名を置換してください。

---

## 🔧 セットアップ・運用Tips（最短）

- **APIキーは環境変数に隠す**：`~/.zshrc` に `export BRAVE_API_KEY=...` など。`mcp.json`には書かない。
- **GitHub MCPを軽量化**：最初は `repos` と `pull_requests` のみ。Issue運用が始まってから追加。
- **Serenaの発火率を上げる**：同系統ツールを同居させない／descriptionを短く用途特化／長文プロンプトで"どの範囲を編集するか"を明示。
- **Exaは"exa‑codeのみ"**：一般検索はBraveに任せ、役割が被らないようにする。
- **Figmaは無料プランで開始**：必要になったら権限とファイル数だけ拡張。まずはDev Mode情報（トークン/コンポーネント名）を取り込む流れに慣れる。

---

## 🛡 セキュリティ＆安定運用

- **最小権限**：GitHubトークンは必要スコープのみ。Figma/Brave/Exaも同様。
- **鍵ローテーション**：四半期ごとの更新を習慣化。
- **監査ログ**：PR作成や強制pushが走る操作は、通知（メール/Teams）を紐づけると安心。
- **プロジェクト分離**：この5本は**Global**、それ以外が必要なときは**プロジェクト別 `.cursor/mcp.json`**で追加。

---

## 🧪 よく使うプロンプト例

- **Brave**：`この機能の最新仕様/Breaking Changesを調べて。要点だけ3つ。`  
- **Exa（exa‑code）**：`Xを実装する最小コード例を3つ。言語はTypeScript、React v18前提、JSDoc付きで。`  
- **Serena**：`foo/bar.ts の関数doTaskの呼び出し箇所を列挙→型の不整合を直しつつ安全にrename。`  
- **GitHub**：`新規ブランチfeat/xを作成→変更点をコミット→PR作成。テンプレに沿って概要/影響範囲/テストを自動記入。`  
- **Figma**：`デザインのButton/Primaryのトークンとpadding/半径を取得→同名のUIコンポーネントへ反映案を出して。`

---

## 💡 重要なポイント

- **5本固定**：Brave / GitHub / Figma / Serena / Exa（exa‑code）
- **役割分離の徹底**：MCPの競合を避け、それぞれが専門領域で最大効果を発揮
- **段階的導入**：まずは検索（Brave）とコード解析（Serena）から始め、必要に応じて拡張

---

## 📝 まとめ

この5本構成により、少数精鋭でも**検索強化＋コード品質＋UI整合＋Git反映**が一気通貫で実現します。自動操作系MCPはCursor標準機能の成熟を待ち、現時点では導入を見送ることで、安定性と保守性を優先します。

---

**調査日**: 2025-10-04  
**調査者**: チームメンバー  
**使用ツール**: ChatGPT / 各種MCP公式ドキュメント

