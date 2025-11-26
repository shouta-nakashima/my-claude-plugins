# Hello World Plugin

Claude Codeプラグイン開発の入門用サンプルプラグインです。

## 機能

- シンプルな挨拶コマンド
- プロジェクト情報表示スキル

## インストール

```bash
/plugin marketplace add shouta-nakashima/my-claude-plugins
/plugin install hello-world@my-claude-plugins
```

## 使い方

### コマンド

#### `/hello-world:greet`

挨拶メッセージを表示します。

```bash
/hello-world:greet
```

### スキル

#### `project-info`

現在のプロジェクトの情報を分析して表示します。ユーザーが「プロジェクトについて教えて」や「このリポジトリの情報は？」と尋ねたときに自動的に起動します。

## 開発者向け

このプラグインは、以下の要素を含む最小限の実装例です：

- `plugin.json` - プラグインメタデータ
- `commands/` - スラッシュコマンド定義
- `skills/` - スキル定義
- `README.md` - ドキュメント

新しいプラグインを作成する際の参考にしてください。

## ライセンス

MIT
