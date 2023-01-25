
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



参考
https://stackoverflow.com/questions/62210349/spring-batch-disable-spring-boot-autoconfiguration-for-specific-jobs/62216804#62216804
https://stackoverflow.com/questions/60349214/how-to-apply-something-like-lazy-to-spring-batch
など
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEwNjcxNDg2MjIsNDE2Mjk4MjIyXX0=
-->