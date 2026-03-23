# Git ワークフロー規約

- コミットメッセージ形式: `feat(keymap): ...` / `fix(combo): ...` / `chore: ...`
- レイヤー変更は1コミット1レイヤーを原則とする
- 作業順序: **編集 → コミット → push → ビルド結果確認**
- `.build/` と `zmk-config/` は .gitignore 対象
