---
description: "GitHub PRを作成（タイトル自動生成、ドラフト対応）"
---

# Create PR

以下の手順でPRを作成してください：

## 0. 事前チェック

以下のコマンドを実行して環境を確認：

### GitHub CLI の確認

`gh --version` を実行。

**インストールされていない場合**、以下のメッセージを表示して処理を中断：

---

**GitHub CLI (`gh`) がインストールされていません。**

PR作成には GitHub CLI が必要です。以下の方法でインストールしてください：

**macOS (Homebrew):**
```bash
brew install gh
```

**Ubuntu/Debian:**
```bash
sudo apt install gh
```

**Windows (winget):**
```bash
winget install GitHub.cli
```

インストール後、以下で認証を行ってください：
```bash
gh auth login
```

詳細: https://cli.github.com/

---

### 認証状態の確認

`gh auth status` を実行。

**未認証の場合**、以下のメッセージを表示して処理を中断：

---

**GitHub CLI の認証が必要です。**

以下のコマンドで認証してください：
```bash
gh auth login
```

---

## 1. 現在の状態を確認

以下のコマンドを並列で実行：
- `git branch --show-current` で現在のブランチ名を取得
- `git log main..HEAD --oneline` でコミット一覧を取得
- `git diff main...HEAD --stat` で変更ファイル一覧を取得
- `git diff main...HEAD` で差分の詳細を取得
- `ls .github/PULL_REQUEST_TEMPLATE.md 2>/dev/null` でテンプレート有無を確認

## 2. ブランチ確認

- mainブランチで実行された場合はエラー：「mainブランチではPRを作成できません。作業ブランチに切り替えてください。」
- コミットがない場合はエラー：「mainブランチとの差分がありません。変更をコミットしてから再度実行してください。」

## 3. PRタイトルの決定

AskUserQuestion ツールで確認：
- 質問：「PRタイトルを入力してください（空欄で自動生成）」
- テキスト入力を受け付ける

### ユーザーが入力した場合
そのまま使用

### 空欄の場合（自動生成）
以下のロジックで生成：
1. ブランチ名からプレフィックスを除去（`feature/`, `fix/`, `hotfix/`, `refactor/`, `docs/`, `chore/` など）
2. kebab-case を自然な文に変換
3. Claudeに指定された言語で生成

#### 自動生成例
- `feature/add-user-auth` → "ユーザー認証機能を追加"
- `fix/login-error` → "ログインエラーを修正"
- `refactor/api-client` → "APIクライアントをリファクタリング"

## 4. PR説明文の生成

Claudeに指定された言語で以下の形式で生成：

### テンプレートがある場合
`.github/PULL_REQUEST_TEMPLATE.md` の形式に従って内容を埋める

### テンプレートがない場合

```markdown
## 概要

[変更内容のサマリー（差分から自動生成、2-3文で簡潔に）]

## 変更内容

- [主要な変更点を箇条書き]

## コミット一覧

- [コミットメッセージ一覧]

## 変更ファイル

- [ファイル一覧]
```

## 5. ドラフト確認

AskUserQuestion ツールで確認：
- 質問：「ドラフトPRとして作成しますか？」
- 選択肢：
  - 「通常のPRとして作成」
  - 「ドラフトPRとして作成」

## 6. リモートへプッシュ

`git push -u origin <branch>` を実行。

すでにリモートブランチが存在する場合は `git push` のみ実行。

## 7. PR作成

`gh pr create` コマンドを実行：

```bash
gh pr create --base main --title "<タイトル>" --body "<説明文>" [--draft]
```

- ドラフトPRの場合は `--draft` フラグを追加

## 8. 結果表示

以下の情報を表示：
- 作成されたPRのURL
- PRタイトル
- ドラフト/通常の区別
