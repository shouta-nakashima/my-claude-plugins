# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## プロジェクト概要

このリポジトリは、Claude CodeとClaude App用のカスタムプラグインを管理するマーケットプレイスです。GitHubをベースとしたプラグインの開発・配布・管理を行います。

## リポジトリ構造

```
my-claude-plugins/
├── .claude-plugin/
│   └── marketplace.json          # マーケットプレイスカタログ（重要）
├── plugins/                      # 各プラグインのソースコード
│   ├── hello-world/             # サンプルプラグイン
│   │   ├── .claude-plugin/
│   │   │   └── plugin.json      # プラグインメタデータ（必須）
│   │   ├── commands/            # スラッシュコマンド定義
│   │   ├── skills/              # スキル定義
│   │   ├── agents/              # エージェント定義
│   │   └── README.md
│   └── ...
├── templates/
│   └── plugin-template/         # 新規プラグイン作成用テンプレート
├── scripts/                     # ユーティリティスクリプト
├── .github/workflows/
│   └── validate-plugins.yml     # 自動検証CI/CD
├── README.md                    # ユーザー向けドキュメント
└── CLAUDE.md                    # このファイル
```

## 重要なファイル

### `.claude-plugin/marketplace.json`

マーケットプレイスのカタログファイル。全てのプラグインをここに登録する必要があります。

**構造**:
```json
{
  "name": "マーケットプレイス名",
  "owner": "所有者",
  "description": "説明",
  "version": "1.0.0",
  "plugins": [
    {
      "name": "プラグイン名",
      "source": "GitHubのURL",
      "description": "説明",
      "version": "1.0.0",
      "author": "作者",
      "tags": ["タグ"]
    }
  ]
}
```

### `plugins/*/. claude-plugin/plugin.json`

各プラグインのメタデータファイル（必須）。

**必須フィールド**:
- `name`: プラグイン名（kebab-case）
- `version`: バージョン（セマンティックバージョニング）
- `description`: 説明

## 開発ワークフロー

### 新しいプラグインを追加する場合

1. **テンプレートをコピー**:
   ```bash
   cp -r templates/plugin-template plugins/new-plugin-name
   ```

2. **plugin.jsonを編集**:
   - プラグイン名、説明、作者などを更新
   - `plugins/new-plugin-name/.claude-plugin/plugin.json`

3. **機能を実装**:
   - コマンド: `commands/*.md`
   - スキル: `skills/SKILL.md`
   - エージェント: `agents/*.yaml`

4. **README.mdを作成**:
   - インストール方法、使い方、例を記載

5. **marketplace.jsonに追加**:
   - `.claude-plugin/marketplace.json` の `plugins` 配列に新しいプラグインを追加

6. **ローカルテスト**:
   ```bash
   /plugin marketplace add ./path/to/my-claude-plugins
   /plugin install new-plugin-name@my-claude-plugins
   ```

### プラグインを更新する場合

1. プラグインのソースコードを修正
2. `plugin.json` のバージョンを更新（セマンティックバージョニング）
3. `marketplace.json` のバージョンも更新
4. 変更内容をREADME.mdに記載

## 検証とテスト

### ローカル検証

新しいプラグインや変更をテストする前に、以下を確認:

1. **JSON形式の検証**:
   ```bash
   jq empty .claude-plugin/marketplace.json
   jq empty plugins/*/. claude-plugin/plugin.json
   ```

2. **必須フィールドの確認**:
   - `plugin.json` に `name`, `version`, `description` が含まれているか
   - `marketplace.json` に正しいプラグイン情報が含まれているか

3. **ローカルインストールテスト**:
   ```bash
   /plugin marketplace add $(pwd)
   /plugin install your-plugin@my-claude-plugins
   ```

### CI/CD

GitHub Actionsが以下を自動検証:
- marketplace.jsonの形式
- 全てのplugin.jsonの形式と必須フィールド
- README.mdの存在
- marketplace.jsonとプラグインディレクトリの整合性

コミット前に必ずパスすること。

## プラグイン開発のベストプラクティス

### 命名規則

- **プラグイン名**: `kebab-case`（例: `hello-world`）
- **コマンド名**: `kebab-case.md`（例: `greet.md`）
- **スキル**: `SKILL.md`（固定名）
- **エージェント**: `kebab-case.yaml`

### ディレクトリ構造

必須ファイル:
- `.claude-plugin/plugin.json`
- `README.md`

オプショナル:
- `commands/` - スラッシュコマンド
- `skills/` - スキル
- `agents/` - エージェント
- `hooks/` - イベントフック

### パスの指定

プラグイン内でパスを指定する場合は `${CLAUDE_PLUGIN_ROOT}` を使用:

```bash
source ${CLAUDE_PLUGIN_ROOT}/scripts/helper.sh
```

これにより、インストール場所に依存しないコードになります。

### バージョン管理

セマンティックバージョニングを使用:
- **MAJOR**: 互換性のない変更（例: 1.0.0 → 2.0.0）
- **MINOR**: 後方互換性のある機能追加（例: 1.0.0 → 1.1.0）
- **PATCH**: 後方互換性のあるバグ修正（例: 1.0.0 → 1.0.1）

## よくあるタスク

### プラグイン情報を確認

```bash
cat .claude-plugin/marketplace.json | jq '.plugins'
```

### 特定のプラグインのメタデータを確認

```bash
cat plugins/hello-world/.claude-plugin/plugin.json | jq
```

### 全プラグインの検証

```bash
for plugin in plugins/*/; do
  echo "Validating $(basename $plugin)..."
  jq empty "$plugin/.claude-plugin/plugin.json" && echo "✓ Valid" || echo "✗ Invalid"
done
```

## トラブルシューティング

### プラグインが認識されない

- `plugin.json` が `.claude-plugin/` ディレクトリにあるか確認
- JSON形式が正しいか確認: `jq empty plugin.json`
- `autoDiscovery` が有効になっているか確認

### マーケットプレイスからインストールできない

- `.claude-plugin/marketplace.json` にプラグインが登録されているか確認
- `source` URLが正しいか確認
- GitHubにプッシュされているか確認

## 注意事項

- リポジトリ名は `my-claude-plagins` ですが、正しいスペルは "plugins" です（修正は任意）
- プラグイン追加時は必ず `marketplace.json` と `plugin.json` の両方を更新してください
- バージョン更新時は両ファイルのバージョンを同期させてください
- コミット前にCI/CDチェックがパスすることを確認してください

## リソース

- [README.md](README.md) - ユーザー向けドキュメント
- [templates/plugin-template/](templates/plugin-template/) - プラグインテンプレート
