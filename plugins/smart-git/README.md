# Smart Git

コミットとPR作成を効率化するGit操作プラグインです。Conventional Commits形式のコミットメッセージ自動生成とGitHub PR作成をサポートします。

## 概要

Gitでの日常的な操作を効率化します：
- ブランチ名と変更内容からConventional Commits形式のコミットメッセージを自動生成
- GitHub PRをコマンド一発で作成
- コミットからPR作成までを一括実行

## 機能

### コマンド

| コマンド | 説明 |
|----------|------|
| `/smart-git:commit` | Conventional Commits形式でコミット |
| `/smart-git:create-pr` | GitHub PRを作成 |
| `/smart-git:commit-and-pr` | コミット → プッシュ → PR作成を一括実行 |

### スキル

「PRを作成して」「プルリクエストを作って」などの自然言語でPR作成が可能。変更がある場合は自動でコミットするか確認します。

## 前提条件

PR作成機能には以下が必要です：

### GitHub CLI (`gh`)

**macOS:**
```bash
brew install gh
```

**Ubuntu/Debian:**
```bash
sudo apt install gh
```

**Windows:**
```bash
winget install GitHub.cli
```

### 認証

```bash
gh auth login
```

## インストール

```bash
# マーケットプレイスを追加（初回のみ）
/plugin marketplace add https://github.com/shouta-nakashima/my-claude-plugins

# プラグインをインストール
/plugin install smart-git@my-claude-plugins
```

## 使い方

### コミット

```bash
/smart-git:commit
```

1. 現在のブランチ名と変更内容を取得
2. ステージング状態を確認（未ステージングがあれば確認）
3. Conventional Commits形式のメッセージを自動生成
4. コミット実行

### PR作成

```bash
/smart-git:create-pr
```

1. mainブランチとの差分を確認
2. PRタイトルを入力（空欄で自動生成）
3. PR説明文を自動生成
4. ドラフトPRにするか確認
5. プッシュしてPR作成

### コミット＋PR作成

```bash
/smart-git:commit-and-pr
```

コミットからPR作成まで一括で実行します。

### 自然言語でPR作成

「PRを作成して」と伝えるだけでOK。変更がある場合は自動でコミットするか確認します。

## サポートされるプレフィックス

| プレフィックス | 用途 | ブランチ名の例 |
|--------------|------|---------------|
| `feat:` | 新機能の追加 | `feature/`, `feat/` |
| `fix:` | バグ修正 | `fix/`, `bugfix/`, `hotfix/` |
| `refactor:` | リファクタリング | `refactor/` |
| `docs:` | ドキュメントのみの変更 | - |
| `style:` | コードフォーマット | - |
| `test:` | テストの追加・修正 | - |
| `chore:` | ビルド・ツール関連 | - |
| `perf:` | パフォーマンス改善 | - |

## 実行例

### コミット

```
ブランチ: feature/user-authentication
変更内容: ユーザー認証機能を実装

生成されるメッセージ:
feat: add user authentication feature
```

### PR作成

```
ブランチ: feature/add-login
タイトル: ログイン機能を追加（自動生成）
ドラフト: いいえ

→ PR URL: https://github.com/user/repo/pull/123
```

## 利点

- **時間短縮**: コミットメッセージやPR説明文を考える時間を削減
- **一貫性**: プロジェクト全体で統一されたフォーマット
- **効率的**: コミットからPR作成までをワンコマンドで完了
- **柔軟**: タイトルの手動入力やドラフトPRにも対応

## Conventional Commitsについて

コミットメッセージに人間と機械が読みやすい意味を持たせるための仕様です。

詳細: https://www.conventionalcommits.org/

## 注意事項

- PR作成には GitHub CLI (`gh`) のインストールと認証が必要です
- ベースブランチは `main` 固定です
- コミットメッセージは英語で生成されます（Conventional Commits準拠）
- PRタイトルと説明文はClaudeに指定された言語で生成されます

## ライセンス

MIT

## 作者

shouta-nakashima
