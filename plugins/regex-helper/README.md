# regex-helper

対話型で正規表現を作成・テスト・デバッグできるClaude Codeプラグインです。

## 機能

正規表現が苦手な人でも、対話しながら目的の正規表現を作れます。

### コマンド一覧

| コマンド | 説明 |
|----------|------|
| `/regex-helper:build` | 対話型で正規表現を構築（自然言語・サンプルからも対応） |
| `/regex-helper:explain` | 正規表現を分解して解説 |
| `/regex-helper:test` | 正規表現をテスト |
| `/regex-helper:patterns` | よく使うパターン集から選択 |
| `/regex-helper:replace` | 置換パターンの作成支援 |
| `/regex-helper:debug` | マッチしない原因を特定 |
| `/regex-helper:convert` | 言語間の正規表現変換 |

## 使用例

### 対話型で正規表現を作成

```
User: /regex-helper:build

Claude: どのように正規表現を作成しますか？
        1. 質問に答えながら作る（対話型）
        2. サンプル文字列から作る
        3. やりたいことを説明する（自然言語）

User: 3

Claude: やりたいことを説明してください:

User: 日本の携帯電話番号を抽出したい

Claude: 生成した正規表現:
        /0[789]0-\d{4}-\d{4}/

        マッチ例:
        ✓ 090-1234-5678
        ✓ 080-9999-0000
```

### 正規表現の解説

```
User: /regex-helper:explain
      ^(?=.*[A-Z])(?=.*\d).{8,}$

Claude: この正規表現はパスワードバリデーションです:

        ^           → 文字列の先頭
        (?=.*[A-Z]) → 大文字を1つ以上含む（先読み）
        (?=.*\d)    → 数字を1つ以上含む（先読み）
        .{8,}       → 任意の文字が8文字以上
        $           → 文字列の末尾

        要約: 8文字以上で、大文字と数字を含む文字列
```

### サンプルから正規表現を生成

```
User: /regex-helper:build

Claude: どのように正規表現を作成しますか？

User: 2

Claude: サンプル文字列を入力してください:

User: ORD-12345-JP

Claude: この文字列のどこを抽出したいですか？

User: 全体

Claude: パターンを分析しました:
        構造: [英字3文字]-[数字5桁]-[英字2文字]

        生成した正規表現:
        /ORD-\d{5}-[A-Z]{2}/
```

### デバッグ

```
User: /regex-helper:debug

Claude: デバッグしたい正規表現を入力:

User: /^[0-9]{3}-[0-9]{4}$/

Claude: テスト文字列を入力:

User: 〒123-4567

Claude: ✗ マッチしません

        原因: 先頭の「〒」が ^ でブロックされています

        修正案:
        1. /^〒?[0-9]{3}-[0-9]{4}$/ で〒を許容
        2. /[0-9]{3}-[0-9]{4}/ で部分マッチ
```

### 言語間変換

```
User: /regex-helper:convert
      JavaScript: /\d+/gi → Python

Claude: Python版:

        import re
        pattern = re.compile(r'\d+', re.IGNORECASE)
        matches = pattern.findall(text)  # gフラグ相当
```

## インストール

```bash
# マーケットプレイスを追加
/plugin marketplace add https://github.com/shouta-nakashima/my-claude-plugins

# プラグインをインストール
/plugin install regex-helper@my-claude-plugins
```

## 対応パターン

`/regex-helper:patterns` で以下のカテゴリのパターンを利用できます:

- **連絡先**: メールアドレス、電話番号
- **Web**: URL、ドメイン、IPアドレス
- **日付・時刻**: 各種フォーマット
- **日本固有**: 郵便番号、ひらがな、カタカナ、漢字
- **バリデーション**: パスワード、ユーザー名
- **プログラミング**: 変数名、HTMLタグ、コメント
- **数値・金額**: 整数、小数、通貨

## ライセンス

MIT
