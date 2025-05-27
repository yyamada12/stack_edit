
# firestore の golang client の retry 実装について

firestore からの document の取得時に、  `The service is temporarily unavailable.` のエラーが返ってくることがある
リトライすればいいのかなと思い、 firestore client がどのようにリトライ処理をしているかを調べた

https://zenn.dev/kawabatas/articles/gcp-go-retry

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY4MzgwOTcyOV19
-->