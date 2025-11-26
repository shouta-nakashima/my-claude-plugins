# Smart Commit

ブランチ名と変更内容から適切なConventional Commits形式のコミットメッセージを自動生成し、コミットを実行するClaude Codeプラグインです。

## 概要

Git コミット時に、ブランチ名（例: `feature/user-auth`）と変更内容を分析して、適切なプレフィックス（`feat:`, `fix:` など）を含むConventional Commits形式のメッセージを自動生成します。

## 機能

- **自動プレフィックス選択**: ブランチ名と変更内容から最適なプレフィックスを判断
- **Conventional Commits準拠**: 標準的なコミットメッセージ形式に従う
- **簡潔な1行メッセージ**: 変更内容を的確に要約
- **日本語対応**: 日本語でのコミットメッセージ生成に対応

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

## インストール

```bash
# マーケットプレイスを追加（初回のみ）
/plugin marketplace add https://github.com/shouta-nakashima/my-claude-plugins

# プラグインをインストール
/plugin install smart-commit@my-claude-plugins
```

## 使い方

### 基本的な使い方

```bash
/smart-commit:commit
```

このコマンドを実行すると、Claudeが以下を自動で行います：

1. 現在のブランチ名を取得
2. 変更内容を確認（`git status`, `git diff`）
3. 適切なConventional Commits形式のメッセージを生成
4. ユーザーに確認を求める
5. コミットを実行

### 実行例

#### 例1: 機能追加の場合

```
ブランチ: feature/user-authentication
変更内容: ユーザー認証機能を実装

生成されるメッセージ:
feat: add user authentication feature
```

#### 例2: バグ修正の場合

```
ブランチ: fix/login-error
変更内容: ログイン時のエラーハンドリングを修正

生成されるメッセージ:
fix: correct error handling in login flow
```

#### 例3: ドキュメント更新の場合

```
ブランチ: docs/update-readme
変更内容: README.mdにインストール手順を追加

生成されるメッセージ:
docs: update README with installation steps
```

## 利点

- **時間短縮**: コミットメッセージを考える時間を削減
- **一貫性**: プロジェクト全体で統一されたコミットメッセージ形式
- **明確な履歴**: `git log` で変更の種類が一目でわかる
- **自動化**: ブランチ名に基づいて適切なプレフィックスを自動選択

## Conventional Commitsについて

Conventional Commitsは、コミットメッセージに人間と機械が読みやすい意味を持たせるための仕様です。

### メリット

- CHANGELOGの自動生成
- セマンティックバージョニングの自動判定
- 変更内容の明確な伝達
- コントリビューターの参加しやすさ向上

詳細: https://www.conventionalcommits.org/

## 注意事項

- コミット前に必ず生成されたメッセージを確認してください
- 複数の種類の変更が含まれる場合は、最も重要な変更に基づいてプレフィックスが選択されます
- 必要に応じて手動でメッセージを調整することも可能です

## ライセンス

MIT

## 作者

shouta-nakashima
