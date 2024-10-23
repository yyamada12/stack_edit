# LLM のAPIの叩き方


## OpenAI

API ごとに指定できるモデル一覧: https://platform.openai.com/docs/models/model-endpoint-compatibility
モデル一覧: https://platform.openai.com/docs/models
料金: https://openai.com/ja-JP/api/pricing/

### token について

専用の tokenizer が利用されている
https://platform.openai.com/tokenizer

modelによって利用する encoding が変わっていて、それによってtoken数が変わってくる模様。
cl100k_base とか o200k_base とかがある

プログラムから計測する際は、tiktoken というライブラリを利用するとよい。 encoding もtiktoken で調べられる
https://github.com/openai/tiktoken?tab=readme-ov-file

参考: https://zenn.dev/microsoft/articles/3438cf410cc0b5

### chat completion

https://platform.openai.com/docs/api-reference/chat/create

post  https://api.openai.com/v1/chat/completions


- messages
	- prompt を指定する
	- 過去の会話の流れの形式で、配列で指定する
	- system, user などの発言を指定できる
- model
	- model 名を指定する
	- 
- 
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE5OTQ3ODA4MzgsMTEzMjEwODQ5MV19
-->