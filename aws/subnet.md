
## AWS subnet
- public subnet
  - インターネットからアクセス可能
  - インターネットへのアクセスも可能
  - private subnet へは、 private ip によってアクセス可能
- private subnet
  - インターネットからのアクセスは不可
    よって、一般的には外部ALBなどから、private subnet 上のアプリケーションにアクセスさせる
  - インターネットへのアクセスは不可
    一般的には、NATゲートウェイを立てて、そこ経由でインターネットにアクセスする
  - public subnet へのアクセスは、 private ip によってアクセス可能


※ ALB は外部ALBと内部ALBがあり、作成時に [スキーム] で、[インターネット向け] または [内部] を選択する


### EC2
- public subnet に配置したEC2
  - EC2起動時にパブリックIPアドレスを設定した場合
    -  インターネットからアクセス可能
    - インターネットへのアクセスも可能
  - EC2起動時にパブリックIPアドレスを指定しなかった場合
    - インターネットからアクセス不可
    - インターネットへのアクセスも不可
    - private ip で、public subnet 上のEC2からsshすることは可能

- private subnet に配置したEC2
  - EC2起動時にパブリックIPアドレスを設定した場合
    - 一応、パブリックIPアドレスを設定することはできる
    - しかし、private subnet に配置しているため、インターネットからのアクセスは不可
    - インターネットへのアクセスも不可
    - (この状態でNATゲートウェイを作った場合でも検証したい)
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNzc2MTMzNjcsLTI2NzY1MjE5MSw0Mz
E5MTIwODUsLTExMDAxOTQ1NjUsMTgwNjMzNzMwMCwzOTc0NTk3
OCw3MzA5OTgxMTZdfQ==
-->