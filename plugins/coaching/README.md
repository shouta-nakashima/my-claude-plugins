# Coaching Plugin

対話型AIコーチングプラグイン。GROW/OSKARモデルを活用し、目標達成・意思決定・内省をサポートします。

## 特徴

- **対話型**: コマンド1つで自然な対話セッションを開始
- **自動選択**: テーマに応じて最適なコーチングフレームワークを自動選択
- **引き出す**: 答えを教えるのではなく、あなた自身の答えを引き出す

## インストール

```bash
/plugin install coaching@my-claude-plugins
```

## 使い方

### コマンドで開始

```
/coaching
```

### 自然言語で開始

以下のような発話でもセッションが始まります：

- 「コーチングして」
- 「相談に乗って」
- 「考えを整理したい」
- 「目標を決めたい」

## 対応テーマ

| テーマ | 例 |
|--------|-----|
| 目標達成 | 「副業を始めたい」「資格を取りたい」 |
| キャリア | 「転職を考えている」「キャリアチェンジしたい」 |
| 意思決定 | 「AかBか迷っている」「決断できない」 |
| 内省・整理 | 「モヤモヤを整理したい」「自分を理解したい」 |

## 使用フレームワーク

### GROWモデル
目標達成に最適なフレームワーク。

| ステップ | 内容 |
|----------|------|
| **G**oal | 達成したい目標を明確化 |
| **R**eality | 現在の状況を把握 |
| **O**ptions | 可能な選択肢を洗い出す |
| **W**ill | 具体的な行動を決定 |

### OSKARモデル
進捗を数値化しながら進めるフレームワーク。

| ステップ | 内容 |
|----------|------|
| **O**utcome | 成果目標を決める |
| **S**caling | 現状を10点満点で数値化 |
| **K**now-how | 必要なスキル・知識を特定 |
| **A**ffirm & Action | 強みを認め行動を決定 |
| **R**eview | 振り返りのタイミングを設定 |

### 自由対話
モヤモヤや気持ちの整理に最適。構造化せず、寄り添いながら対話を進めます。

## セッション例

```
ユーザー: /coaching

AI: こんにちは。今日はどんなことについて話しましょうか？

ユーザー: 新しいプロジェクトを任されたけど、うまくやれるか不安で...

AI: 新しいプロジェクトを任されたんですね。
    期待と不安、両方あるのは自然なことです。

    まず教えてください。
    このプロジェクトが「うまくいった」と言える状態は、どんな状態ですか？

ユーザー: チームがまとまって、期日通りにリリースできること。

AI: チームのまとまりと期日遵守、2つのポイントがあるんですね。
    今の段階で、それぞれどのくらい手応えがありますか？

（対話が続く...）

AI: 今日話したことを整理させてください。

    【テーマ】
    新プロジェクトへの不安

    【気づき・決めたこと】
    - 不安の正体は「チームビルディング」だった
    - まずは1on1でメンバーの状況を把握する

    【次のアクション】
    - 来週中に全メンバーと15分ずつ1on1を実施

    応援しています！
```

## Claude Desktop で使う

Claude Desktop（Pro/Team/Max）でも同じコーチング体験ができます。

### セットアップ手順

1. 以下のファイルをダウンロード：

   **[coaching-prompt.md をダウンロード](https://raw.githubusercontent.com/shouta-nakashima/my-claude-plugins/main/plugins/coaching/desktop/coaching-prompt.md)**

2. Claude Desktopで新しい **Project** を作成

3. **Project Knowledge** にダウンロードしたファイルをドラッグ&ドロップ

4. 「コーチングして」と話しかけるとセッション開始

### Custom Instructions（オプション）

より短い指示で済ませたい場合は、ProjectのCustom Instructionsに以下を設定：

```
Project Knowledgeにあるコーチングプロンプトに従って対話してください。
```

## MCP Server として使う（無料版対応）

ローカルにクローンしてMCPサーバーとして起動すれば、**無料版でも毎回コピペ不要**で使えます。

### MCP（Model Context Protocol）とは？

MCPは、Claude Desktopに追加機能を提供するための仕組みです。
一度設定すれば、コーチングプロンプトをいつでも呼び出せるようになります。

### 前提条件

以下がインストールされている必要があります：

| ソフトウェア | 確認コマンド | インストール方法 |
|-------------|-------------|-----------------|
| Python 3.10以上 | `python --version` | [python.org](https://www.python.org/downloads/) |
| Git | `git --version` | [git-scm.com](https://git-scm.com/downloads) |
| Claude Desktop | - | [claude.ai/download](https://claude.ai/download) |

### セットアップ手順

#### Step 1: リポジトリをダウンロード

ターミナル（macOS）またはコマンドプロンプト（Windows）を開き、以下を実行：

```bash
# ホームディレクトリに移動（任意の場所でOK）
cd ~

# リポジトリをクローン
git clone https://github.com/shouta-nakashima/my-claude-plugins.git
```

ダウンロードが完了すると `my-claude-plugins` フォルダが作成されます。

#### Step 2: 依存関係をインストール

```bash
# mcpフォルダに移動
cd my-claude-plugins/plugins/coaching/mcp

# 必要なライブラリをインストール
pip install -r requirements.txt
```

> **うまくいかない場合**: `pip3 install -r requirements.txt` を試してください

#### Step 3: server.py のパスを確認

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

#### Step 4: Claude Desktop の設定ファイルを編集

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

#### Step 5: 設定を追加

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

#### Step 6: Claude Desktopを再起動

1. Claude Desktopを完全に終了
   - macOS: メニューバーのClaudeアイコンを右クリック →「終了」
   - Windows: タスクトレイのClaudeアイコンを右クリック →「終了」
2. Claude Desktopを再度起動

### 使い方

#### プロンプトの呼び出し方

1. Claude Desktopで新しいチャットを開く
2. 入力欄の左にある **「+」ボタン** をクリック
3. **「MCP Server からプロンプトを追加」** を選択
4. **「coaching」** サーバーから使いたいプロンプトを選択

#### 利用可能なプロンプト

| プロンプト | 説明 | おすすめの場面 |
|-----------|------|---------------|
| `coaching` | 自動選択モード | テーマが決まっていないとき |
| `coaching_grow` | GROWモデル固定 | 目標達成したいとき |
| `coaching_oskar` | OSKARモデル固定 | 数値目標があるとき |
| `coaching_free` | 自由対話モード | モヤモヤを整理したいとき |

### トラブルシューティング

#### 「coaching」サーバーが表示されない

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

#### エラーが出る

Claude Desktopの開発者ツールでログを確認できます：
- macOS: `Cmd + Option + I`
- Windows: `Ctrl + Shift + I`

「Console」タブでエラーメッセージを確認してください。

## 注意事項

- コーチングは「アドバイス」ではなく「引き出し」のアプローチです
- 専門的な医療・法律・財務のアドバイスはできません
- 深刻な悩みの場合は、専門家への相談をおすすめすることがあります

## ライセンス

MIT
