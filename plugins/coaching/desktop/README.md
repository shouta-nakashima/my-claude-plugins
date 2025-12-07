# Coaching for Claude Desktop

Claude Desktop の Skills 機能を使ってコーチングを利用する方法です。

> **注意**: Skills は Claude **Pro/Team/Max/Enterprise** プランで利用可能です。
> 無料版をお使いの方は [MCP Server](../mcp/) をご利用ください。

## セットアップ手順

### Step 1: スキルをダウンロード

以下のリンクからZIPファイルをダウンロード：

**[coaching-skill.zip をダウンロード](https://github.com/shouta-nakashima/my-claude-plugins/raw/main/plugins/coaching/desktop/coaching-skill.zip)**

### Step 2: スキルをアップロード

1. Claude Desktop を開く
2. **Settings**（設定）を開く
3. **Capabilities**（機能）をクリック
4. **Skills** セクションまでスクロール
5. **「Upload skill」** をクリック
6. ダウンロードした `coaching-skill.zip` を選択

### Step 3: 使用開始

どのチャットでも、以下のように話しかけるとスキルが自動で発動します：

- 「コーチングして」
- 「相談に乗って」
- 「考えを整理したい」
- 「目標を決めたい」

## ファイル構成

```
desktop/
├── README.md              # このファイル
├── coaching-skill.zip     # アップロード用ZIP
└── coaching-skill/
    └── SKILL.md           # スキル定義
```

## 関連リンク

- [メインREADME](../README.md) - プラグイン全体の説明
- [MCP Server](../mcp/) - 無料版向けセットアップ
- [Using Skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude) - 公式ドキュメント
