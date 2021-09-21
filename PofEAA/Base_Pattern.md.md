# Base Pattern

## GatewayとMapper
どちらもサブシステム間の分離レイヤである。
外部システムとのやり取りの間に入って、外部システムに直接依存しないようにするためのもの。
### GatewayとMapperの違い
Gatewayは、外部システムはGatewayに依存していない(知らない) が、 内部側のシステムはGatewayを知っており、呼び出しを実行する。
例えば、テーブルモジュールはテーブルデータケートウェイを呼び出して、自身にデータを読み込む。
一方でMapperは、やり取りするそう
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTg4OTc2MzU1MV19
-->