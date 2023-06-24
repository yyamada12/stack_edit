# Gin Test

ginのtest

## 公式の方法
https://gin-gonic.com/ja/docs/testing/

http.NewRequest()でリクエストを作成し、
httptest.NewRecorder() でレスポンスを捕捉し、検証するという流れ

mockは使わず、本番と同じ router (setupRouter()で用意したrouter)を使っている

この流れでmockを使うなら、
setupTestRouter() で適度にmockに置き換えたtest用のrouterを用意する形になりそう
↓
テストケースによって、mockの返す値を変える、というのは面倒になりそう

## 公式の方法2

gin.CreateTestContext() を使う方法

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTAyOTc4ODk2Ml19
-->