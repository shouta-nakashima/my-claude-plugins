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
/plugin install hello-world@my-claude-plugins
```

### 利用可能なプラグインを確認

```bash
/plugin
```

ブラウズメニューから "Browse Plugins" を選択してください。

## 利用可能なプラグイン

### hello-world

Claude Codeプラグイン開発のサンプル実装。

- **コマンド**: `/hello-world:greet` - 挨拶メッセージを表示
- **スキル**: プロジェクト情報の自動分析

**インストール**:
```bash
/plugin install hello-world@my-claude-plugins
```

## プラグイン開発

### 新しいプラグインの作成

1. `templates/plugin-template` をコピー:

   ```bash
   cp -r templates/plugin-template plugins/your-plugin-name
   ```

2. `plugins/your-plugin-name/.claude-plugin/plugin.json` を編集

3. コマンド、スキル、エージェントを追加

4. `plugins/your-plugin-name/README.md` にドキュメントを記載

5. `.claude-plugin/marketplace.json` にプラグインを追加

### プラグイン構造

```
your-plugin/
├── .claude-plugin/
│   └── plugin.json          # プラグインメタデータ（必須）
├── commands/                # スラッシュコマンド（.mdファイル）
├── skills/                  # スキル（SKILL.mdファイル）
├── agents/                  # エージェント（YAMLファイル）
├── hooks/                   # イベントフック
│   └── hooks.json
└── README.md                # ドキュメント
```

## ローカルテスト

開発中のプラグインをローカルでテストする場合：

```bash
/plugin marketplace add ./path/to/my-claude-plugins
/plugin install your-plugin@my-claude-plugins
```

## ライセンス

MIT

## リソース

- [Claude Code 公式ドキュメント](https://docs.anthropic.com/claude-code)
- [Plugin Development Guide](https://docs.anthropic.com/claude-code/plugins)
