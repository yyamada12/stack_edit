# LLM のAPIの叩き方


## OpenAI

API ごとに指定できるモデル一覧: https://platform.openai.com/docs/models/model-endpoint-compatibility
モデル一覧: https://platform.openai.com/docs/models
料金: https://openai.com/ja-JP/api/pricing/



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
eyJoaXN0b3J5IjpbLTkyMTk1NjE2NywxMTMyMTA4NDkxXX0=
-->