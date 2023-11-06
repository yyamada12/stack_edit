# Spring test で DB コネクションあふれる問題

SpringBootにおける @SpringBootApplicationTest では、テストごとにApplicationContextを作成する
ApplicationContextを作るのは高コストなため、テストごとに使いまわせるように、Cacheにのり、デフォルトでは最大で20まで作成される。
よって、コネクションプールの設定でコネクションプール数を20とかに設定していると、最大で 20 x 20 = 400 とかのコネクション数になり、DB側の最大コネクション数の設定を超えると、エラーになってしまう。
開発初期は発生せず、テスト数が増えてくる頃に発生するのでタチが悪い。。


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY4MzE5NTgzNl19
-->