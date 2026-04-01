# GO OUT ヘッダーデモ プロジェクト

## 最重要ルール

**元サイト（https://web.goout.jp/）のデザインを徹底的に忠実に再現すること。**

新機能追加時も、まず元サイトのCSS・フォント・色・サイズ・余白を詳細に調査し、完全に再現した上で機能を追加する。「だいたい同じ」ではなく「完全に同じ」を目指す。

### 調査すべき項目
- フォントファミリー、サイズ、ウェイト、行間
- 色（RGB値で正確に）
- 余白（padding, margin）
- 要素サイズ（width, height）
- ボーダー（太さ、色、スタイル）
- レスポンシブ時の変化

---

## 概要

https://web.goout.jp/ のヘッダー部分をローカルで再現・カスタマイズしたデモファイル群。
C案ヘッダーを実際のWordPressページ構造に適用した静的HTMLサイトとして、GitHub Pagesで公開中。

## 公開URL

https://kitasinkita.github.io/gooutweb/

| ページ | URL |
|--------|-----|
| TOPページ | https://kitasinkita.github.io/gooutweb/ |
| PICKUP記事 | https://kitasinkita.github.io/gooutweb/pickup/464610/ |
| FASHION記事 | https://kitasinkita.github.io/gooutweb/fashion/473673/ |
| デモ: C案ライト | https://kitasinkita.github.io/gooutweb/demo-c-light.html |
| デモ: C案グレー | https://kitasinkita.github.io/gooutweb/demo-c-gray.html |
| デモ: C案ダーク | https://kitasinkita.github.io/gooutweb/demo-c-dark.html |

## ファイル構成

### 本番ページ（元サイト構造を再現）
| ファイル | 説明 |
|---------|------|
| `index.html` | TOPページ（PICKUP + 記事一覧 + サイドバー + フッター） |
| `pickup/464610/index.html` | PICKUP記事ページ（プロレス×ファッション座談会） |
| `fashion/473673/index.html` | NEWS/FASHION記事ページ（メレル×ジャーナルスタンダード）+ パンくずナビ |

### ヘッダーデモ（テーマ比較用）
| ファイル | 説明 |
|---------|------|
| `demo-c-light.html` | C案 ライトテーマ（薄茶色ナビ＋薄茶色サブカテゴリ） |
| `demo-c-gray.html` | C案 グレーテーマ（薄茶色ナビ＋濃いグレーサブカテゴリ） |
| `demo-c-dark.html` | C案 ダークテーマ（黒ナビ＋黒サブカテゴリ） |
| `demo-light.html` | 旧版 ライトテーマ（ドロップダウン式） |
| `demo-dark.html` | 旧版 ダークテーマ（ドロップダウン式） |
| `demo-article-breadcrumb.html` | 記事ページ + OCEANS風パンくずナビ |

### インフラ
| ファイル | 説明 |
|---------|------|
| `.github/workflows/pages.yml` | GitHub Pages 自動デプロイ（mainブランチpush時） |

**テーマ切り替え:** デモファイルは右下のボタンで3テーマを行き来可能

## C案の特徴

### PC版
- **メガドロップダウン**: NEWS/SNAPにマウスオーバーで横長バーにサブカテゴリ表示
- **カテゴリ**: NEWS, PICKUP, SPECIAL, SNAP, STORE, MAGAZINE, GO OUT CAMP
- **フォント**: Montserrat（元サイトと同じ）
- **ロゴ**: SVGで中央配置

### モバイル版（900px以下）
- **ナビバー常時表示**: ヘッダー直下にカテゴリ名を横一列で表示（横スクロール可能）
- **ハンバーガーメニュー**: 左からスライドインするサイドバー
- **アコーディオン**: NEWS/SNAPはタップで展開するサブカテゴリ
- **背景色**: rgb(222, 212, 200)（元サイトと同じベージュ）
- **メニュー順序**: PCと同じ（NEWS, PICKUP, SPECIAL, SNAP, STORE, MAGAZINE, GO OUT CAMP）
- **フォント統一**: 全項目14px/font-weight 700、アイコンなし

## 実装経緯

### Phase 1: 基本構造
- 元サイト（web.goout.jp）からヘッダー構造を分析
- ロゴSVGを抽出
- ナビゲーションカテゴリを実装

### Phase 2: C案（メガドロップダウン）
- サブカテゴリを横長バーで表示するスタイルを実装
- ライト/ダークの2テーマを作成
- Montserratフォントで元サイトと統一

### Phase 3: モバイル対応
- ハンバーガーメニューを追加
- スライドインサイドバーを実装
- オーバーレイとクローズボタン

### Phase 4: アコーディオン追加
- NEWS/SNAPにアコーディオン形式のサブカテゴリを追加
- 矢印アイコンの回転アニメーション
- max-heightによるスムーズな開閉

### Phase 5: スタイル統一
- STORE/MAGAZINE/GO OUT CAMPからアイコンを削除
- 全メニュー項目のフォントサイズを統一
- メニュー順序をPCと同じに修正

### Phase 6: 検索アイコン修正
- 検索アイコンを元サイトと同じ塗りつぶし（fill）スタイルに変更
- 元サイトの`#icon-search3`シンボルを使用
- viewBox: `0 0 30 32`

### Phase 7: 3テーマ対応
- グレーテーマ（demo-c-gray.html）を追加
- ライト＋ダークの中間：薄茶色ナビ＋濃いグレーサブカテゴリ
- 3テーマ切り替えボタンを右下に配置
- 各テーマ間を自由に行き来可能

### Phase 8: 記事ページ + パンくずナビ
- `demo-article-breadcrumb.html` を新規作成
- 元サイトの記事ページ（https://web.goout.jp/fes_music/460914/）を忠実に再現
- OCEANS風パンくずナビを追加: `NEWS > FES/MUSIC > 記事タイトル全文`
- パンくずはPC/SP共に横スクロール（折り返さない）
- カテゴリ表示: NEWS と FES/MUSIC を **横並び（inline-block）**
- 元サイトのSVGアイコン・ロゴを完全再現

### Phase 9: モバイル ナビバー常時表示
- スマホ（900px以下）でもヘッダー直下にカテゴリナビバーを表示
- NEWS, PICKUP, SPECIAL, SNAP, STORE, MAGAZINE, GO OUT CAMP を横一列に配置
- サブメニューなし（メガドロップダウンは非表示のまま）
- 横スクロール可能（`overflow-x: auto`、スクロールバー非表示）
- 元サイト仕様準拠: 高さ50px、`justify-content: flex-start`
- フォント: Montserrat 14px / weight 700
- 対象ファイル: `demo-c-light.html`, `demo-c-gray.html`, `demo-c-dark.html`

### Phase 10: 本番ページ構造の実装 + GitHub Pages公開
- `index.html`（TOPページ）を新規作成
  - PICKUP フィーチャー記事（大画像 + シェアボタン）
  - NEWS 記事一覧（縦型リストカード形式、10記事）
  - サイドバー（RANKING, SNAP, TAGS, STORE, MAGAZINE）
  - フッター（ロゴ + SNS + 2カラムナビ + コーポレートリンク）
- `pickup/464610/index.html`（PICKUP記事ページ）を新規作成
  - カテゴリヘッダー「PICK UP」のみ（サブカテゴリなし）
  - 記事本文 + 画像 + タグ（グレーピル型）+ 著者ボックス
  - 関連記事（3列グリッド）
- `fashion/473673/index.html`（NEWS/FASHION記事ページ）を新規作成
  - カテゴリヘッダー「NEWS」+「FASHION」横並び（inline-block）
  - OCEANS風パンくずナビ: `NEWS > FASHION > 記事タイトル全文`
  - 目次（Table of Contents）セクション
  - 商品情報セクション
- GitHub Pages で自動デプロイ設定（`.github/workflows/pages.yml`）
- 全ページでC案ヘッダー（`demo-c-light.html`と同じデザイン）を統一適用
  - 7カテゴリ: NEWS, PICKUP, SPECIAL, SNAP, STORE, MAGAZINE, GO OUT CAMP
  - アイコンなし、Montserrat 18.75px/700
  - NEWS/SNAPにメガドロップダウン
- シェアボタンは全て黒アイコン（元サイト準拠）
- タグはグレー背景ピル型（bg rgb(231,231,231), 11px）

## 技術詳細

### CSS
- レスポンシブブレークポイント: 900px
- モバイルナビバー: `overflow-x: auto`, `scrollbar-width: none`, 高さ50px
- モバイルメニュー: `position: fixed`, `left: -100%` → `left: 0`
- アコーディオン: `max-height: 0` → `max-height: 500px`
- 矢印回転: `transform: rotate(45deg)` → `rotate(-135deg)`

### JavaScript
```javascript
// モバイルメニュー開閉
function toggleMobileMenu() {
  document.querySelector('.mobile-menu').classList.toggle('open');
  document.querySelector('.overlay').classList.toggle('open');
  document.body.style.overflow = /* toggle */;
}

// アコーディオン開閉
function toggleAccordion(button) {
  button.classList.toggle('open');
  button.nextElementSibling.classList.toggle('open');
}
```

## 確認方法

**方法1: GitHub Pages（推奨）**

https://kitasinkita.github.io/gooutweb/

`main`ブランチにpushすると自動デプロイされる。

**方法2: HTMLファイルを直接開く**

静的HTMLなのでブラウザで直接開くだけでOK：
- `index.html` をダブルクリック
- または、ブラウザにドラッグ&ドロップ

**方法3: ローカルサーバー経由**
```bash
cd /Users/sk/Documents/sanei/gooutweb
python3 -m http.server 9000
```
- http://localhost:9000/
- http://localhost:9000/pickup/464610/
- http://localhost:9000/fashion/473673/

## 元サイトデザイン仕様（調査結果）

### フォント
| 要素 | フォント | サイズ | ウェイト | 行間 |
|------|----------|--------|----------|------|
| body | "Noto Sans JP", sans-serif | 14px | 400 | 21px (1.5) |
| ナビバー | Montserrat, sans-serif | 18.75px | 700 | - |
| カテゴリ見出し | Montserrat, sans-serif | 30px (SP: 20px) | 700 | 30px |
| カテゴリサブ | Montserrat, sans-serif | 14px | 700 | - |
| 記事タイトル | "Noto Sans JP", sans-serif | 32px (SP: 20px) | 700 | 1.3 |
| 日付ラベル | "Open Sans", sans-serif | 12px | 400 | - |
| 日付値 | Oswald, sans-serif | 12.5px | 700 | - |
| 本文 | "Noto Sans JP", sans-serif | 18px | 400 | 36px (2x) |

### 色
| 要素 | 色 |
|------|-----|
| テキスト | rgb(0, 0, 0) |
| ナビバー背景 | rgb(207, 192, 174) |
| カテゴリサブリンク | rgb(98, 80, 58) |
| カテゴリ下線 | 3px solid rgb(98, 80, 58) |
| nav-archive下線 | 1px solid rgb(87, 87, 87) |
| シェア X | rgb(0, 0, 0) |
| シェア FB | rgb(68, 96, 160) |
| シェア はてブ | rgb(0, 164, 222) |
| シェア LINE | rgb(6, 199, 85) |

### サイズ（PC）
| 要素 | 値 |
|------|-----|
| siteNav高さ | 90px |
| brandNav高さ | 50px |
| ハンバーガー | 30px × 25px |
| ハンバーガー線 | 30px × 2.5px |
| ロゴ | 141px × 32.5px |
| ナビアイコン | 15px × 15px |
| 記事エリア幅 | 830px |
| サイドバー幅 | 336px |
| シェアアイコン | 18px |

### サイズ（モバイル）
| 要素 | 値 |
|------|-----|
| siteNav高さ | 60px |
| brandNav高さ | 50px, 横スクロール, justify: flex-start |
| カテゴリ見出し（.h2） | 18px, line-height: 27px, padding-bottom: 8px |
| カテゴリサブ（.tx-cat） | 12px, **inline-block**（NEWSと横並び） |
| 記事タイトル | 20px, 行間26px |
| パンくず | 11px, 横スクロール（折り返さない） |

## パンくずナビ仕様（OCEANS風）

### 形式
```
NEWS > FES/MUSIC > 記事タイトル全文
```

### CSS
```css
.breadcrumb {
  display: flex;
  flex-wrap: nowrap;      /* 折り返さない */
  overflow-x: auto;       /* 横スクロール */
  white-space: nowrap;
  font-size: 12px;        /* SP: 11px */
  padding: 12px 0;
  border-bottom: 1px solid rgb(238, 238, 238);
}

.breadcrumb a {
  color: rgb(102, 102, 102);
  text-decoration: underline;
}

.breadcrumb-current {
  color: rgb(102, 102, 102);
  text-decoration: none;
}
```

### 重要ポイント
- タイトルは**全文表示**（省略しない）
- SP/PC共に**横スクロール**で対応
- カテゴリヘッダー（NEWS + FES/MUSIC）の下に配置
- NEWSとFES/MUSICは**横並び（inline-block）** ← 元サイト準拠

## 参考サイト

- 元サイト: https://web.goout.jp/
- 記事例（PICKUP）: https://web.goout.jp/pickup/464610/
- 記事例（FASHION）: https://web.goout.jp/fashion/473673/
- 記事例（FES/MUSIC）: https://web.goout.jp/fes_music/460914/
- ストア: https://www.goout.jp/
- キャンプ: https://www.gooutcamp.jp/
- パンくず参考: OCEANS（https://oceans.tokyo.jp/）

## GitHub

- リポジトリ: https://github.com/kitasinkita/gooutweb
- デプロイ: GitHub Pages（mainブランチpush時に自動）
