# SQS 利用時の設計考慮点

用語
- コンシューマー 
キューからメッセージを受信するシステム
- 

## メッセージの受信と削除・可視性タイムアウト
https://docs.aws.amazon.com/ja_jp/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html
> コンシューマーがキューからメッセージを受信して処理しても、そのメッセージはキューに保留されたままです。Amazon SQSでは、メッセージが自動的に削除されません。

メッセージは受信されると、可視性タイムアウトで設定した時間の間は、他の



## メッセージサイズ

標準キュー

## キューのタイプ
標準キュー

・冪等性
・多重起動への対応
・


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTc2NzA4Mjk4MywtNTMzNjA0MjM1XX0=
-->