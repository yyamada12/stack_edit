
# firestore の golang client の retry 実装について

firestore からの document の取得時に、  `The service is temporarily unavailable.` のエラーが返ってくることがある
リトライすればいいのかなと思い、 firestore client がどのようにリトライ処理をしているかを調べた

大体これっぽい。
https://zenn.dev/kawabatas/articles/gcp-go-retry

以下の、Client 構造体の CallOptions に設定できる
https://pkg.go.dev/cloud.google.com/go/firestore@v1.18.0/apiv1#Client

デフォルトの挙動は、 以下で設定されている
https://github.com/googleapis/google-cloud-go/blob/03a579095fc75a42feb57a34a08208d43dcb9aaf/firestore/apiv1/firestore_client.go#L86 

firestore からの document 取得は、 codes.Unavailable に対して 60秒くらいリトライしてくれている。
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NTUzMTk1MDhdfQ==
-->