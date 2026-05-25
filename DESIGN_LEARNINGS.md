# Design Learnings — MAISON ROUGE

## ベルベットを画像なしで「布」に見せる

「ベルベット赤」をベタ塗りに見せない試行で、最終的に三層を重ねた。縦 3-stop の `linear-gradient(#5a1a23 → #6b1f2a → #5a1a23)` で布の襞の陰影、SVG `feTurbulence` を `data:` URL ノイズ化、`mix-blend-mode: overlay` で乗算。Safari 旧版用に `@supports` でフォールバックを用意。

## ブライダルから煽りを構造で抜く

LE MARIAGE は CSS でなく情報構造で煽りを排除した。価格は LE SOIN にのみ置き、LE MARIAGE は 12mo→6mo→3mo→前日 の縦タイムラインに「自分のピークを当日に合わせる長い設計」として記述。CTA は「ご予約」ではなく「面談から」。Klee One の手紙的引用と Noto Serif JP 本文で、広告ではなくメゾンからの招待状の温度を作った。Klee One は引用と署名のみに限定しないと一気にカジュアル婚活サイトに転落する。
