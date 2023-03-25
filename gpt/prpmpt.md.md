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


## 使えそうな定型分
```
# 命令文:
あなたはプロのxxxです。入力文にある内容を、制約条件を満たしながら、出力例に従って、テーブルにまとめてください。

# 入力文:
[1] YYYにおいて常に見るべきKPI
[2] [1]の見るべきポイント
[3] [2]について、来週行えるボリュームの施策案
[4] [2]について、3ヶ月かけて行う施策案

# 制約条件:
- ZZZから取得できるデータを対象にしてください
- KPIは30個あげてください。
- 見るべきKPIに優先順位をつけて、優先度が高い順から並べてください。

# 出力例:
[1]の各項目について、[2]の項目を上げ、[3][4]を書く。これをテーブルの1行ずつまとめてください。
```


## プロンプトデザイン

http://soysoftware.sakura.ne.jp/archives/3691

```
私のプロンプトエンジニアになって欲しい。あなたの目標は、私のニーズに合わせて最高のプロンプトを作るのを手伝ってもらうことです。そのプロンプトは、ChatGPTであなたが使用するのに使われます。
次のプロセスに従ってください。
1.  あなたの最初の応答は、プロンプトが何についてであるべきかを私に尋ねることです。
私は私の答えを提供しますが、次のステップを経て、継続的な反復を通じて改善する必要があります。
2.  私の入力に基づいて、2つのセクションを生成します。
a) 改訂されたプロンプト（書き直されたプロンプトを提供します。明確、簡潔で、簡単にあなたが理解できるものにする必要があります）
b) 提案（プロンプトを改善するためにプロンプトを含めるべき詳細について提案する）
c) 質問（プロンプトを改善するために私から必要な追加情報について、関連する質問をしてくだい）
3.  この反復プロセスは、私があなたに追加情報を提供し、あなたが改訂されたプロンプトセクションのプロンプトを更新し、私が完了したというまで続けます。
まずは、「PythonとShapelyでGIS入門」という記事のブログを作成するためのプロンプトを生成してください。
```
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMTQxNzgzOTAsLTgwMTMxMzAyMCwxMD
E4NzI5OTUxLDE5OTI1MzAxMDEsLTk3NTYzMjkyOCwxMDY0MjI0
ODAwLDEzNzAzMDYyNzBdfQ==
-->