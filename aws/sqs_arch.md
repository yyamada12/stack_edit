# SQS 利用時の設計考慮点

用語
- メッセージ
キューに格納されるデータ
- コンシューマー 
キューからメッセージを受信するシステム
- プロデューサー
キューにメッセージを送信するシステム

## メッセージの受信と削除
https://docs.aws.amazon.com/ja_jp/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html
> コンシューマーがキューからメッセージを受信して処理しても、そのメッセージはキューに保留されたままです。Amazon SQSでは、メッセージが自動的に削除されません。

受信しただけでは、キューに残り続けるので、
処理が成功した場合は明示的にメッセージを削除することが必要
逆に、処理が失敗した場合はメッセージを削除しないことで、次回受信時にリトライができる
そのため、どのようなタイミングでメッセージを削除するかどうかの検討が必要

## 可視性タイムアウト


## メッセージサイズ

標準キュー

## キューのタイプ
標準キュー

・冪等性
・多重起動への対応
・


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3ODc3MTY3NjcsLTY5ODY2MjE2MCwtNz
Y3MDgyOTgzLC01MzM2MDQyMzVdfQ==
-->