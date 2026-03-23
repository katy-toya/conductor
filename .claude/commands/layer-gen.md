---
description: 新しいレイヤーの雛形を生成してキーマップに追加
argument-hint: [レイヤー名 用途の説明]
---
## 現在のキーマップ

!`cat config/monokey.keymap`

要求: $ARGUMENTS

上記キーマップのスタイルに合わせて新しいレイヤーの雛形を生成し、
layer_7〜layer_11 の中で `bindings` が `&trans` のみの未使用テンプレートを探して上書きしてください。

条件：
- キー数は40（最終行: 左6キー + 右4キーの変則配列）
- 未割り当てキーは `&trans` で埋める
- レイヤー名は UPPER_SNAKE_CASE
