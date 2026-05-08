# OKR テンプレート

- カテゴリ: 発想・ビジネスフレームワーク系候補
- 状態: 実装済
- 実装先: `src/okr-template/index.html`

## 概要
Objective（目指す状態）と 3〜5 個の Key Result（測定可能な達成指標）でゴールを定義するフレーム。進捗バー付きで運用したい。

## 要件メモ
- 複数の Objective を持つ
- 各 Objective に Key Result を 3〜5 件追加
- 各 KR に進捗 (0〜100%) と現在値 / 目標値
- localStorage 自動保存
- Markdown / JSON 出力
