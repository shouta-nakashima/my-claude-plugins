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

### セットアップ手順

1. リポジトリをクローン：

```bash
git clone https://github.com/shouta-nakashima/my-claude-plugins.git
cd my-claude-plugins/plugins/coaching/mcp
```

2. 依存関係をインストール：

```bash
pip install -r requirements.txt
```

3. Claude Desktop の設定ファイルを編集：

**macOS**: `~/Library/Application Support/Claude/claude_desktop_config.json`
**Windows**: `%APPDATA%\Claude\claude_desktop_config.json`

```json
{
  "mcpServers": {
    "coaching": {
      "command": "python",
      "args": ["/path/to/my-claude-plugins/plugins/coaching/mcp/server.py"]
    }
  }
}
```

4. Claude Desktopを再起動

### 使い方

MCPサーバーが起動すると、以下のプロンプトが利用可能になります：

| プロンプト | 説明 |
|-----------|------|
| `coaching` | 自動選択モード（テーマに応じてフレームワークを選択） |
| `coaching_grow` | GROWモデルで固定 |
| `coaching_oskar` | OSKARモデルで固定 |
| `coaching_free` | 自由対話モードで固定 |

Claude Desktopで「+」→「MCP Server」→「coaching」から選択できます。

## 注意事項

- コーチングは「アドバイス」ではなく「引き出し」のアプローチです
- 専門的な医療・法律・財務のアドバイスはできません
- 深刻な悩みの場合は、専門家への相談をおすすめすることがあります

## ライセンス

MIT
