# Git ワークフロー規約

- コミットメッセージ形式: `feat(keymap): ...` / `fix(combo): ...` / `chore: ...`
- レイヤー変更は1コミット1レイヤーを原則とする
- ビルド成功を確認してからコミット
- `.build/` と `zmk-config/` は .gitignore 対象
