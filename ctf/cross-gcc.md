# cross-gcc
熱血！／大熱血！ アセンブラ入門  
開発環境のＶＭイメージ
http://kozos.jp/vmimage/burning-asm.html

## ID/PASS
user/progtooluser
root/progtoolroot


## tool
/usr/local/cross-gcc494/bin 配下にobjdumpなどのツールが入っている
例えば arm-elf用の toolは `ls /usr/local/cross-gcc494/bin/arm-elf*` 

objdump なら
```
/usr/local/cross-gcc494/bin/arm-elf-objdump -d arm-elf.x | less
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk0NzQyOTNdfQ==
-->