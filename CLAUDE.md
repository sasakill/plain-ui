# Plain UI - AI向け指示

> このDSは「主張しない」ことを目的に設計されている。コンテンツの構造と階層を伝えるための最小限のシステム。
> UI生成時にこのファイルから読み始めること。

**読み込みモード**:

| モード | 読むファイル | 用途 |
|--------|------------|------|
| クイック | CLAUDE.md のみ | 単体UIの生成（全コンポーネント対応） |
| フル | CLAUDE.md + README.md | 設計思想の確認・DS変更 |

> クイックリファレンスだけで基本的なUIは生成可能。

---

## 設計原則（3つ）

1. **Invisible Design** — デザインシステム自体が前に出ず、コンテンツの構造だけが伝わる
2. **Structure First** — タイポグラフィと余白だけで読める状態を基準とする
3. **Open for Interpretation** — ブランドカラー・書体・アイコン・モーションは意図的に未定義。デザイナーが決定する

---

## 制約

- 色はグレースケールのみ（Black / White / Gray）
- 装飾要素なし（影・グラデーション・角丸すべて不使用）
- アニメーションなし
- `border-radius: 0` を徹底

---

## CSS Variables

```css
:root {
  /* Color — 純粋なグレースケール */
  --color-black:  #000000;
  --color-900:    #1A1A1A;
  --color-700:    #4D4D4D;
  --color-500:    #808080;
  --color-300:    #B3B3B3;
  --color-100:    #E6E6E6;
  --color-50:     #F5F5F5;
  --color-white:  #FFFFFF;

  /* Typography */
  --font-serif:  'Noto Serif JP', Georgia, serif;
  --font-sans:   -apple-system, 'Hiragino Sans', sans-serif;
  --font-mono:   'DM Mono', 'Courier New', monospace;

  /* Type Scale — Minor Third (1.2) */
  --text-xs:    0.694rem;  /* 11px — ラベル・キャプション */
  --text-sm:    0.833rem;  /* 13px — 補助テキスト */
  --text-base:  1.000rem;  /* 16px — 本文（基準） */
  --text-md:    1.200rem;  /* 19px — リード文・引用 */
  --text-lg:    1.440rem;  /* 23px — h3 */
  --text-xl:    1.728rem;  /* 28px — h2 */
  --text-2xl:   2.074rem;  /* 33px — h1（セクション） */
  --text-3xl:   2.488rem;  /* 40px — h1（ページ） */

  /* Leading */
  --leading-tight:  1.4;   /* 見出し */
  --leading-base:   1.85;  /* 本文（日本語） */
  --leading-loose:  2.1;   /* リード文・引用 */

  /* Tracking */
  --tracking-normal: 0.02em;
  --tracking-wide:   0.06em;

  /* Spacing — 8px grid */
  --sp-1:   0.5rem;   /*   8px */
  --sp-2:   1rem;     /*  16px */
  --sp-3:   1.5rem;   /*  24px */
  --sp-4:   2rem;     /*  32px */
  --sp-6:   3rem;     /*  48px */
  --sp-8:   4rem;     /*  64px */
  --sp-12:  6rem;     /*  96px */
  --sp-16:  8rem;     /* 128px */

  /* Layout */
  --max-w-prose: 68ch;
  --max-w-wide:  90ch;
  --max-w-full:  1200px;
}
```

---

## クイックリファレンス

### レイアウト
```
ページ背景           : background: var(--color-50)
コンテナ             : max-width: var(--max-w-full); margin: 0 auto; padding: 0 var(--sp-4)
本文コンテナ         : max-width: var(--max-w-prose)
セクション間隔       : padding: var(--sp-8) 0
区切り線             : 1px solid var(--color-300)
グリッド             : 12カラム, gap: var(--sp-4)
```

### テキスト
```
本文                 : font-family: var(--font-serif); font-weight: 300; color: var(--color-700); line-height: var(--leading-base)
強調                 : font-weight: 500; color: var(--color-900)
h1（ページ）         : font-size: var(--text-3xl); font-weight: 300; line-height: var(--leading-tight)
h2                   : font-size: var(--text-xl); font-weight: 400
h3                   : font-size: var(--text-lg); font-weight: 400
h4                   : font-size: var(--text-md); font-weight: 500
h5                   : font-size: var(--text-base); font-weight: 500
段落間               : margin-bottom: var(--sp-3)
```

### コンポーネント
```
ナビゲーション       : border-bottom: 1px solid var(--color-300); ブランド名 var(--font-sans) var(--text-sm) uppercase tracking-wide; リンク var(--color-700) hover:var(--color-900)

Page Header          : eyebrow var(--font-mono) var(--text-xs) var(--color-500) uppercase; h1 var(--text-3xl) weight 300; リード var(--text-md) var(--color-700); border-bottom: 1px solid var(--color-300)

Section              : label var(--font-mono) var(--text-xs) var(--color-500) uppercase; padding: var(--sp-8) 0; border-bottom: 1px solid var(--color-300)

Button（Primary）    : border: 1px solid var(--color-900); color: var(--color-900); background: transparent; hover→ bg var(--color-900) text var(--color-white); font var(--font-sans) var(--text-sm); padding: var(--sp-1) var(--sp-3); border-radius: 0

Button（Ghost）      : border: 1px solid var(--color-300); color: var(--color-700); hover→ border var(--color-900) color var(--color-900); border-radius: 0

Card Grid            : gap: 1px; background: var(--color-300)（目地がボーダー）; カード bg var(--color-white) padding var(--sp-4); meta var(--font-mono) var(--text-xs) var(--color-500) uppercase

Tag / Label          : border: 1px solid var(--color-300); font var(--font-mono) var(--text-xs) var(--color-500); padding: 2px var(--sp-1); border-radius: 0

Blockquote           : border-left: 1px solid var(--color-900); font-size: var(--text-md); color: var(--color-700); cite var(--font-mono) var(--text-sm) var(--color-500)

Table                : ヘッダー var(--font-mono) var(--text-xs) uppercase var(--color-500); ヘッダー下 1px solid var(--color-900); 行間 1px solid var(--color-300); セル var(--text-sm) var(--color-700)

Notice / Callout     : border-left: 2px solid var(--color-900); background: var(--color-white); padding: var(--sp-3); text var(--text-sm) var(--color-700)

Definition List      : dt var(--font-mono) var(--text-xs) var(--color-500) uppercase tracking-wide; dd var(--color-700) margin-top var(--sp-1); 項目間 var(--sp-3)

Figure               : placeholder bg var(--color-300) aspect-ratio 16/9; caption var(--text-sm) var(--color-500) italic
```

### セマンティックHTML方針
```
クラスレスに近い設計。HTMLタグを正しく使えば最低限の体裁が整う。
<nav> <header> <main> <section> <article> <aside> <footer> <figure> <blockquote> <dl>
```

---

## このシステムが定義しないもの

デザイナーが自由に決定する：
- ブランドカラー / 書体 / アイコン / モーション / 角丸 / 影 / イラスト・写真スタイル / ダークモード

---

## 禁止パターン

| 禁止 | 理由 |
|------|------|
| `border-radius` > 0 | 角丸は使わない |
| `box-shadow` | 影は使わない |
| グラデーション | 装飾は使わない |
| グレースケール以外の色 | ブランドカラーはDS外で定義 |
| `font-weight: 600` 以上 | 最大500まで |
| アニメーション / transition | 動きは定義しない |
