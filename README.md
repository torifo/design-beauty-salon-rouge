# MAISON ROUGE — beauty-salon/rouge

design シリーズ第 8 弾「高級感漂う美容サロン」の 4 ペルソナのうち **rouge**。架空のフランス系オートクチュール・メゾン・ド・ボーテ **MAISON ROUGE** の Web 実装。

## ペルソナ

- **業態**: フェイシャル × ボディ × ブライダル準備の総合メゾン
- **美学**: パリ・オートクチュール、ベルベットの布、薔薇水、蜜蝋、シャンパン
- **配色**: クリーム `#f1eadd` + ベルベット赤 `#6b1f2a` + シャンパン `#d4c5a9` + 老金 `#9d7e3c`
- **書体**: Playfair Display Italic + Cormorant Garamond Italic + Noto Serif JP 500+ + Klee One（キャプション・引用のみ）

## サイト構成

1. **Hero** — 薔薇 still-life の縦長写真 + Playfair Italic で *"L'art de se préparer."*
2. **Philosophy** — メゾンの哲学（Noto Serif JP の長文 3 段落）
3. **Le Soin** — フェイシャル 4 種（Velours / Rose / Champagne / Cire d'Abeille）
4. **Le Corps** — ボディ 3 種、ベルベット赤のセクション
5. **Le Mariage** — 12ヶ月→6ヶ月→3ヶ月→前日 の縦タイムライン（パック価格・煽り CTA は構造的に排除）
6. **La Maison** — 室内・素材の編集記事（薔薇水・蜜蝋・ベルベット・真鍮）
7. **Notes** — メゾンの作法（営業時間・予約・お召し物・静寂・撮影・付き添い）
8. **Réservation** — 完全予約制・面談式、ベルベット赤のセクション
9. **Footer** — *"L'art de se préparer."*

## 中核技術

- **ベルベットの布の CSS 表現**: SVG `feTurbulence` ノイズ × `mix-blend-mode: overlay` × 縦 3-stop linear-gradient で純 CSS で布の起毛と陰影を出す。画像不使用
- **`@supports (mix-blend-mode: overlay)`** で Safari のフォールバック
- **`prefers-reduced-motion`**: 全アニメ無効化 + hairline は最初から表示
- **840px breakpoint**: 1 カラム化 + LE MARIAGE は縦タイムラインに変形（モバイル時は rail を非表示にして stage の縦並びへ）

## 開発

純 HTML + CSS + 最小 JS（nav scroll state と IntersectionObserver reveal のみ）。ビルド不要。`index.html` を開けば動く。

## デプロイ

- GitHub Pages + カスタムドメイン
- `CNAME`: `design.beauty-salon-rouge.riumu.net`
- `.nojekyll` で Jekyll を無効化

## 関連リンク

- [spec.md](./spec.md) — 仕様
- [DESIGN_LEARNINGS.md](./DESIGN_LEARNINGS.md) — 実装で得た知見
- 親シリーズ計画: `../PLAN_BEAUTY_SALON.md`
- 姉妹ペルソナ: `../noir/` `../ivoire/` `../wabi/`

## 注意

すべて架空のブランド・施術・料金です。実在の人物・店舗・サービスとは無関係です。写真は Unsplash の外部 URL を `loading="lazy"` で参照しています。


## Install as a skill / スキルとして導入

This repo ships a cross-agent **`SKILL.md`** (open standard) usable by both Claude Code and Codex CLI as a design-reference skill. Link the repo into the agent's skills directory:

このリポジトリは Claude Code / Codex CLI 共通の **`SKILL.md`**（オープン標準）を同梱し、デザイン参照スキルとして使えます。

```bash
# Claude Code
ln -s "$(pwd)" ~/.claude/skills/design-beauty-salon-rouge
# Codex CLI
ln -s "$(pwd)" ~/.codex/skills/design-beauty-salon-rouge
```

Restart the agent; it is matched automatically by the skill's `description` (skill name: `design-beauty-salon-rouge`). / エージェント再起動後、`description` に基づき自動マッチします。
