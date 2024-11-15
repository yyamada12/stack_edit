# k8s
## context
一つのk8s環境を `cluster` といい、kubectlコマンドを利用する際にcontextを設定することで特定のclusterに対してコマンドを実行できる。

- context 一覧の取得
```
kubectl config get-contexts
```
- context の切り替え
```
kubectl config use-context $CLUSTER_NAME
```


## curl

k8s で稼働中のpod に対して、curlを実行したい場合

```
kubectl run -it curl --image=curlimages/curl --rm --restart=Never -- /bin/sh
```
これで、 pod の IPに対してcurlを実行すれば良い

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTQ5OTg5NjIxLC0zOTQwMzA5MiwxNzI3MT
MyODg2XX0=
-->