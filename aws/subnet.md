
## AWS subnet
- public subnet
  - インターネットからアクセス可能
  - インターネットへのアクセス可能
- private subnet
インターネットからのアクセスは不可
よって、一般的には外部ALBなどから、private subnet 上のアプリケーションにアクセスさせる


※ ALB は外部ALBと内部ALBがあり、作成時に [スキーム] で、[インターネット向け] または [内部] を選択する

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY1ODA0MjAzNCw3MzA5OTgxMTZdfQ==
-->