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

※ legacy の completion と chat completion があるので注意

### chat completion

https://platform.openai.com/docs/api-reference/chat/create

post  https://api.openai.com/v1/chat/completions


- messages
	- prompt を指定する
	- 過去の会話の流れの形式で、配列で指定する
	- system, user などの発言を指定できる
- model
	- model 名を指定する
- max_tokens (deprecated), max_completion_tokens
	- 出力させるtoken の最大値を指定する。基本は、モデルの最大値をそのまま指定するのがよさそう



### azure の場合

https://learn.microsoft.com/en-us/azure/ai-services/openai/reference#chat-completions

POST https://{endpoint}/openai/deployments/{deployment-id}/chat/completions?api-version=2024-06-01

`endpoint`, `deployment-id` は Azure OpenAI Studio で設定する必要がある

指定できるパラメータは基本的には同じになる


### python SDK
https://github.com/openai/openai-python/tree/main

azure も対応している
```
from openai import AzureOpenAI
```

基本的にはAPI呼び出す時に指定する
<!--stackedit_data:
eyJoaXN0b3J5IjpbMzI4MTc3NDMxLDE0OTU5OTQ2NzRdfQ==
-->