# ビルド結果確認ルール

## 待機時間
- push 後は **2分30秒待機**してから確認する（フックが自動実行）
- 根拠: 過去25回の実行時間の中央値 = 113秒（外れ値3件除外）

## WebFetch キャッシュ問題
WebFetch は GitHub Actions ページをキャッシュするため、古い結果を返し続けることがある。

**症状**: 同じ実行番号・同じコミット SHA が2回以上続いて返ってくる
**対処手順**:

1. `git log --oneline -1` で直近のコミット SHA を確認
2. WebFetch の結果に表示されるコミットと一致すれば、そのビルド結果が最新
3. **一致しない場合** → URL にクエリパラメータを付けてキャッシュ回避を試みる
   ```
   https://github.com/katy-toya/conductor/actions?t=<unix timestamp>
   ```
4. それでも同じ古い結果が返ってくる場合は、**ユーザーにブラウザで直接確認を促す**
   > 「WebFetch がキャッシュされた結果を返しているようです。ブラウザで https://github.com/katy-toya/conductor/actions を確認してください。」

## 確認 URL
https://github.com/katy-toya/conductor/actions
