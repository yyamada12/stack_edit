
# python format

python は linter, formatter 系が色々あり、組み合わせることが多い


- mypy
- black
- isort
- autof



## vscode で保存時にformatさせたい

formatOnSave では一つのformatter しか指定できないので、 RunOnSave を使うのも一つの手。

settings.json に以下のような設定を入れると、 autoflake + black を実行してくれる
```
    "emeraldwalk.runonsave": {
        "commands": [
            {
                "match": ".*\\.py$",
                "message": "Running autoflake...",
                "cmd": "poetry run autoflake --in-place --remove-all-unused-imports --remove-unused-variables ${file}"
            },
            {
                "match": ".*\\.py$",
                "message": "Running black...",
                "cmd": "poetry run black ${file}"
            }
        ]
    }
```


> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE4Mjc3ODY4MV19
-->