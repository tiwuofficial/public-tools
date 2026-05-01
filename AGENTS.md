# AGENTS.md

このリポジトリにツールを追加する AI エージェント／コントリビュータ向けの指針。

## このリポジトリは何か

ブラウザだけで動く小さな web ツールを集めたサイト。GitHub Pages で配信する。
各ツールは `src/<kebab-case-name>/index.html` の単一ファイルで完結する。

## デザインルール（厳守）

- **共通 CSS**: `src/_shared/style.css` を `<link rel="stylesheet" href="../_shared/style.css">` で必ず読み込む。ツール固有 CSS は原則書かない。
- **共通スタイルの拡張**: スタイルが足りないときは個別ツール側で書かず、`src/_shared/style.css` に共通コンポーネントとして追記する。既存ツールを壊さないこと。
- **CSS 変数を使う**: 色や角丸は既存変数 (`--accent`, `--border`, `--card`, `--muted`, `--bg`, `--fg`, `--radius` など) を再利用する。新色をハードコードしない。
- **PC 専用**: スマホ/タブレット対応は考慮不要。メディアクエリで小画面最適化を入れない。
- **外部依存禁止**: CDN、npm パッケージ、外部フォント、外部画像 などは使わない。HTML/JS は単一ファイル内にインライン。
- **言語**: 日本語 UI。`<html lang="ja">` と `<meta charset="UTF-8">` を必ず付ける。

## HTML テンプレート

```html
<!DOCTYPE html>
<html lang="ja">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1">
<title>ツール名 - public-tools</title>
<link rel="stylesheet" href="../_shared/style.css">
</head>
<body>
<div class="container">
  <div class="nav"><a href="../../index.html">← ツール一覧へ戻る</a></div>
  <header class="page-header">
    <h1>ツール名</h1>
    <p class="lead">短い説明（1 文）</p>
  </header>

  <!-- ツール本体 -->

</div>
<script>
  // ツールのロジック
</script>
</body>
</html>
```

## 利用可能な共通クラス

`src/_shared/style.css` で定義済みの主要なクラス。詳細はファイルを参照。

- レイアウト: `.container`, `.nav`, `.page-header`, `.lead`
- 入力: `<input>`, `<textarea>`, `<select>` はタグセレクタで整形済み
- ボタン: `<button>` / `.button`、強調は `.primary`
- アクション行: `.actions`（ボタン横並び）
- カード: `.card`
- 統計表示: `.stats` ＞ `.stat` ＞ `.label` / `.value`（カウンタ系で利用）
- ツール一覧（ルート専用）: `ul.tools` ＞ `li` ＞ `<a>` / `.desc`
- フッター: `footer.page-footer`

## ツール候補（優先度順）

未実装のものを優先的に選ぶ:

1. 2 つの文章の差分比較 (diff)
2. タイマー / ストップウォッチ
3. ルーレット (項目をランダム抽選)
4. その他: カラーピッカー / QR コード生成 / UUID 生成 / Markdown プレビュー / Unix time 変換 / 正規表現テスター / パスワード生成 / JSON 整形 / Base64 エンコード など

バイトカウント単独版は文字数カウンタに含まれるため低優先。

## 1 イテレーションでやること

1. `ls src/` で既存ツールを確認し、重複しないアイデアを 1 つ決める
2. `src/<kebab-case-name>/index.html` を作成（テンプレート準拠）
3. 必要なら `src/_shared/style.css` に共通コンポーネントを追記
4. ルートの `index.html` のツール一覧 `<ul class="tools">` にリンクと `.desc` を追加
5. HTML 構文と JS の明らかな誤りを目視チェック
6. `git add` で対象ファイルだけステージ → `git commit -m "Add <tool name> tool"`
7. `git push` する（コミットごとに都度 push してよい）
8. 1 イテレーションで **1 ツールだけ** 追加する

## やってはいけないこと

- `.claude/` 配下のファイルをコミットする
- `git push --force` などの破壊的 push
- 既存ツールのスタイルを壊すような共通 CSS の破壊的変更
- 同じツールを別名で重複追加する
- 外部依存（CDN, fonts, npm, fetch 先 API）を持ち込む
- リポジトリ直下の `.nojekyll` を消す（GitHub Pages の Jekyll 処理を無効化している。消すと `_shared/` のような `_` 始まりディレクトリが 404 になる）
