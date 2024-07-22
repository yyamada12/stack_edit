# poetry

pip + virtualenv 的なツール
npm の python 版だと思ってもいい

参考
https://qiita.com/ksato9700/items/b893cf1db83605898d8a

## コマンド

- poetry init
既存のプロジェクトで初期化
- poetry new ${project-name}
新規プロジェクトを作成

- poetry install
仮想環境のセットアップ
virtualenv の作成 + 依存関係のインストール
が行われる

- poetry shell
仮想環境に入る

- poetry run
仮想環境でpythonコマンドを実行する

## VSCodeでのデバッグ

### vscode に poetry が作成した仮想環境を認識してもらう


https://zenn.dev/pesuchin/articles/4c128aeb60cb42204311

以下の3つのやり方があるが、ブログでおすすめしているように3つ目一択
-   poetry shellで仮想環境に切り替えてからVSCodeを開く
-   .vscode/setting.jsonにpoetryによって自動生成された仮想環境のパスを入力する
-   プロジェクト直下で仮想環境を作成するようにPoetryの設定を変更する(個人的におすすめ)


poetry install する前に以下の設定を入れておく
```
poetry config virtualenvs.in-project true
```

もし、すでに poetry install してしまっている場合

```
poetry env list
poetry env remove <削除したいenv>
```

という形で一度削除してから poetry install しなおせば良い


### launch.json
```
{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
        {
            "name": "Python: FastAPI",
            "type": "python",
            "request": "launch",
            "module": "uvicorn",
            "args": [
                "main:app",
                "--reload"
            ],
            "jinja": true,
            "justMyCode": true,
        }
    ]
}
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTQzNDU3MTE5NCwxOTI5MzEwMjMzXX0=
-->