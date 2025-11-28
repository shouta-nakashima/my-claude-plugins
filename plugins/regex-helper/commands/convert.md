# convert - 言語間の正規表現変換

異なるプログラミング言語間で正規表現を変換するコマンドです。

## 実行時の動作

### ステップ1: 変換元の入力

```
変換元の正規表現と言語を入力してください:

例:
- JavaScript: /\d+/gi
- Python: r'\d+'
- "Go言語の \d+ を Python に変換したい"
```

### ステップ2: 変換先の選択

```
変換先の言語を選択してください:

1. JavaScript
2. Python
3. Go
4. Java
5. Ruby
6. PHP
7. Rust
8. C# (.NET)
```

### ステップ3: 変換結果の表示

```
変換結果:

【JavaScript → Python】

元の正規表現:
/\d+/gi

Python版:
import re
pattern = re.compile(r'\d+', re.IGNORECASE)

# 使用例
matches = pattern.findall(text)  # gフラグ相当（全マッチ）
match = pattern.search(text)      # 最初のマッチのみ

注意点:
- Python に g フラグはなく、findall() で全マッチを取得
- i フラグは re.IGNORECASE で指定
- Python の raw string (r'...') を使用してエスケープを簡略化
```

## 言語別の違い

### フラグの対応表

| フラグ | JavaScript | Python | Go | Java |
|--------|------------|--------|-----|------|
| 大文字小文字無視 | `i` | `re.IGNORECASE` | `(?i)` | `(?i)` or `CASE_INSENSITIVE` |
| 複数行 | `m` | `re.MULTILINE` | `(?m)` | `(?m)` or `MULTILINE` |
| ドット改行対応 | `s` | `re.DOTALL` | `(?s)` | `(?s)` or `DOTALL` |
| グローバル | `g` | なし（findall使用） | なし（FindAll使用） | なし（Matcher使用） |

### JavaScript → Python

```javascript
// JavaScript
const regex = /(\d{4})-(\d{2})-(\d{2})/g;
const matches = text.matchAll(regex);
```

```python
# Python
import re
pattern = re.compile(r'(\d{4})-(\d{2})-(\d{2})')
matches = pattern.findall(text)  # タプルのリスト
# または
matches = pattern.finditer(text)  # マッチオブジェクトのイテレータ
```

### JavaScript → Go

```javascript
// JavaScript
const regex = /\b\w+@\w+\.\w+\b/i;
```

```go
// Go
import "regexp"

// Goは(?i)をパターン内に埋め込む
pattern := regexp.MustCompile(`(?i)\b\w+@\w+\.\w+\b`)
matches := pattern.FindAllString(text, -1)
```

### JavaScript → Java

```javascript
// JavaScript
const regex = /^[a-z]+$/i;
regex.test(str);
```

```java
// Java
import java.util.regex.*;

Pattern pattern = Pattern.compile("^[a-z]+$", Pattern.CASE_INSENSITIVE);
Matcher matcher = pattern.matcher(str);
boolean matches = matcher.matches();
```

### Python → JavaScript

```python
# Python
import re
pattern = re.compile(r'(?P<year>\d{4})-(?P<month>\d{2})', re.IGNORECASE)
match = pattern.search(text)
if match:
    year = match.group('year')
```

```javascript
// JavaScript (名前付きキャプチャ対応)
const regex = /(?<year>\d{4})-(?<month>\d{2})/i;
const match = text.match(regex);
if (match) {
    const year = match.groups.year;
}
```

## 変換時の注意点

### 1. 名前付きキャプチャグループ

```
Python:  (?P<name>...)
JS/Java: (?<name>...)
Ruby:    (?<name>...) または (?'name'...)
```

### 2. 後読み（Lookbehind）のサポート

```
JavaScript: ES2018以降でサポート
Go:         サポートなし（代替手段が必要）
Python:     固定長のみサポート
```

### 3. Unicode プロパティ

```
JavaScript: /\p{Script=Han}/u （uフラグ必須）
Python:     regex モジュールが必要
Go:         \p{Han} （標準でサポート）
```

### 4. 文字列のエスケープ

```
JavaScript: /path\\to\\file/  または  new RegExp('path\\\\to\\\\file')
Python:     r'path\\to\\file' （raw string推奨）
Go:         `path\\to\\file`  （バッククォート推奨）
```
