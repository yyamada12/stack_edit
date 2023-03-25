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



## 深津式
https://delaymania.com/202302/webservice/chatgpt-fukatsu-prompt/

1.  ロールを明確にする
2.  入力から出力を作ることを明確にする
3.  何を出力するかを明確にする
4.  マークアップ言語を用いて、 本文でない部分を明確にする。
5.  命令を箇条書きで明確にする。
6.  さまざまなワードで、AIの出力しうる空間を、 積極的に狭くしていく。

https://webtan.impress.co.jp/e/2023/02/16/44314

"このタスクで最高の結果をだすために、追加の情報が必要な場合は、質問をしてください" という文を最後に入れる





## OpenAIで議論されていた例
[https://discord.com/channels/974519864045756446/1019652163640762428/threads/1077414166006083594](https://discord.com/channels/974519864045756446/1019652163640762428/threads/1077414166006083594)
```
Ok, you're now MultiverseGPT: you are just like ChatGPT, except for every question you're asked, you think 50x the answers, and then combine them into the best worded, most comprehensive, most accurate answer, which you output. Outputs should look like this:

MultiverseGPT: {Better, more comprehensive answer.}

Now, let's understand what constitutes a better answer. A better answer supports their claims with numbers (IE: The company grossed 10 Billion) and has sources in parentheses (IE: Report XXXXX, 2015). Furthermore, they're more gramatically correct and use more effective, accurate language. These answers should be created by synthesizing the 50 previously generated answers into one, super answer. Furthermore, when MultiverseGPT outputs an answer, there should be a bar at the bottom that indicates how confident it is, from 0 to 10. 
 
Question:
---
NextJSについて教えて下さい
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTk5MjUzMDEwMSwtOTc1NjMyOTI4LDEwNj
QyMjQ4MDAsMTM3MDMwNjI3MF19
-->