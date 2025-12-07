# Coaching for Claude Desktop (Pro/Team/Max)

Claude Desktop の Project 機能を使って、コーチングプロンプトを設定する方法です。

> **注意**: この方法は Claude Pro/Team/Max プランが必要です。
> 無料版をお使いの方は [MCP Server](../mcp/) をご利用ください。

## セットアップ手順

### Step 1: プロンプトファイルをダウンロード

以下のリンクからダウンロード：

**[coaching-prompt.md をダウンロード](https://raw.githubusercontent.com/shouta-nakashima/my-claude-plugins/main/plugins/coaching/desktop/coaching-prompt.md)**

### Step 2: Project を作成

1. Claude Desktop を開く
2. 左サイドバーの **「Projects」** をクリック
3. **「New Project」** をクリック
4. プロジェクト名を入力（例：「コーチング」）

### Step 3: Project Knowledge に追加

1. 作成したプロジェクトを開く
2. **「Project Knowledge」** セクションを見つける
3. ダウンロードした `coaching-prompt.md` をドラッグ&ドロップ

### Step 4: 使用開始

プロジェクト内で新しいチャットを開始し、以下のように話しかけてください：

- 「コーチングして」
- 「相談に乗って」
- 「考えを整理したい」

## Custom Instructions（オプション）

より確実にコーチングモードで動作させたい場合は、Project の Custom Instructions に以下を設定：

```
Project Knowledgeにあるコーチングプロンプトに従って対話してください。
```

## ファイル構成

```
desktop/
├── README.md              # このファイル
└── coaching-prompt.md     # コーチングプロンプト本体
```

## 関連リンク

- [メインREADME](../README.md) - プラグイン全体の説明
- [MCP Server](../mcp/) - 無料版向けセットアップ
