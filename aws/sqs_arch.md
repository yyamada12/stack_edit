# SQS 利用時の設計考慮点

## 前提知識

### 基本用語
- メッセージ
キューに格納されるデータ
- コンシューマー 
キューからメッセージを受信するシステム
- プロデューサー
キューにメッセージを送信するシステム


### メッセージの受信と削除
https://docs.aws.amazon.com/ja_jp/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-visibility-timeout.html
> コンシューマーがキューからメッセージを受信して処理しても、そのメッセージはキューに保留されたままです。Amazon SQSでは、メッセージが自動的に削除されません。

> コンシューマーはメッセージを受信して処理した後、キューからメッセージを削除する必要があります。

メッセージを受信しただけでは、キューにメッセージが残り続けるので、
処理が成功した場合は明示的にメッセージを削除することが必要
逆に、処理が失敗した場合はあえてメッセージを削除しないことで、次回受信時にリトライができる
そのため、どのようなタイミングでメッセージを削除するかどうかの検討が必要

## 必須パラメータ
### キューのタイプ
https://docs.aws.amazon.com/ja_jp/AWSSimpleQueueService/latest/SQSDeveloperGuide/sqs-queue-types.html

スタンダードキューとFIFOキューがあり、どちらを利用するか選択する必要がある

- スタンダードキュー
低コストかつ高スループット(1秒あたりほぼ無制限のAPIコールをサポート)だが以下の制約がある
  - 配信順序が保証されない (Best-Effort Ordering)
  - 同一メッセージが複数回配信される可能性がある (At-Least-Once Delivery )
- FIFOキュー
スタンダードキューによる制限を解消するが、コストが高く、スループットに制約がある
  - 1秒あたり最大300のAPIコールをサポート (ただしクウォータの引き上げも可能)
  - 配信順序が保証される (First-In-First-Out Delivery)
  - 同一メッセージは1度のみ配信される (Exactly-Once Processing)

つまりスタンダードキューを選択する場合は以下の2点を満たす必要がある
- 処理が冪等であること
- キューに入れた順序とキューから取り出す順序変わってしまっても問題ないこと

## メッセージサイズ

標準キュー

## キューのタイプ
標準キュー

・冪等性
・多重起動への対応
・


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbNTEwMDg0NjM3LC04Nzg3NDgyMzEsMTkwMz
I2MTMyMCw1MjkzMTE5NzksLTY5ODY2MjE2MCwtNzY3MDgyOTgz
LC01MzM2MDQyMzVdfQ==
-->