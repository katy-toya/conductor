# Conductor ZMK Firmware

## アーキテクチャ
- ZMK Firmware ベース（revision: v0.3 固定）
- ボード: `seeeduino_xiao_ble`（左右それぞれ）
- シールド: `monokey_L` / `monokey_R` + `rgbled_adapter`（左右分割ワイヤレス）
- キーマップ: `config/monokey.keymap`
- シールド定義: `config/boards/shields/monokey/`
- カスタムモジュール:
  - `zmk-pmw3610-driver`（トラックボールセンサー）
  - `zmk-rgbled-widget`（RGB LED）
  - `zmk-feature-charge-indicator`（充電インジケーター）

## ビルド方法
**ローカルビルドは行わない。GitHub Actionsで自動ビルド。**
- `git push` → `.github/workflows/build.yml` が自動発動
- ビルド設定: `build.yaml`（ボード・シールドの組み合わせを定義）
- ビルド成果物はGitHub ActionsのArtifactsからダウンロード

## ビルド結果確認
**push 後は必ず WebFetch でビルド結果を確認すること。**
詳細な確認手順・キャッシュ問題の対処法は `.claude/rules/build-check.md` を参照。

確認 URL: `https://github.com/katy-toya/conductor/actions`

## レイヤー構成（現在）
```
0: default_layer - BASE（通常入力）
1: FUNCTION      - 記号・特殊キー
2: NUM           - ファンクションキー・数字
3: ARROW         - カーソル移動・ウィンドウ操作
4: MOUSE         - マウスレイヤー（to 4 で固定切替）
5: SCROLL        - スクロールレイヤー（コンボ key-pos 17+18 で発動）
6: Bluetooth     - BT選択・CLR・bootloader
7-11: layer_7〜layer_11（未使用、雛形）
```

## キー構成
- 4行 × 左5 + 右5 = 合計40キー
- 最終行のみ変則: 左6 + 右4（合計10キー）
- マトリクス: 4行 × 11列（col 5 は最終行のみ）

## ホールドタップ設定（グローバル）
- `mt`: flavor = "balanced", quick-tap-ms = 175
- `lt`: quick-tap-ms = 175
- `tapping-term-ms` は ZMK デフォルト値（明示指定なし）

## コンボ（現在）
- `scroll`: key-positions = <17 18> → &mo 5
- `mouse_layer`: key-positions = <16 36> → &to 4

## コマンド・スキル一覧
- `/flash` — diff確認してpush・ビルド発動（事前にコミット済みであること）
- `/layer-gen [名前 用途]` — 未使用テンプレートを新レイヤーに書き換え
- `/validate-keymap [レイヤー番号|all]` — キー数・コンボ競合・hold-tap設定を検証
- `combo-helper`（自動発動）— コンボ候補の提案・競合チェック
- `keymap-review`（自動発動）— キーマップ全体のレビュー

## 規約
- コンボは key-positions でインデックス指定（0始まり、行×列順）
- レイヤー名は UPPER_SNAKE_CASE
- 未使用キーは `&trans`（透過）、無効化は `&none`
- マクロは config/macros/ に切り出す（将来）

## 注意点
- ZMK はリアルタイムレイヤー変更不可（変更 = push = ビルド必須）
- BLE設定変更後はペアリングリセットが必要（settings_reset シールドを使用）
- west.yml の revision を v0.3 に固定すること（ZMK 破壊的変更対策）
- `snippet: studio-rpc-usb-uart` は monokey_R のみ（build.yaml 参照）
