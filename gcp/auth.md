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

### Cloud Shell, GCP上のサーバ内
自動的に認証されるため明示的にloginは不要


## application の場合

https://cloud.google.com/docs/authentication/application-default-credentials

ADC(Application Default Credentials ) と呼ばれる仕組みになる

1: GOOGLE_APPLICATION_CREDENTIALS に認証用のjsonファイルを指定する

json としては、 サービスアカウントや、IdPを通して手にいれる認証情報ファイルがある

2: デフォルトのパスに認証ファイルを配置する
GOOGLE_APPLICATION_CREDENTIALS が設定されていない場合は以下のパスを見に行ってくれる
```
$HOME/.config/gcloud/application_default_credentials.json 
```

3: metadata server を見に行く

<!--stackedit_data:
eyJoaXN0b3J5IjpbMjA4MDEwNDYzMSwtMTEyMjU5ODgyNCwtNT
kwMzQ1MTI2XX0=
-->