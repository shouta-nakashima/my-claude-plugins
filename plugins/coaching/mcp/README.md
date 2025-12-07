# Coaching MCP Server セットアップガイド

Claude Desktop（無料版含む）でコーチングプロンプトを使うためのMCPサーバーです。
一度設定すれば、毎回コピペ不要でコーチングセッションを開始できます。

## MCP（Model Context Protocol）とは？

MCPは、Claude Desktopに追加機能を提供するための仕組みです。
このサーバーを設定すると、コーチングプロンプトをいつでも呼び出せるようになります。

## 前提条件

以下がインストールされている必要があります：

| ソフトウェア | 確認コマンド | インストール方法 |
|-------------|-------------|-----------------|
| Python 3.10以上 | `python --version` | [python.org](https://www.python.org/downloads/) |
| Git | `git --version` | [git-scm.com](https://git-scm.com/downloads) |
| Claude Desktop | - | [claude.ai/download](https://claude.ai/download) |

## セットアップ手順

### Step 1: リポジトリをダウンロード

ターミナル（macOS）またはコマンドプロンプト（Windows）を開き、以下を実行：

```bash
# ホームディレクトリに移動（任意の場所でOK）
cd ~

# リポジトリをクローン
git clone https://github.com/shouta-nakashima/my-claude-plugins.git
```

ダウンロードが完了すると `my-claude-plugins` フォルダが作成されます。

### Step 2: 依存関係をインストール

```bash
# mcpフォルダに移動
cd my-claude-plugins/plugins/coaching/mcp

# 必要なライブラリをインストール
pip install -r requirements.txt
```

> **うまくいかない場合**: `pip3 install -r requirements.txt` を試してください

### Step 3: server.py のパスを確認

次のステップで必要になるため、`server.py` の絶対パスをコピーしておきます。

**macOS/Linux:**
```bash
# 現在のパスを表示
pwd
# 例: /Users/yourname/my-claude-plugins/plugins/coaching/mcp
```

フルパスは `/Users/yourname/my-claude-plugins/plugins/coaching/mcp/server.py` になります。

**Windows:**
```bash
# 現在のパスを表示
cd
# 例: C:\Users\yourname\my-claude-plugins\plugins\coaching\mcp
```

フルパスは `C:\Users\yourname\my-claude-plugins\plugins\coaching\mcp\server.py` になります。

### Step 4: Claude Desktop の設定ファイルを編集

Claude Desktopの設定ファイルを開きます。

**macOS:**
```bash
# Finderで開く
open ~/Library/Application\ Support/Claude/
```
`claude_desktop_config.json` をテキストエディタで開きます。

**Windows:**
1. `Win + R` キーを押す
2. `%APPDATA%\Claude` と入力してEnter
3. `claude_desktop_config.json` をメモ帳で開く

### Step 5: 設定を追加

ファイルの内容を以下のように編集します。

**初めてMCPを設定する場合（ファイルが空または存在しない）:**

macOS/Linuxの場合:
```json
{
  "mcpServers": {
    "coaching": {
      "command": "python3",
      "args": ["/Users/yourname/my-claude-plugins/plugins/coaching/mcp/server.py"]
    }
  }
}
```

Windowsの場合:
```json
{
  "mcpServers": {
    "coaching": {
      "command": "python",
      "args": ["C:\\Users\\yourname\\my-claude-plugins\\plugins\\coaching\\mcp\\server.py"]
    }
  }
}
```

> **重要**: `/Users/yourname/...` の部分は、Step 3で確認した実際のパスに置き換えてください。
> Windowsの場合、パスの `\` は `\\` に変換してください。

**すでに他のMCPサーバーがある場合:**

既存の `mcpServers` の中に追加します：

```json
{
  "mcpServers": {
    "既存のサーバー": {
      ...
    },
    "coaching": {
      "command": "python3",
      "args": ["/Users/yourname/my-claude-plugins/plugins/coaching/mcp/server.py"]
    }
  }
}
```

### Step 6: Claude Desktopを再起動

1. Claude Desktopを完全に終了
   - macOS: メニューバーのClaudeアイコンを右クリック →「終了」
   - Windows: タスクトレイのClaudeアイコンを右クリック →「終了」
2. Claude Desktopを再度起動

## 使い方

### プロンプトの呼び出し方

1. Claude Desktopで新しいチャットを開く
2. 入力欄の左にある **「+」ボタン** をクリック
3. **「MCP Server からプロンプトを追加」** を選択
4. **「coaching」** サーバーから使いたいプロンプトを選択

### 利用可能なプロンプト

| プロンプト | 説明 | おすすめの場面 |
|-----------|------|---------------|
| `coaching` | 自動選択モード | テーマが決まっていないとき |
| `coaching_grow` | GROWモデル固定 | 目標達成したいとき |
| `coaching_oskar` | OSKARモデル固定 | 数値目標があるとき |
| `coaching_free` | 自由対話モード | モヤモヤを整理したいとき |

## トラブルシューティング

### 「coaching」サーバーが表示されない

1. **設定ファイルのJSON形式を確認**
   - カンマの位置、括弧の対応が正しいか確認
   - [JSONLint](https://jsonlint.com/) で検証できます

2. **Pythonのパスを確認**
   ```bash
   which python3  # macOS/Linux
   where python   # Windows
   ```
   表示されたパスを `command` に設定してみてください

3. **server.py のパスを確認**
   - パスにスペースや日本語が含まれていないか確認
   - 絶対パスを使用しているか確認

### エラーが出る

Claude Desktopの開発者ツールでログを確認できます：
- macOS: `Cmd + Option + I`
- Windows: `Ctrl + Shift + I`

「Console」タブでエラーメッセージを確認してください。

## ファイル構成

```
mcp/
├── README.md          # このファイル
├── server.py          # MCPサーバー本体
└── requirements.txt   # 依存関係
```
