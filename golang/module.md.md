# Go Module, Go Workspace


## go module

go.mod と go.sum で依存ライブラリを管理する仕組み

### go mod init [module名]
このコマンドでmoduleを初期化する
go.modファイルが作成され、module名とgoのversionが記載される
require として、直接必要なライブラリと、間接的に必要なライブラリが追加されていくことになる

### go mod tidy
tidy は 「たいでぃ」と読む
ソースコードに記載されている内容から、必要なライブラリをgo.modに追加し、不要なライブラリを削除する

また、必要なライブラリをlocalにダウンロードする
ダウンロード先のディレクトリは、GOMODCACHE という名前のgo env で決まっており、デフォルトでは GOPATH/pkg/mod になっている




## Go Workspace

`go work init` で初期化する
go.work ファイルが作成される

`go work use [モジュールディレクトリ名]` とすると、必要なモジュールを追加することができる

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY2Mzg5NTQwOCwtMTU4NjM2ODQ3Ml19
-->