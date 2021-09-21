# Base Pattern

## GatewayとMapper
どちらもサブシステム間の分離レイヤである。
外部システムとのやり取りの間に入って、外部システムに直接依存しないようにするためのもの。
### GatewayとMapperの違い
Gatewayは、外部システムはGatewayに依存していない(知らない) が、 内部側のシステムはGatewayを知っており、呼び出しを実行する。
例えば、テーブルモジュールはテーブルデータケートウェイを呼び出して、自身にデータを読み込む。
一方でMapperは、やり取りする双方のオブジェクトが、Mapperに依存しない(知らない)。
例えば、Domain Model では、 DataMapperによってデータがDomain Modelに読み込まれるが、Domain Model 自体は DataMapperを意識しない (知らない)。知っていればそれはActive Record である。

### GOFデザインパターンとの関係
PofEAAでは、GatewayパターンをFacade, Adaptor, Mediator それぞれと別のパターンとしている。(18.1.2)
また、Mapperも Mediator とは別のパターンとしている。(18.2.2)

### Repositoryは？
Repository は Gatewayの一部と考えて良さそう。
データストアに対するGatewayをRepositoryと呼ぶ。

https://medium.com/@jonathanloscalzo/perhaps-gateway-and-repository-do-not-mean-the-same-according-to-fowler-7a4367a6d631
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTc4MjU3MTMzOV19
-->