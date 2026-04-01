# Plain Design System
**Version 0.1 — For Designer Reference**

> このデザインシステムは「主張しない」ことを目的に設計されています。
> コンテンツの構造と階層を伝えるための最小限のシステムです。
> デザイナーはここから自由に出発してください。

---

## 1. 設計思想

### 原則

**Invisible Design（見えないデザイン）**
デザインシステム自体が前に出ず、コンテンツの構造だけが伝わる状態を目指す。

**Structure First（構造を先に）**
色・形・装飾より先に、情報の階層と関係性を明示する。タイポグラフィと余白だけで読める状態を基準とする。

**Open for Interpretation（解釈の余地）**
このシステムは未完成である。ブランドカラー・書体・アイコン・モーションは意図的に定義しない。デザイナーがゼロから決定できる余地を残す。

### 制約

- 色はグレースケールのみ（Black / White / Gray）
- 装飾要素（影・グラデーション・角丸）は使わない
- アニメーションは定義しない
- フォントは目立たないもの、または未定義

---

## 2. Color

グレースケールのみ。温かみ・冷たさのない、中立的なグレー。

| Token              | Hex       | RGB               | 用途                               |
|--------------------|-----------|-------------------|------------------------------------|
| `--color-black`    | `#000000` | 0, 0, 0           | 最強調。見出し・ボーダーアクセント |
| `--color-900`      | `#1A1A1A` | 26, 26, 26        | 本文テキスト（基本）               |
| `--color-700`      | `#4D4D4D` | 77, 77, 77        | 補助テキスト・説明文               |
| `--color-500`      | `#808080` | 128, 128, 128     | プレースホルダー・無効状態         |
| `--color-300`      | `#B3B3B3` | 179, 179, 179     | ボーダー・区切り線                 |
| `--color-100`      | `#E6E6E6` | 230, 230, 230     | 背景（サーフェス）                 |
| `--color-50`       | `#F5F5F5` | 245, 245, 245     | 背景（ベース）                     |
| `--color-white`    | `#FFFFFF` | 255, 255, 255     | 純白。カード背景・反転テキスト     |

### 使用ルール

- テキストと背景のコントラスト比は **4.5:1 以上**（WCAG AA準拠）
- `--color-900` on `--color-white` → 対比率 約17:1（本文に使用）
- `--color-700` on `--color-white` → 対比率 約7:1（補助テキストに使用）
- `--color-500` on `--color-white` → 対比率 約4.5:1（最低限。プレースホルダーのみ）
- ブランドカラーは **このシステムでは定義しない**

---

## 3. Typography

### フォント定義

| Role      | Family（候補）                                    | 特性                         |
|-----------|--------------------------------------------------|------------------------------|
| 本文      | `Noto Serif JP`, Georgia, serif                  | 読みやすさ優先。主張しない。 |
| UI・ラベル | System UI `-apple-system`, Hiragino Sans, sans-serif | ナビ・ボタン・タグ等         |
| 補助      | `DM Mono`, Courier New, monospace                | 日付・カテゴリ・コード等     |

> **Note:** フォント選定はデザイナーに委ねる。上記はあくまで「機能のプレースホルダー」。

### タイプスケール（Minor Third 比率 1.2 基準）

| Token        | rem      | px相当 | 用途                     |
|--------------|----------|--------|--------------------------|
| `--text-xs`  | 0.694rem | 11px   | ラベル・キャプション・メタ |
| `--text-sm`  | 0.833rem | 13px   | 補助テキスト・フッター     |
| `--text-base`| 1.000rem | 16px   | 本文（基準）               |
| `--text-md`  | 1.200rem | 19px   | リード文・引用             |
| `--text-lg`  | 1.440rem | 23px   | h3                        |
| `--text-xl`  | 1.728rem | 28px   | h2                        |
| `--text-2xl` | 2.074rem | 33px   | h1（セクション）           |
| `--text-3xl` | 2.488rem | 40px   | h1（ページ）               |

### ウェイト

| 値  | 用途                       |
|-----|----------------------------|
| 300 | 本文・説明文（ライト）     |
| 400 | 通常見出し・リンク         |
| 500 | 強調・ラベル・ボタン       |

### 行間・字間

| Token              | 値    | 用途                         |
|--------------------|-------|------------------------------|
| `--leading-tight`  | 1.4   | 見出し                       |
| `--leading-base`   | 1.85  | 本文（日本語）               |
| `--leading-loose`  | 2.1   | リード文・引用               |
| `--tracking-wide`  | 0.06em| ラベル・uppercaseテキスト    |
| `--tracking-normal`| 0.02em| UI テキスト全般              |

---

## 4. Spacing

8px グリッドベース。

| Token     | rem    | px  |
|-----------|--------|-----|
| `--sp-1`  | 0.5rem | 8px |
| `--sp-2`  | 1rem   | 16px|
| `--sp-3`  | 1.5rem | 24px|
| `--sp-4`  | 2rem   | 32px|
| `--sp-6`  | 3rem   | 48px|
| `--sp-8`  | 4rem   | 64px|
| `--sp-12` | 6rem   | 96px|
| `--sp-16` | 8rem   | 128px|

---

## 5. Layout

### コンテナ幅

| Token           | 値     | 用途                     |
|-----------------|--------|--------------------------|
| `--max-w-prose` | 68ch   | 本文・読み物コンテンツ   |
| `--max-w-wide`  | 90ch   | 表・複数カラム           |
| `--max-w-full`  | 1200px | ページ全体の最大幅       |

### グリッド

- 基本：12カラムグリッド（実装はflexまたはgrid）
- ガター：`--sp-4`（32px）
- サイドパディング：`--sp-4` / モバイルは `--sp-3`

---

## 6. Components

### 6-1. Navigation

```
[ブランド名]                           [リンク] [リンク] [リンク]
```

- 下線ボーダー：`1px solid --color-300`
- ブランド名：`--font-sans`, `--text-sm`, uppercase, `letter-spacing: --tracking-wide`
- リンク：`--font-sans`, `--text-sm`, color `--color-700`
- リンク hover：color `--color-900`

---

### 6-2. Page Header

```
[eyebrow — モノスペース小文字]
[大見出し h1]
[リード文 — 本文より少し大きく]
```

- eyebrow：`--font-mono`, `--text-xs`, `--color-500`, uppercase, tracking wide
- h1：`--text-3xl`, weight 300, `--leading-tight`
- リード文：`--text-md`, `--color-700`, `--leading-loose`
- 下にボーダー：`1px solid --color-300`

---

### 6-3. Section

```
[section-label — モノスペース]
[h2]
[content]
```

- section-label：`--font-mono`, `--text-xs`, `--color-500`, uppercase, tracking wide
- h2：`--text-xl`, weight 400
- セクション間ボーダー：`1px solid --color-300`
- セクション縦パディング：`--sp-8`

---

### 6-4. Headings

| 要素 | サイズ        | Weight | 用途               |
|------|---------------|--------|--------------------|
| h1   | `--text-3xl`  | 300    | ページタイトル     |
| h2   | `--text-xl`   | 400    | セクション見出し   |
| h3   | `--text-lg`   | 400    | サブセクション     |
| h4   | `--text-md`   | 500    | ブロック見出し     |
| h5   | `--text-base` | 500    | 小見出し           |

---

### 6-5. Body Text

- font：`--font-serif`, weight 300
- color：`--color-700`
- 段落間マージン：`--sp-3`
- `<strong>`：weight 500, color `--color-900`

---

### 6-6. Blockquote

```
│ 引用テキスト（イタリック、少し大きめ）
│
│ — 出典
```

- 左ボーダー：`1px solid --color-900`（細くシャープに）
- 本文より少し大きく：`--text-md`
- color：`--color-700`
- cite：`--font-mono`, `--text-sm`, `--color-500`

---

### 6-7. Table

```
COLUMN A        COLUMN B        COLUMN C
——————————————————————————————————————————
Value           Value           Value
Value           Value           Value
```

- ヘッダー：`--font-mono`, `--text-xs`, uppercase, `--color-500`
- ヘッダー下：`1px solid --color-900`
- 行間：`1px solid --color-300`
- セルパディング：`--sp-2` 上下、右のみ
- テキスト：`--text-sm`, `--color-700`

---

### 6-8. Card Grid

- グリッド：`gap: 1px; background: --color-300`（目地をボーダーとして使う）
- カード背景：`--color-white`
- カードパディング：`--sp-4`
- card-meta：`--font-mono`, `--text-xs`, `--color-500`, uppercase
- カードタイトル：h4
- カード本文：`--text-sm`, `--color-700`

---

### 6-9. Button

```
[ ラベルテキスト ]       ← Primary
[ ラベルテキスト ]       ← Ghost
```

**Primary**
- border：`1px solid --color-900`
- color：`--color-900`
- background：transparent
- hover：background `--color-900`, color `--color-white`

**Ghost**
- border：`1px solid --color-300`
- color：`--color-700`
- hover：border `--color-900`, color `--color-900`

- フォント：`--font-sans`, `--text-sm`, `letter-spacing: 0.04em`
- パディング：`--sp-1` × `--sp-3`
- 角丸：**なし**（`border-radius: 0`）

---

### 6-10. Tag / Label

```
[ CATEGORY ]
```

- border：`1px solid --color-300`
- font：`--font-mono`, `--text-xs`, `--color-500`
- パディング：`2px --sp-1`
- 角丸：**なし**

---

### 6-11. Notice / Callout

```
┃ お知らせテキスト
```

- 左ボーダー：`2px solid --color-900`
- background：`--color-white`
- パディング：`--sp-3`
- テキスト：`--text-sm`, `--color-700`

---

### 6-12. Definition List

```
LABEL
  Value text

LABEL
  Value text
```

- dt：`--font-mono`, `--text-xs`, `--color-500`, uppercase, tracking wide
- dd：`--color-700`, margin-top `--sp-1`
- 項目間マージン：`--sp-3`

---

### 6-13. Figure / Image

```
┌──────────────────────────────────────┐
│                                      │
│          IMAGE PLACEHOLDER           │
│                                      │
└──────────────────────────────────────┘
キャプションテキスト（イタリック）
```

- プレースホルダー背景：`--color-300`
- アスペクト比：16:9（基本）
- キャプション：`--text-sm`, `--color-500`, italic

---

## 7. Semantic HTML の方針

このシステムは **クラスレスに近い設計** を目指す。
HTMLのタグを正しく使えば、最低限の体裁が整う状態を基準とする。

| HTML要素     | 対応する役割                  |
|--------------|-------------------------------|
| `<nav>`      | ナビゲーション                |
| `<header>`   | ページ・セクションヘッダー    |
| `<main>`     | メインコンテンツ              |
| `<section>`  | コンテンツブロック            |
| `<article>`  | 独立したコンテンツ            |
| `<aside>`    | 補足・サイドバー              |
| `<footer>`   | フッター                      |
| `<figure>`   | 画像・図表                    |
| `<blockquote>`| 引用                         |
| `<dl>`       | 定義リスト（会社概要等）      |

---

## 8. このシステムが定義しないもの

デザイナーが自由に定義してよい項目：

- **ブランドカラー** — アクセントカラー・プライマリカラー
- **書体** — ブランドに合ったフォントファミリー
- **アイコン** — スタイル・ライブラリの選定
- **モーション** — トランジション・アニメーション
- **角丸** — `border-radius`の方針
- **影** — `box-shadow`の使用可否
- **イラスト・写真スタイル** — ビジュアルトーン
- **ダークモード** — 対応するかどうか含めて

---

## 9. CSS Variables（実装リファレンス）

```css
:root {
  /* Color */
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

  --text-xs:    0.694rem;
  --text-sm:    0.833rem;
  --text-base:  1.000rem;
  --text-md:    1.200rem;
  --text-lg:    1.440rem;
  --text-xl:    1.728rem;
  --text-2xl:   2.074rem;
  --text-3xl:   2.488rem;

  --leading-tight:  1.4;
  --leading-base:   1.85;
  --leading-loose:  2.1;

  --tracking-normal: 0.02em;
  --tracking-wide:   0.06em;

  /* Spacing */
  --sp-1:   0.5rem;
  --sp-2:   1rem;
  --sp-3:   1.5rem;
  --sp-4:   2rem;
  --sp-6:   3rem;
  --sp-8:   4rem;
  --sp-12:  6rem;
  --sp-16:  8rem;

  /* Layout */
  --max-w-prose: 68ch;
  --max-w-wide:  90ch;
  --max-w-full:  1200px;
}
```

---

*Plain Design System v0.1 — This document is a living reference. Update as the system evolves.*
