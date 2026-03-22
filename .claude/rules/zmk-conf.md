---
paths:
  - "config/*.conf"
---
# ZMK 設定フラグ規約

- BLE有効化: CONFIG_BT=y / CONFIG_ZMK_BLE=y
- USB有効化: CONFIG_USB=y / CONFIG_ZMK_USB=y
- デバッグログは本番ビルド前に必ず削除
  （CONFIG_ZMK_LOG_LEVEL_DBG はサイズ増大・遅延の原因）
- コンボ機能: CONFIG_ZMK_COMBO=y が必要
- マクロ機能: CONFIG_ZMK_MACROS=y が必要
