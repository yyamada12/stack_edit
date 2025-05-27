
# firestore の golang client の retry 実装について

firestore からの document の取得時に、  `The service is temporarily unavailable.` のエラーが返ってくることがある
リトライすればいいのかなと思い、 firestore client がどのようにリトライ処理をしているかを調べた

大体これっぽい。
https://zenn.dev/kawabatas/articles/gcp-go-retry

https://pkg.go.dev/cloud.google.com/go/firestore@v1.18.0/apiv1#Client

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTk5MzM5MjIwMV19
-->