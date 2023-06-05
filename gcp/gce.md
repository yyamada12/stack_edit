
## local から ssh する方法

AWSのように、ssh鍵を作って配布するようなことはしてくれないので、自分で鍵を作って登録する

1: ssh-keygen で作る
2: コンソールで、compute engine → 編集 → ssh 鍵登録
3: ssh -i 鍵 ユーザー名@gceのIPアドレス でsshできる
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE1NTQ5Mzg1MDNdfQ==
-->