# プロンプト作成のコツ

## 公式ドキュメント
https://platform.openai.com/docs/guides/completion

(2023/03/25)

- 指示や例を与えるのが大事
- 例は十分な量があればあるほど良い
- temperatureやtop_pの設定は大事
	- 答えが決まっているような問いの時は、どちらも小さい値を設定するとよい

### 分類タスクの場合

- 平易な言葉を使うこと
- どんな分類先があるのかを示すこと
- 一般的なタスクであれば、少ない例でも良い



### 会話の場合
- 意図を伝えると同時に、どのように振る舞うべきかを指示すると良い
	- 「親切で」とか「フレンドリー」とか
- IDをつける。下の例の HumanとかAI とか見たいな

```
Human: Hello, who are you? 
AI: I am an AI created by OpenAI. How can I help you today? Human:
```


### 間違ったことを言わせないために

- 正しい知識をinputしておく
	- (それができれば苦労しない気がするけど、、)
- I don't know  と答えて良いとinputする




<!--stackedit_data:
eyJoaXN0b3J5IjpbODk3MzEwOTA2LDEzNzAzMDYyNzBdfQ==
-->