---
paths:
  - "config/monokey.keymap"
  - "config/boards/shields/monokey/*.keymap"
---
# ZMK キーマップ記述規約

- バインディングは `&kp`、`&mt`、`&lt`、`&mo`、`&to` を使い分ける
- グローバル設定: `mt` は flavor="balanced"、`quick-tap-ms = <175>`（変更時は全体統一）
- `tapping-term-ms` は明示指定なし（ZMKデフォルト使用）
- コンボのキーポジションは必ずコメントで位置を併記する
  例: `key-positions = <17 18>;  /* row1: col7 col8 */`
- 1レイヤーあたりのキー数は40（最終行: 左6+右4の変則配列に注意）
- `&trans` と `&none` を混同しない（透過 vs 無効）
- レイヤー固定切替は `&to`、一時切替は `&mo`
