
# 基本概念
- firestore上のデータは全てcollection と document である
  - 常にdocumentはcollection の配下にあり、collection配下に直接collectionを置くこともできない
  - collection → document → sub collection → document という形で交互にネストしていくことは可能


## Create document
- Set
	- デフォルトだと、完全に上書きされる
	- optionとして、 merge を指定すると既存のドキュメントとmergeされる

- 

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTIxMTk3MjEyOTQsMTU3NTM0MTU1OV19
-->