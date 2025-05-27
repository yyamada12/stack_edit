
# firestore の golang client の retry 実装について

firestore からの document の取得時に、  `The service is temporarily unavailable.` のエラーが返ってくることがある
リトライすればいいのかなと思い、 firestore client がどのようにリトライ処理をしているかを調べた

大体これっぽい。
https://zenn.dev/kawabatas/articles/gcp-go-retry



<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY5ODc1NDc2NF19
-->