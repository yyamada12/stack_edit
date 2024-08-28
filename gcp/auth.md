# GCP での 認証方法まとめ

ref: https://cloud.google.com/docs/authentication

## user identity and workload identity
https://cloud.google.com/iam/docs/google-identities

人間が使う、 user 用の identity とシステムが使う workload 用の identity が存在する

workload用の identity 

CLIの場合は、 user 用の identity を使って認証することもできるし、 workload 用の identity を使って認証することもできる


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

3: metadata server 
GOOGLE_APPLICATION_CREDENTIALS にも デフォルトのパスにも認証情報がない場合は、 metadata server を見に行く  
これはGCPのサーバーから参照される想定のもの


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE4MTI1MTA5LC0xMTIyNTk4ODI0LC01OT
AzNDUxMjZdfQ==
-->