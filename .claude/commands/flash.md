---
description: 変更内容を確認してGitHubにプッシュ（GitHub Actionsでビルド発動）
---
## 前提確認

!`git status`

**前提条件**: 変更はすでにコミット済みであること（未コミットの変更がある場合はまずコミットしてください）

## コミット済み未プッシュの内容

!`git log origin/main..HEAD --oneline`

## 差分サマリ

!`git diff origin/main..HEAD -- config/monokey.keymap`

上記の差分を確認し、内容に問題がなければプッシュして GitHub Actions ビルドを発動してください。
問題がある場合は修正点を指摘してください。

ビルド結果は GitHub Actions の Artifacts からダウンロードできます。
