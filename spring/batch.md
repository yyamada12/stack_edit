
# Spring Batch メモ

1つのプロジェクトで複数のバッチ処理を実装したい場合

- 環境変数にJobの名前を設定する (SPRING_BATCH_JOB_NAMES=xxx みたいにすれば良い)
or
- jar の実行時に --spring.batch.job.names=xxx として指定する
or 
- application.properties をバッチごとに作る
or
- Main をカスタマイズする
のどれかになりそう

やる場合の注意点

- バッチが増えていくと fat jar になる
- bean登録 を lazy load にしないと、 不要なbean登録にリソースがとられてしまう
- 一つのバッチを修正するだけで、jar 全体をビルドし直しになる


<!--stackedit_data:
eyJoaXN0b3J5IjpbNDE2Mjk4MjIyXX0=
-->