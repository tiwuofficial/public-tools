# OGP / メタタグ確認ツール

- カテゴリ: システム情報・ネットワーク系候補
- 状態: 実装済
- 実装先: `src/ogp-checker/index.html`

## 概要
URL または貼り付けた HTML から OGP、Twitter Card、title、description などを抽出してプレビューする。

## 要件メモ
- URL fetch は同一オリジンまたは CORS 許可サイトに限られる。
- fetch 失敗時は HTML 貼り付けでのチェックを案内する。
