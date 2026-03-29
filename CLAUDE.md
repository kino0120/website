# kinotos — サイト設計ガイド

## コンセプト

**「感性を、定量化する。」**

Data Scientist である kinotos が、主観的な体験（サウナ・音楽・コーヒー・クラフトビール）を客観的に記述・分析・共有するための個人サイト。
感性と数字の緊張関係そのものが、このサイトのアイデンティティ。

---

## デザイン世界観

### ビジュアルテイスト
アルバムジャケットから読み取った美意識を基準にする：
- **シュルレアリスム的コラージュ** — 植物・解剖学・ヴィンテージ写真の混在
- **水中・霧の中のような霞感** — ぼんやりとした境界線、夢の中にいる感覚
- **有機的 × 構造的** — 生き物的な曲線と、データの格子が共存する
- **静謐でメランコリック** — 主張しすぎない、余白に意味がある

### カラーパレット
```
--bg:       #0d0c0b   /* ウォームダーク。純粋な黒ではなく、わずかに体温を持つ */
--surface:  #131210
--border:   #252320
--text:     #ddd8cf   /* クリームがかったホワイト */
--muted:    #5a5650   /* 枯れ草色のグレー */
--accent:   #8faab3   /* ダスティブルー — 水風呂、水中、霧 */
--rose:     #c4908a   /* ミュートローズ — 植物、花、温度 */
```

### タイポグラフィ
- フォント：Inter（システムフォントにフォールバック）
- 見出し：font-weight 200〜300、letter-spacing マイナス。大きく・軽く・詩的に
- 本文：12〜15px、color: var(--muted)、line-height 1.8〜2.0
- ラベル：11px、letter-spacing 0.2em、text-transform uppercase

### アニメーション・インタラクション
- **ヌルヌル感が命** — transition は必ず ease、0.3s〜0.6s
- カスタムカーソル（ドット + 遅延リング）
- スクロールで要素がふわっとフェードアップ（IntersectionObserver）
- ナビゲーションはスクロールでフロストガラスに変化
- フィルムグレイン + ビネット で写真的な質感
- マーキーで興味・キーワードが流れる

### やってはいけないこと
- 鮮やかすぎる色（高彩度はNG）
- アニメーションが速すぎる・派手すぎる
- 情報を詰め込みすぎる（余白は意味を持つ）
- コーポレートっぽい表現・レイアウト

---

## サイト構成

| セクション | 内容 |
|---|---|
| Hero | `kinotos` の名前、コンセプト文、フェードインアニメーション |
| Marquee | Sauna / Music / Coffee / Craft Beer / Data Science / 感性×数値 |
| 01 Interests | 4つの興味領域 + Quantify Metrics |
| 02 Writing | note.com の記事リンク一覧 |
| 03 Products & Apps | 開発中・構想中のアプリ |
| 04 About | データサイエンティストとしての自己紹介 |
| Footer | © kinotos / note / GitHub リンク |

---

## 技術スタック

- 純粋な HTML / CSS / JS（フレームワークなし）
- 単一ファイル `index.html`
- GitHub Pages でホスティング予定（`main` ブランチ）

---

## コンテンツ追加のパターン

### note 記事を追加するとき
```html
<a href="https://note.com/..." target="_blank" class="writing-item">
  <div class="writing-item-left">
    <p class="writing-tag">Sauna / Coffee など</p>
    <p class="writing-title">記事タイトル</p>
  </div>
  <span class="writing-arrow">→</span>
</a>
```

### プロダクトを追加するとき
```html
<div class="work-card">
  <div class="work-card-placeholder">スクリーンショットやアイキャッチ</div>
  <h3 class="work-card-title">プロダクト名</h3>
  <p class="work-card-desc">説明文</p>
  <span class="work-tag">公開中 / 開発中 / 構想中</span>
</div>
```
