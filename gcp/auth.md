# GCP での 認証方法まとめ

ref: https://cloud.google.com/docs/authentication

## gcloud CLIの場合

https://cloud.google.com/docs/authentication/gcloud?hl=ja

### ローカル環境
1: user 認証を使って、ログインする場合
- 以下のコマンドでブラウザから認証できる
```
gcloud auth login
```

- 以下のコマンドで現在のaccountが見れる

```
gcloud auth list
```

- 以下のコマンドで、account を切り替えられる

```
gcloud config set account `ACCOUNT`
```

2: service account を利用することもできる

```
gcloud auth login --cred-file=xxx
```

### 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5NDM4MzE5ODUsLTExMjI1OTg4MjQsLT
U5MDM0NTEyNl19
-->