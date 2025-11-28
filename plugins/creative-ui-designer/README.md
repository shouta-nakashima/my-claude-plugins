# Creative UI Designer

AIっぽくない、独創的で印象的なUIデザインを生成するClaude Codeプラグインです。

## 概要

Claudeが生成するフロントエンドUIは、訓練データの統計パターンから「安全な」デザイン選択を優先するため、似たようなデザイン(Interフォント、紫グラデーション、白背景など)に収束しがちです。このプラグインは、その「分布的収束(distributional convergence)」を回避し、独創的で印象的なUIを生成します。

## 特徴

- **タイポグラフィ**: 退屈で一般的なフォントを避け、特徴的なフォントペアリングを提案
- **色彩とテーマ**: IDEテーマや文化的美学から着想を得た一貫したパレット
- **背景効果**: 単色ではなく、レイヤー化されたグラデーション、パターン、効果で深みを作成
- **アニメーション**: ページロード時など高インパクトな瞬間に焦点を当てた動き
- **アクセシビリティ**: WCAG AA基準を維持しながら独創的なデザインを実現

## 対応技術スタック

- **React** (TypeScript + Hooks優先)
- **Vue** (Vue 3 Composition API優先)
- **HTML/CSS/JavaScript** (モダンES6+)
- **CSSフレームワーク**: Tailwind CSS優先、CSS Modules、Styled Componentsも対応

## インストール

```bash
/plugin marketplace add shouta-nakashima/my-claude-plugins
/plugin install creative-ui-designer@my-claude-plugins
```

## 使い方

### コマンド

#### `/creative-ui-designer:create-component`

独創的なUIコンポーネントを作成します。

```
/creative-ui-designer:create-component
```

インタラクティブウィザードが起動し、以下を質問します:
- コンポーネント名(例: "Button", "Card", "HeroSection")
- コンポーネントのタイプ・目的
- ターゲットフレームワーク(React、Vue、HTMLなど)
- デザインの方向性(オプション)

**生成されるもの**:
- 完全な実装コード
- TypeScript型定義(該当する場合)
- レスポンシブデザイン
- アクセシビリティ属性
- ホバー/フォーカス状態とアニメーション
- 使用例
- デザイン決定の説明

#### `/creative-ui-designer:design-page`

ページ全体(ランディングページ、ダッシュボードなど)をデザインします。

```
/creative-ui-designer:design-page
```

以下を質問されます:
- ページタイプ(ランディングページ、ダッシュボード、ポートフォリオ、ブログ、ECなど)
- ターゲットフレームワーク
- デザインの方向性(IDEテーマ、文化的美学、自然パレットなど)

**生成されるもの**:
- 完全なページ実装
- セクション構造(Hero、Features、CTAなど)
- レスポンシブレイアウト
- アニメーションと相互作用
- セットアップ手順
- デザインドキュメント

#### `/creative-ui-designer:evaluate-design`

既存のページやコンポーネントのデザインを評価し、改善提案を行います。

```
/creative-ui-designer:evaluate-design
```

以下を質問されます:
- 評価するファイルのパス(単一ファイルまたはGlobパターン)

**評価内容**:
1. **タイポグラフィ評価** (/10点) - フォント選択、ペアリング、コントラスト
2. **配色とテーマ評価** (/10点) - カラーパレット、統一感、アクセシビリティ
3. **背景効果評価** (/10点) - 深み、レイヤー化、視覚的階層
4. **アニメーション評価** (/10点) - 戦略的配置、高インパクト、アクセシビリティ

**総合スコア**: /40点

**生成されるもの**:
- 詳細な評価レポート
- 4つの領域ごとのスコアと分析
- 具体的な改善提案(優先度付き)
- 実装例(Before/After)
- 次のステップの提案
- オプション: 改善版コードの生成

**評価ランク**:
- 🌟 35-40点: 優秀 - 非常に独創的
- ✅ 28-34点: 良好 - 独創的な要素が多い
- ⚠️ 20-27点: 改善が必要 - もっと独創性が必要
- ❌ 10-19点: 大幅な改善が必要 - かなりAIっぽい
- 🚨 0-9点: 全面的な再設計推奨

### スキル

#### `distinctive-ui-design`

フロントエンドのコンポーネントやページ作成時に自動的に適用されるスキルです。以下のような依頼で起動します:

- "コンポーネントを作って"
- "ページをデザインして"
- "UIを作成して"
- "ランディングページを作って"
- "ダッシュボードを構築して"

このスキルは以下を提供します:
- 独創的なタイポグラフィの選択肢
- IDEテーマや文化的美学に基づいたカラーパレット
- 背景効果のテクニック(レイヤー化グラデーション、パターン、グラスモーフィズム)
- 高インパクトなアニメーションパターン
- アクセシビリティガイドライン

## デザイン原則

### 避けるべきパターン ❌

- **フォント**: Inter, Roboto, Open Sans などの一般的なフォント
- **配色**: 紫のグラデーション、白背景に紫、ジェネリックなパステルカラー
- **レイアウト**: 単調な中央寄せ、グリッドの過度な使用
- **アニメーション**: 散発的なマイクロインタラクション
- **背景**: 単色背景、ありふれたグラデーション

### 推奨される実践 ✅

1. **タイポグラフィ**: Playfair Display、Space Grotesk、Bricolage Grotesqueなどの特徴的なフォント
2. **色彩・テーマ**: Tokyo Night、Dracula、Nord、ブルータリズム、ヴェイパーウェーブなどから着想
3. **背景エフェクト**: レイヤー化グラデーション、幾何学パターン、ノイズテクスチャ
4. **アニメーション**: ページロード時のスタッガード表示、意味のあるホバー状態

## 日本語対応

このプラグインは日本語コンテンツに完全対応しています!

### 日本語フォントの推奨

**避けるべき**: デフォルトのゴシック体(カスタマイズなしのYu Gothic)

**推奨フォント**:

#### ゴシック体(Gothic) - モダン、クリーン
- Zen Kaku Gothic New
- M PLUS Rounded 1c
- Kosugi Maru

#### 明朝体(Mincho) - エレガント、フォーマル
- Shippori Mincho B1
- Zen Old Mincho
- Noto Serif JP

#### 丸ゴシック体(Rounded) - 親しみやすい
- Zen Maru Gothic
- M PLUS Rounded 1c
- Kiwi Maru

#### 手書き・装飾(Handwriting/Decorative) - 独創的
- Yusei Magic
- RocknRoll One
- Dela Gothic One

### 日本語フォントペアリング例

| 見出し | 本文 | スタイル |
|--------|------|----------|
| Shippori Mincho B1 | Noto Sans JP | クラシックなエディトリアル |
| Dela Gothic One | Zen Kaku Gothic New | 大胆でモダン |
| Yusei Magic | M PLUS 1p | 遊び心のある独創的 |
| Zen Old Mincho | Kosugi | 伝統的でエレガント |

### 実装例

```html
<!-- Google Fontsで日本語フォントを読み込み -->
<link href="https://fonts.googleapis.com/css2?family=Shippori+Mincho+B1:wght@400;700;800&family=Noto+Sans+JP:wght@300;400;500;700&display=swap" rel="stylesheet">

<style>
  h1, h2, h3 { font-family: 'Shippori Mincho B1', serif; }
  body { font-family: 'Noto Sans JP', sans-serif; }
</style>
```

### バイリンガルデザイン

英語と日本語が混在するサイトの場合:

```css
:root { font-family: 'Inter', sans-serif; }
:lang(ja) { font-family: 'Noto Sans JP', sans-serif; }
h1 { font-family: 'Playfair Display', serif; }
h1:lang(ja) { font-family: 'Shippori Mincho B1', serif; }
```

## 例

### コンポーネント作成の例

```
User: /creative-ui-designer:create-component
Claude: 何のコンポーネントを作成しますか?
User: Call-to-actionボタン
Claude: どのフレームワークを使用していますか?
User: React with Tailwind CSS
Claude: デザインの方向性はありますか?(オプション)
User: Tokyo Night theme

[Claudeが独創的なボタンコンポーネントを生成...]
```

### ページデザインの例

```
User: /creative-ui-designer:design-page
Claude: どのタイプのページをデザインしますか?
User: Landing page
Claude: どのフレームワークを使用していますか?
User: Next.js with Tailwind CSS
Claude: デザインの方向性やインスピレーションはありますか?
User: Brutalism with ocean color palette

[Claudeが完全なランディングページを生成...]
```

### デザイン評価の例

```
User: /creative-ui-designer:evaluate-design
Claude: 評価するファイルのパスを教えてください
User: src/components/Hero.tsx

[Claudeが詳細な評価レポートを生成...]

# デザイン評価レポート

**評価対象**: src/components/Hero.tsx
**総合スコア**: 23/40点 - ⚠️ 改善が必要

## 📊 スコア内訳

### タイポグラフィ: 4/10点
**主な問題**:
- Interフォントをデフォルトで使用
- 見出しと本文のフォントが同じ
- フォントサイズのコントラストが不十分

### 配色とテーマ: 7/10点
**良い点**: 統一感のあるカラーパレット
**主な問題**: 紫のグラデーションが一般的

### 背景効果: 6/10点
**主な問題**: 単色背景のみ、深みがない

### アニメーション: 6/10点
**良い点**: ホバー状態あり
**主な問題**: 戦略的配置が不十分

## 🎯 改善提案

### 優先度: High
1. タイポグラフィの変更
   **提案**: Space Grotesk + DM Sansに変更
   [実装例...]

[その他の改善提案...]

Claude: 改善版のコードを生成しますか?
User: はい

[Claudeが改善版コード + Before/After比較を生成...]
```

## トラブルシューティング

### スキルが適用されない

コマンドを明示的に使用してください:
```
/creative-ui-designer:create-component
```

または、依頼時に明確に指示してください:
```
distinctive-ui-designスキルを使って、ボタンコンポーネントを作成して
```

### デザインが一般的に見える

コマンドを使用する際に、具体的なデザイン方向を指定してください:
- IDEテーマ: "Tokyo Night", "Dracula", "Nord"
- 文化的美学: "Brutalism", "Swiss design", "Vaporwave"
- 自然パレット: "Ocean", "Sunset", "Forest"

## アクセシビリティ

このプラグインは独創性を追求しながら、基本的なアクセシビリティを維持します:

- **色のコントラスト**: WCAG AA最小値(通常テキストは4.5:1、大きいテキストは3:1)
- **セマンティックHTML**: 適切な見出し階層、ランドマーク、フォームラベル
- **キーボードナビゲーション**: すべてのインタラクティブ要素がキーボードでアクセス可能
- **ARIA属性**: セマンティックHTMLが不十分な場合に追加
- **prefers-reduced-motion**: アニメーションはユーザーの設定を尊重

## ライセンス

MIT

## 参考文献

このプラグインは、Anthropicの記事「[Improving Frontend Design Through Skills](https://www.claude.com/blog/improving-frontend-design-through-skills)」にインスパイアされています。
