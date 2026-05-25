# MAISON ROUGE — beauty-salon/rouge Spec

**Status:** Approved
**Author:** torifo
**Created:** 2026-05-25
**Updated:** 2026-05-25

---

## 1. Overview

### Problem Statement
ブライダル美容を扱う Web サイトは、結婚式という人生イベントの強さに引きずられ、煽り CTA（「今だけ」「先着」「キャンペーン」）と過剰な笑顔のビフォーアフター訴求に陥りやすい。一方で「フランス・オートクチュール」のような審美眼を持つ花嫁にとって、それらは品位を欠き、選択肢から外れる根拠となる。日本語圏の Web 上に「パリのメゾンで身を整える儀式」を Web で表現する語彙が、ブライダル美容領域では確立されていない。

### Goal
架空ブランド **MAISON ROUGE**（メゾン・ルージュ）を、「フェイシャル・ボディの定期手入れ」と「結婚式に向けた花嫁準備」を同格に並べたパリ系オートクチュール・エステとして実装する。Diptyque の still-life 編集感、Guerlain / Sisley の serif italic と低彩度写真、Lancôme の cream-champagne 基調を骨格にしつつ、ベルベット赤を「布の質感」として CSS で表現する。「結婚式までの数ヶ月、ここで自分を整える」という時間感覚を、装飾ではなくタイポグラフィ・素材感・余白で成立させる。

### Non-Goals
- 「○ヶ月で −5kg」「ブライダル特別価格」等の煽り CTA／割引キャンペーン訴求
- 顔の正面フル写真・ビフォーアフター比較・モデルの笑顔強調
- 価格表の前面化（コース構成は記すが、来店時の総額シミュレーションは持たない）
- カート／決済／オンライン予約フォーム（問い合わせ・来店相談のみ）
- 鮮やかな赤（純色赤 `#ff0000` 系）。あくまでベルベットの落ち着いた赤
- 装飾的なハート・ピンク多用・キラキラ加工（カジュアル婚活サイトの空気）

---

## 2. User Stories

| ID | Persona | Want to | So that |
|----|---------|---------|---------|
| US-01 | 31歳・外資系広報・式半年前の花嫁 | 半年で計画的に肌・身体を整えてくれるメゾンを探したい | 当日に自分のピークを合わせられる |
| US-02 | 28歳・大学院研究員・式 1 年前 | 「派手な式場併設」ではなく、独立した審美眼のあるメゾンに通いたい | 自分のペースと美意識を守れる |
| US-03 | 35歳・経営者の妻・定期客 | 結婚後も同じメゾンで顔・身体を季節ごとに手入れしたい | 通い続ける「儀式」として位置付けられる |
| US-04 | 26歳・式は未定だが審美感度が高い | フェイシャルだけでも一度通って雰囲気を見たい | 場違いにならず、長期で関われるか判断できる |

---

## 3. Functional Requirements

| ID | Requirement | Priority |
|----|-------------|----------|
| FR-01 | クリーム `#f1eadd` 基調 + ベルベット赤 `#6b1f2a` のヒーロー、Playfair Display Italic の大型見出し | P0 |
| FR-02 | ヒーロー写真は薔薇 still-life または横顔／唇半分のクローズアップ 1 枚、低彩度で重厚に | P0 |
| FR-03 | LE SOIN（フェイシャル）／LE CORPS（ボディ）／LE MARIAGE（ブライダル準備）の 3 領域を同格に並べる | P0 |
| FR-04 | LE MARIAGE は「12 ヶ月前／6 ヶ月前／3 ヶ月前／前日」の時間軸でケアの流れを縦に提示。割引・パック価格は出さない | P0 |
| FR-05 | LES SOINS（施術一覧）：Soin Velours（ベルベット・フェイシャル）／Soin Rose（薔薇水トリートメント）／Soin Champagne（ブライダル直前光輝ケア）等、フランス語＋日本語の二言語名で 6〜8 件 | P0 |
| FR-06 | LA MAISON（メゾン紹介）：施術室の調度、薔薇水・蜜蝋ろうそく・ベルベットのドレープ等の素材物語を 1 ページぶんの編集記事として提示 | P0 |
| FR-07 | NOTES（メゾンの作法・所要時間・お召し物・写真撮影の可否等）を品位ある列挙で明記 | P1 |
| FR-08 | RÉSERVATION（ご予約）：完全予約制・面談式である旨を一文で。具体的な料金は記載するが「ご相談」を主軸とする | P0 |
| FR-09 | ナビ固定上部、リンクホバー時に老金 `#9d7e3c` の hairline が左→右へ 0.6 秒で伸びる | P1 |
| FR-10 | 背景クリーム面に微細なノイズテクスチャ（ベルベットの起毛感）を CSS で重ね、赤領域には縦方向の微グラデを敷いて布の陰影を作る | P0 |
| FR-11 | 840px 以下で 1 カラム化、LE MARIAGE の時間軸は縦タイムラインに変形 | P0 |
| FR-12 | フッターに小さく仏語の一文 "L'art de se préparer."（自分を整える芸術） | P1 |

---

## 4. Key Design Decisions

| Decision | Chosen | Rationale | Rejected |
|----------|--------|-----------|----------|
| 基調色 | クリーム `#f1eadd` + ベルベット赤 `#6b1f2a` + シャンパン `#d4c5a9` + 老金 `#9d7e3c` | パリのオートクチュール・メゾンの室内（薔薇／ベルベットドレープ／蜜蝋）の色温度。赤は純色を外し血色寄りに落とす | 鮮やかなワインレッド `#8b0000`、ピンク基調、純白背景 |
| ベルベットの「布」表現 | CSS の `background-image` で SVG noise（feTurbulence）を `mix-blend-mode: overlay` で重ね、赤領域は `linear-gradient` を縦方向に 3 stop（`#5a1a23`→`#6b1f2a`→`#5a1a23`）で敷いて布の陰影を演出 | 画像を使うと重く、ベタ塗りでは紙の質感に見える。CSS だけで「布」を匂わせ、画像帯域を写真に回す | 画像テクスチャ全面敷き、`box-shadow` 多用、グラスモーフィズム |
| 見出し書体（欧文） | Playfair Display Italic + Cormorant Garamond Italic | Italic の流れがオートクチュールの筆記体伝統と一致。Playfair は display サイズで揺れの強さが効き、Cormorant は中見出しで上品さが残る | Bodoni（硬すぎる）、Didot（noir で使用予定なので回避）、Serif の roman 体のみ（メゾンの「揺らぎ」が出ない） |
| 見出し書体（和文） | Noto Serif JP 500 + Klee One（キャプション・引用） | Noto Serif JP で格を、Klee One で「手書きのカード」の温度を入れ、メゾンの手紙のような声を作る | Shippori Mincho B1（wabi 用予定）、Yu Mincho 単独（温度が足りない） |
| 写真 | 顔は半分のみ（唇・首筋・横顔）。フル正面顔は禁止。薔薇 / ベルベット / 蜜蝋 / シャンパングラス / 布のドレープの still-life を中心に | フル正面顔は「ブライダル広告」の文法。半分にすることで観る側の想像の余地が残り、品位とエレガンスが両立する | モデルの集合写真、笑顔強調、ビフォーアフター並置 |
| 装飾 | 老金 `#9d7e3c` の hairline（0.5–1px）と oval frame（楕円フレーム）。装飾的アイコン・絵文字は禁 | Diptyque のオーバル意匠と French apothecary の細線意匠を参照。線 1 本で格を出す | 金箔風グラデ、ハートアイコン、薔薇のイラスト乱用 |
| コピートーン | 仏語の短いフレーズ + 丁寧な日本語補足。CTA は「ご予約」「お問合せ」「Réservation」 | "Maison de beauté" の語彙で寡黙な大人の声を作る。煽り語は構造的に排除 | 「今だけ」「特別」「限定」「特典」 |
| ブライダル領域の扱い | LE SOIN / LE CORPS と同格に LE MARIAGE を 3 番目に置く。時間軸（12 ヶ月→前日）で語る | 「ブライダル特化サロン」ではなく「メゾンに通った先にブライダルもある」という順序にすることで、結婚後も通える日常性を保つ | LE MARIAGE をヒーロー直下に置く、ブライダル料金パック前面化 |
| アニメーション | reveal 0.8 秒・ease-out、hover は hairline の左→右伸び + 文字色を `#6b1f2a` へ。視差・スケール拡大は禁 | "灯がともる" 感覚をベルベットの重みで再現。激しい動きは布の重厚さと矛盾 | 視差スクロール、ホバー時のスケール 1.05、フェードズーム |
| `prefers-reduced-motion` | 全アニメーション無効化 + hairline は最初から表示 | アクセシビリティ要件と高級感の両立 | 部分的に無効化 |

---

## 5. Design System

```css
/* Palette — French velvet maison */
--cream:     #f1eadd;   /* base, ベルベット起毛のクリーム面 */
--cream-2:   #ebe2cf;   /* セクション分割 / カード背景 */
--velvet:    #6b1f2a;   /* 主役のベルベット赤 */
--velvet-d:  #5a1a23;   /* 布陰影グラデの暗側 */
--velvet-l:  #7a2632;   /* hover 時の小さな明度差 */
--champagne: #d4c5a9;   /* シャンパン、補助面 */
--gold-old:  #9d7e3c;   /* 老金、hairline と差し色 */
--ink:       #2a1f1d;   /* 本文（純黒ではなく葡萄酒下の影色） */
--ink-mute:  #6e5e58;   /* キャプション・補足 */
--line:      #c8b89c;   /* クリーム面上の細線 */

/* Typography */
--font-display: 'Playfair Display', 'Cormorant Garamond', 'Noto Serif JP', serif;
--font-display-it: 'Playfair Display', serif;   /* italic 指定で使う */
--font-serif-jp: 'Noto Serif JP', serif;
--font-hand:   'Klee One', 'Noto Serif JP', serif;  /* キャプション・引用・手紙 */
--font-body:   'Cormorant Garamond', 'Noto Serif JP', serif;
--font-meta:   'Cormorant Garamond', 'Noto Serif JP', serif;

/* Scale */
--fs-hero:   clamp(56px, 9vw, 144px);   /* Playfair Italic */
--fs-h2:     clamp(32px, 4vw, 64px);
--fs-h3:     clamp(22px, 2.2vw, 32px);
--fs-body:   17px;
--fs-cap:    13px;
--lh-body:   1.9;
--lh-disp:   1.05;
--tracking-display: 0.01em;
--tracking-eyebrow: 0.32em;  /* "LE SOIN" 等の小見出し */
--tracking-body:    0.04em;

/* Layout */
--max:    1180px;
--pad-x:  clamp(24px, 5vw, 80px);
--gap:    clamp(64px, 10vh, 160px);

/* Motion */
--ease:   cubic-bezier(.22,.61,.36,1);
--dur:    .8s;

/* Velvet texture — 布の質感を CSS で */
/* クリーム面: SVG noise + overlay で起毛 */
--noise-cream: url("data:image/svg+xml;utf8,<svg xmlns='http://www.w3.org/2000/svg' width='240' height='240'><filter id='n'><feTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='2' stitchTiles='stitch'/><feColorMatrix values='0 0 0 0 0.15  0 0 0 0 0.12  0 0 0 0 0.10  0 0 0 0.06 0'/></filter><rect width='100%25' height='100%25' filter='url(%23n)'/></svg>");
/* 赤面: 縦グラデで布の襞を演出 */
--velvet-fold: linear-gradient(180deg, var(--velvet-d) 0%, var(--velvet) 45%, var(--velvet-d) 100%);
```

### 構造的ディテール

```css
/* クリーム背景に微細なノイズを重ねる */
body {
  background: var(--cream);
  background-image: var(--noise-cream);
  background-blend-mode: multiply;
}

/* ベルベット赤セクションは縦グラデで布の陰影 */
.section--velvet {
  background: var(--velvet-fold);
  color: var(--cream);
}

/* hairline は左→右に伸びる */
.nav a::after {
  content: '';
  display: block;
  height: 0.5px;
  background: var(--gold-old);
  width: 0;
  transition: width var(--dur) var(--ease);
}
.nav a:hover::after { width: 100%; }
```

### セクション構成

```text
index.html
├── header.nav                 クリーム背景・固定・スクロール時に薄い hairline 出現
├── section.hero               薔薇 still-life or 横顔半分 + Playfair Italic で "L'art de se préparer."
├── section.philosophy         メゾンの哲学 2〜3 段落、Noto Serif JP の長文
├── section.le-soin            LE SOIN — フェイシャル（Soin Velours / Soin Rose 等）
├── section.le-corps           LE CORPS — ボディ
├── section.le-mariage         LE MARIAGE — 12mo→6mo→3mo→前日 の縦タイムライン
├── section.la-maison          LA MAISON — 室内・素材物語（編集記事）
├── section.notes              NOTES — メゾンの作法
├── section.reservation        RÉSERVATION — 完全予約制 / 面談式
└── footer                     "L'art de se préparer." と所在地
```

### Imagery guideline

- Unsplash の外部 URL、`loading="lazy"`、`alt` は日本語で内容を記述
- 被写体は **薔薇／ベルベットのドレープ／蜜蝋ろうそく／薔薇水の瓶／シャンパングラス／横顔半分／首筋／唇のクローズアップ／真鍮の道具**
- フル正面顔・笑顔・ビフォーアフター・モデル集合写真は禁
- 低彩度・室内ランプ光・縦長 portrait 比率を基本に

---

## 6. References

### 参照サイト
- [Sisley Paris](https://www.sisley-paris.com/) — フランス・オートクチュール系の象徴、"Phyto Rouge Velvet" のような vocabulary
- [Diptyque](https://www.diptyqueparis.com/) — French apothecary、oval frame・cream-red 基調・still-life 編集感
- [Guerlain](https://www.guerlain.com/) — メゾン・ド・ボーテの典型、ornamental gold 意匠
- [Lancôme](https://www.lancome.com/) — Continental design principles、"L'Absolu Rouge" の French nomenclature
- [TAKAMI BRIDAL](https://takamibridal.com/) — 国内ブライダル美容の参照（時間軸でケアを語る構造を参考）

### Google Fonts
- [Playfair Display](https://fonts.google.com/specimen/Playfair+Display) — display serif (italic 主用)
- [Cormorant Garamond](https://fonts.google.com/specimen/Cormorant+Garamond) — body / sub-display serif italic
- [Noto Serif JP](https://fonts.google.com/noto/specimen/Noto+Serif+JP) — 和文見出し
- [Klee One](https://fonts.google.com/specimen/Klee+One) — キャプション・引用（手紙の温度）

### 内部参照
- [PLAN_BEAUTY_SALON.md](../../PLAN_BEAUTY_SALON.md) — シリーズ全体の上位計画
- [fitness-gym/salon/spec.md](../../fitness-gym/salon/spec.md) — serif display × ゴールドの構造的参考
- [stationery/mono/spec.md](../../stationery/mono/spec.md) — spec フォーマット基準
