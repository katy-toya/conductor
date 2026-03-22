---
description: キーマップの整合性チェック（コンボ競合・レイヤーキー数検出）
argument-hint: [レイヤー番号 or all]
---
## キーマップ内容

!`cat config/monokey.keymap`

## シールド定義（キー配列）

!`cat config/boards/shields/monokey/monokey.dtsi`

対象: $ARGUMENTS（未指定なら全レイヤー）

以下をチェックしてください：
1. 各レイヤーのキー数が40（最終行は左6+右4の変則配列）と一致しているか
2. コンボのキーポジションが重複・矛盾していないか
3. `&trans` と `&none` の使い方が意図通りか
4. `&to` と `&mo` の使い分けが意図通りか
5. quick-tap-ms の値がグローバル設定（175）と合っているか
問題があれば修正案を提示してください。
