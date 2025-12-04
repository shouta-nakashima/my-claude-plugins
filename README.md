# My Claude Plugins Marketplace

Claude CodeとClaude App用のカスタムプラグインを管理するマーケットプレイスリポジトリです。

## 概要

このリポジトリは、独自開発したClaude Codeプラグインを一元管理し、簡単にインストール・共有できるようにするためのマーケットプレイスです。

## 特徴

- **一元管理**: 複数のプラグインを1つのリポジトリで管理
- **簡単インストール**: スラッシュコマンドで即座にインストール可能
- **テンプレート提供**: 新規プラグイン開発用のテンプレート付き
- **自動検証**: GitHub Actionsによる品質チェック

## クイックスタート

### マーケットプレイスの追加

Claude Codeで以下のコマンドを実行：

```bash
/plugin marketplace add shouta-nakashima/my-claude-plugins
```

### プラグインのインストール

```bash
/plugin install smart-git@my-claude-plugins
```

### 利用可能なプラグインを確認

```bash
/plugin
```

ブラウズメニューから "Browse Plugins" を選択してください。

## 利用可能なプラグイン

### [smart-git](plugins/smart-git/README.md)

コミットとPR作成を効率化するGit操作プラグイン。ブランチ名と変更内容からConventional Commits形式のコミットメッセージを自動生成し、GitHub PR作成もコマンド一発で実行できます。

- `/smart-git:commit` - Conventional Commits形式でコミット
- `/smart-git:create-pr` - GitHub PRを作成
- `/smart-git:commit-and-pr` - コミット → プッシュ → PR作成を一括実行

```bash
/plugin install smart-git@my-claude-plugins
```

---

### [regex-helper](plugins/regex-helper/README.md)

対話型で正規表現を作成・テスト・デバッグできるプラグイン。正規表現が苦手な人でも、対話しながら目的の正規表現を作れます。

- `/regex-helper:build` - 対話型で正規表現を構築（自然言語・サンプルからも対応）
- `/regex-helper:explain` - 正規表現を分解して解説
- `/regex-helper:test` - 正規表現をテスト
- `/regex-helper:debug` - マッチしない原因を特定

```bash
/plugin install regex-helper@my-claude-plugins
```

---

### [creative-ui-designer](plugins/creative-ui-designer/README.md)

AIっぽくない、独創的で印象的なUIデザインを生成するプラグイン。Claudeが生成しがちな「安全な」デザイン（Interフォント、紫グラデーション等）を回避し、IDEテーマや文化的美学から着想を得たユニークなUIを作成します。

- `/creative-ui-designer:create-component` - 独創的なUIコンポーネントを作成
- `/creative-ui-designer:design-page` - ページ全体をデザイン
- `/creative-ui-designer:evaluate-design` - 既存デザインを評価し改善提案

```bash
/plugin install creative-ui-designer@my-claude-plugins
```

## ライセンス

MIT

## リソース

- [Claude Code 公式ドキュメント](https://docs.anthropic.com/claude-code)
- [Plugin Development Guide](https://docs.anthropic.com/claude-code/plugins)
