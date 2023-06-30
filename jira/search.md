
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

代表的なところは、
- approvals
- assignee (担当者)
- category
- creator (課題の作成者、報告者とは一応別)
- reporter (報告者)




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
eyJoaXN0b3J5IjpbNzgxODQ1MjcwXX0=
-->