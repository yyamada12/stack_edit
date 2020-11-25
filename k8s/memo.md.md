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

<!--stackedit_data:
eyJoaXN0b3J5IjpbLTM5NDAzMDkyLDE3MjcxMzI4ODZdfQ==
-->