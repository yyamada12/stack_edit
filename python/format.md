
# python format

python は linter, formatter 系が色々あり、組み合わせることが多い


- mypy
- black
- isort
- autoflake 

etc


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


<!--stackedit_data:
eyJoaXN0b3J5IjpbMTExNzcxODAzMl19
-->