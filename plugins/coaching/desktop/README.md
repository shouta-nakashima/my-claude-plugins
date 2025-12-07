# Coaching for Claude Desktop

Claude Desktop でコーチングを使う方法は2つあります。

> **注意**: どちらの方法も Claude **Pro/Team/Max** プランが必要です。
> 無料版をお使いの方は [MCP Server](../mcp/) をご利用ください。

## 方法の比較

| 方法 | 特徴 | おすすめの人 |
|------|------|-------------|
| **Skills（推奨）** | 自動で発動、全チャットで使える | 手軽に使いたい人 |
| **Project Knowledge** | プロジェクト内限定 | 他の資料と組み合わせたい人 |

---

## 方法1: Skills を使う（推奨）

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

---

## 方法2: Project Knowledge を使う

プロジェクト単位でコーチングを使いたい場合はこちら。

### Step 1: プロンプトファイルをダウンロード

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

プロジェクト内で新しいチャットを開始し、「コーチングして」と話しかけてください。

### Custom Instructions（オプション）

より確実にコーチングモードで動作させたい場合：

```
Project Knowledgeにあるコーチングプロンプトに従って対話してください。
```

---

## ファイル構成

```
desktop/
├── README.md              # このファイル
├── coaching-skill.zip     # Skills用（方法1）
├── coaching-skill/
│   └── SKILL.md           # スキル定義
└── coaching-prompt.md     # Project Knowledge用（方法2）
```

## 関連リンク

- [メインREADME](../README.md) - プラグイン全体の説明
- [MCP Server](../mcp/) - 無料版向けセットアップ
- [Using Skills in Claude](https://support.claude.com/en/articles/12512180-using-skills-in-claude) - 公式ドキュメント
