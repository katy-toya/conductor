---
description: 変更内容を確認してGitHubにプッシュ（GitHub Actionsでビルド発動）
---
## 現在の変更差分

!`git diff config/monokey.keymap`

## コミット済み未プッシュの内容

!`git log origin/main..HEAD --oneline`

上記の差分を確認し、内容に問題がなければプッシュして GitHub Actions ビルドを発動してください。
問題がある場合は修正点を指摘してください。

ビルド結果は GitHub Actions の Artifacts からダウンロードできます。
