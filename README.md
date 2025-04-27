# 0427websitedemoeibunn
20250427Websiteの英語の長文レイアウト崩れや@mediaボタンサイズ修正のデモサイト練習
レスポンシブデザインの練習に最適な、@mediaを活用した新人エンジニア向けのデモサイトを作成します。このサイトでは、画面サイズによってレイアウトが変化する実例を示し、修正方法も解説します。

# @mediaクエリ練習用デモサイトの解説

作成したデモサイトでは、レスポンシブデザインの基本と@mediaクエリの使い方を実践的に学ぶことができます。ブラウザの幅を変更すると、レイアウトが自動的に変化します。

## デモサイトの特徴

1. **3つのレイアウト**:
   - デスクトップ (769px以上)
   - タブレット (481px～768px)
   - モバイル (480px以下)

2. **現在の画面情報表示**:
   - 画面幅のリアルタイム表示
   - 現在のデバイスタイプの表示

3. **レスポンシブ要素**:
   - 柔軟なナビゲーションメニュー
   - フレックスボックスを使用したカードレイアウト
   - メインコンテンツとサイドバーのレイアウト変更

## @mediaクエリの解説

### 基本構文

```css
@media メディアタイプ and (条件) {
    /* 条件に一致した場合に適用されるスタイル */
}
```

### 主なメディアタイプ

- `screen`: 画面用（モニター、スマホなど）
- `print`: 印刷用
- `all`: すべてのデバイス（デフォルト）

### 主な条件（メディア特性）

- `width`, `min-width`, `max-width`: 画面幅
- `height`, `min-height`, `max-height`: 画面高さ
- `orientation`: 向き（`portrait`または`landscape`）
- `aspect-ratio`: 画面のアスペクト比
- `resolution`: 解像度

## デモサイトでの実装例

### タブレット向けのスタイル (768px以下)

```css
@media screen and (max-width: 768px) {
    .main-content {
        flex-direction: column; /* 横並びから縦並びに変更 */
    }
    
    .sidebar {
        margin-left: 0;
        margin-top: 20px; /* サイドバーを下部に移動 */
    }
    
    .card {
        flex-basis: 48%; /* カードを2列に */
    }
    
    nav ul {
        flex-wrap: wrap; /* ナビゲーションを折り返し可能に */
    }
    
    nav li {
        flex-basis: 50%; /* ナビアイテムを2列に */
    }
}
```

### モバイル向けのスタイル (480px以下)

```css
@media screen and (max-width: 480px) {
    .card {
        flex-basis: 100%; /* カードを1列に */
    }
    
    nav li {
        flex-basis: 100%; /* ナビアイテムを1列に */
    }
    
    .mobile-warning {
        display: block; /* モバイル警告を表示 */
    }
}
```

## よくある@mediaクエリの問題と修正方法

### 1. ブレイクポイントの選定

**問題**: 不適切なブレイクポイント設定によるレイアウト崩れ

**修正方法**:
- デバイスに合わせたブレイクポイントではなく、コンテンツに合わせたブレイクポイントを設定
- 一般的なブレイクポイント: 480px, 768px, 1024px, 1200px

```css
/* 小型デバイス用 */
@media screen and (max-width: 480px) { ... }

/* タブレット用 */
@media screen and (max-width: 768px) { ... }

/* 小型デスクトップ用 */
@media screen and (max-width: 1024px) { ... }
```

### 2. メタビューポートの設定

**問題**: モバイルデバイスでの表示が最適化されない

**修正方法**:
```html
<meta name="viewport" content="width=device-width, initial-scale=1.0">
```

### 3. メディアクエリの順序

**問題**: 後に定義したスタイルが先に定義したものを上書きしてしまう

**修正方法**:
- モバイルファースト: 小さい画面サイズから大きい画面サイズへ順に定義
```css
/* ベース（モバイル用）スタイル */
.element { ... }

/* タブレット用 */
@media screen and (min-width: 481px) { ... }

/* デスクトップ用 */
@media screen and (min-width: 769px) { ... }
```

- デスクトップファースト: 大きい画面サイズから小さい画面サイズへ順に定義
```css
/* ベース（デスクトップ用）スタイル */
.element { ... }

/* タブレット用 */
@media screen and (max-width: 768px) { ... }

/* モバイル用 */
@media screen and (max-width: 480px) { ... }
```

### 4. 画像のレスポンシブ対応

**問題**: 画像サイズがコンテナに合わない

**修正方法**:
```css
img {
    max-width: 100%;
    height: auto;
}
```

### 5. テキストサイズの調整

**問題**: 小さい画面での読みにくさ

**修正方法**:
```css
body {
    font-size: 16px; /* ベースサイズ */
}

@media screen and (max-width: 768px) {
    body {
        font-size: 14px; /* タブレット用に少し小さく */
    }
}
```

## 実践練習のヒント

1. デモサイトでブラウザの幅を変更して、各ブレイクポイントでのレイアウト変化を観察
2. 「修正を表示/非表示」ボタンで修正前と修正後の違いを確認
3. 以下の変更を試して実践練習:

   - カードの色を画面サイズによって変更
   ```css
   @media screen and (max-width: 768px) {
       .card {
           background-color: #f0f8ff; /* タブレットでは薄い青色に */
       }
   }
   ```

   - フォントサイズを画面サイズによって変更
   ```css
   @media screen and (max-width: 480px) {
       h1 {
           font-size: 1.5em; /* モバイルでは小さく */
       }
   }
   ```

   - 印刷用スタイルの追加
   ```css
   @media print {
       nav, .sidebar, .controls {
           display: none; /* 印刷時には非表示 */
       }
   }
   ```

このデモサイトを通じて、@mediaクエリの基本から応用までを実践的に学ぶことができます。様々な画面サイズでテストしながら、レスポンシブデザインのスキルを向上させてください。
