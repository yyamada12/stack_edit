Backendのレイヤードアーキテクチャでのpackage構成の例

## application layer

### リクエスト/レスポンスを定義するpackage

https://techblog.raccoon.ne.jp/archives/1621909754.html
ではform

https://qiita.com/YutaKase6/items/7d88fa23f81366905270
ではresource


form は、 view を返すアプリケーションで使う感じ。
spring なら @Controller を使う場合

RESTfull な APIであれば、 resourceとしてしまうのが良さそう


TERASOLUNA でも、viewを返すアプリではForm、
https://terasolunaorg.github.io/guideline/5.0.0.RELEASE/ja/Overview/ApplicationLayering.html
RESTful Web Service では Resourceを利用するとなっている
https://terasolunaorg.github.io/guideline/5.0.0.RELEASE/ja/ArchitectureInDetail/REST.html#id4


あとはdto
dtoは意味が広いので、
https://zenn.dev/morio_pg/articles/16777261720294644011
にあるように

> 各DTOの名称は下記のように用途毎に分ける
> 
> リクエスト関連：Form（Web）、Request（API）
> レスポンス関連（JSON）：Response、View
> DBや外部API：Entity

dto.request とかは普通にわかりやすいかも
