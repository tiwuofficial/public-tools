# public-tools

様々な便利な web で動くツールをまとめたサイト。GitHub Pages で公開する。

## 構成

```
/
├── index.html          ルート (ツール一覧ページ)
├── src/
│   ├── _shared/
│   │   └── style.css   全ツール共通のスタイル
│   └── <tool-name>/
│       └── index.html  ツール本体 (HTML/JS をインライン)
└── AGENTS.md           AI エージェント向けの寄稿ルール
```

- 各ツールは `src/<kebab-case-name>/index.html` の単一ファイルで完結させる
- 外部 CDN や npm パッケージは使わない（GitHub Pages から静的配信できる範囲のみ）
- スタイルは `src/_shared/style.css` を共通利用し、全ツールでデザインを統一する
- 表示対象は **PC のみ**。スマホ/タブレットの最適化は不要

## ツール追加の手順

1. `src/<kebab-case-name>/index.html` を作成し、`../_shared/style.css` を読み込む
2. ページ先頭に「← ツール一覧へ戻る」リンク (`../../index.html`) を置く
3. ルートの `index.html` のツール一覧 `<ul class="tools">` にリンクと短い説明を追加する
4. `git commit -m "Add <tool name> tool"` でコミットする

詳細なテンプレートと寄稿ルールは [`AGENTS.md`](./AGENTS.md) を参照。
