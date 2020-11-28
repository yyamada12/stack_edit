# cross-gcc

## 開発環境
熱血！／大熱血！ アセンブラ入門  
開発環境のＶＭイメージ
http://kozos.jp/vmimage/burning-asm.html

### ID/PASS
user/progtooluser
root/progtoolroot


### tool
/usr/local/cross-gcc494/bin 配下にobjdumpなどのツールが入っている
例えば arm-elf用の toolは `ls /usr/local/cross-gcc494/bin/arm-elf*` 

objdump なら
```
/usr/local/cross-gcc494/bin/arm-elf-objdump -d arm-elf.x | less
```


## ARMのexploit例
問題・解答例は以下に保管。 https://github.com/yyamada12/ctfs/tree/master/seccon2019final 


<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMjk3ODI3NzksNjMxMjE1NTg5LC05ND
c0MjkzXX0=
-->