# Go Module, Go Workspace


## go module

go.mod と go.sum で依存ライブラリを管理する仕組み

### go mod init [module名]
このこ

### go mod tidy
「たいでぃ」と読む
ソースコードに記載されている内容から、必要なライブラリをgo.modに追加し、不要なライブラリを削除する

また、必要なライブラリをlocalにダウンロードする
ダウンロード先のディレクトリは、GOMODCACHE という名前のgo env で決まっており、デフォルトでは GOPATH/pkg/mod になっている






> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI0MTUxMDQ2NiwtMTU4NjM2ODQ3Ml19
-->