# Gin Test

ginのtest

## 公式の方法
https://gin-gonic.com/ja/docs/testing/
```go
func TestPingRoute(t *testing.T) {
	router := setupRouter()

	w := httptest.NewRecorder()
	req, _ := http.NewRequest("GET", "/ping", nil)
	router.ServeHTTP(w, req)

	assert.Equal(t, 200, w.Code)
	assert.Equal(t, "pong", w.Body.String())
}
```

http.NewRequest()でリクエストを作成し、
httptest.NewRecorder() でレスポンスを捕捉し、検証するという流れ

mockは使わず、本番と同じ router (setupRouter()で用意したrouter)を使っている

この流れでmockを使うなら、
setupTestRouter() で適度にmockに置き換えたtest用のrouterを用意する形になりそう
↓
テストケースによって、mockの返す値を変える、というのは面倒になりそう

## 公式の方法2

gin.CreateTestContext() を使う方法
CreateTestContext は、 *gin.Contextと *gin.Engine を返してくる

### *gin.Context を使う方法
gin.
```go
w := httptest.NewRecorder()
c, _ := gin.CreateTestContext(w)
c.Request, _ = http.NewRequest("GET", "/user/test", nil)
c.Params = append(c.Params, gin.Param{Key: "name", Value: "test"})

h.GetUser(c)

assert.Equal(t, tt.expect, w.Body.String())
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIwNzU3MzI3NTIsODM1NzA2NzA3LDEwMj
k3ODg5NjJdfQ==
-->