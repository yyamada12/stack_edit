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

まず、 vscode に poetry が作成した仮想環境を認識してもらう必要がある


https://zenn.dev/pesuchin/articles/4c128aeb60cb42204311

とりあえず
```
poetry config virtualenvs.in-project true
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTkxNjM3ODkxOF19
-->