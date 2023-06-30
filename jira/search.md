
# Jira 検索

検索対象となるのは、あくまで「課題」のみっぽい

検索の仕組みは3種類
1: クイック検索
→ 画面右上の検索窓からやるやつ
検索の仕方としては
- 課題のキーを入れる
- 課題の要約・説明・コメントに含まれる単語をフリーワードで探す
- [スマート クエリ](https://ja.confluence.atlassian.com/jiracoreserver073/quick-searching-861257204.html#Quicksearching-Smartquerying) を入れる


2: 基本検索
フィルターから、GUIで選ぶやつ。

3: 詳細検索 (JQL)
https://support.atlassian.com/jira-service-management-cloud/docs/use-advanced-search-with-jira-query-language-jql/

## JQL
https://support.atlassian.com/jira-service-management-cloud/docs/what-is-advanced-search-in-jira-cloud/

### 利用できる課題のフィールド一覧
https://support.atlassian.com/jira-software-cloud/docs/jql-fields/
代表的なところは、以下

- assignee (担当者)
- creator (課題の作成者、報告者とは一応別)
- reporter (報告者)
- type (課題タイプ)
→ 選択できる課題タイプを確認したい時は、新規で課題を作成して、プルダウンの中身を確認すると良い
- label 
- status
→選択できるステータスを確認したい時は、workflowを確認すると良い
- "epic link" (エピック名 or エピックの課題のキーを指定)
- summary (要約: タイトルっぽく、課題の一番上に出るやつ)
- description (説明: メインで色々書くところ)
- comment

文字列系は、 ~ と !~ で検索する

正規表現は使えないが、
[専用の検索構文](https://ja.confluence.atlassian.com/jiracoreserver/search-syntax-for-text-fields-939937723.html)を利用できる

`?` : 一文字のワイルドカード
`*`: 複数文字のワイルドカード

`+`: 先頭につけると、その用語が必須で含まれることが条件となる
`-`: 先頭につけると、その


**ボードに含まれる課題を検索したい場合**
ボードは、フィルターによって構成されている
よって、ボードに設定されているフィルターと同じ内容をJQLに設定することで、ボード内の課題を検索することができる。

**自分をフィルター条件に設定する場合**
メールアドレスを指定すると、候補で出てくるっぽいが、 `currentUser()`を指定するのでもいける
ex) assignee = currentUser()



### 利用できる演算子、キーワード
https://support.atlassian.com/jira-software-cloud/docs/jql-operators/
https://support.atlassian.com/jira-software-cloud/docs/jql-keywords/

- =
- !=
- >
- >=
- IN
- NOT IN
- CONTAINES (~)
- DOES NOT CONTAIN(!~)
- IS
- IS NOT
- WAS
- WAS IN
- AND
- OR
- NOT
- EMPTY
- NULL
- ORDER BY
あたりを使いそう

### 利用できる関数
https://support.atlassian.com/jira-software-cloud/docs/jql-functions/


<!--stackedit_data:
eyJoaXN0b3J5IjpbMjAyODUxNTI3OSwxOTQ5OTMyMjU3LDc4MT
g0NTI3MF19
-->