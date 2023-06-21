
## AWS subnet
- public subnet
  - インターネットからアクセス可能
  - インターネットへのアクセスも可能
  - private subnet へは、 private ip によってアクセス可能?(検証したい)
- private subnet
  - インターネットからのアクセスは不可
    よって、一般的には外部ALBなどから、private subnet 上のアプリケーションにアクセスさせる
  - インターネットへのアクセスは不可
    一般的には、NATゲートウェイを立てて、そこ経由でインターネットにアクセスする
  - public subnet へのアクセスは、 private ip によってアクセス可能? (検証したい)


※ ALB は外部ALBと内部ALBがあり、作成時に [スキーム] で、[インターネット向け] または [内部] を選択する


### EC2
- public subnet に配置したEC2
  - パブリックIPアドレスを設定した場合
    -  インターネットからアクセス可能
    - インターネットへのアクセスも可能
  - パブリックIPアドレスを指定しなかった場合
    - インターネットからアクセス不可
    - インターネットへのアクセスは可能
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMDAxOTQ1NjUsMTgwNjMzNzMwMCwzOT
c0NTk3OCw3MzA5OTgxMTZdfQ==
-->