
# 基本概念
- firestore上のデータは全てcollection と document である
  - 常にdocumentはcollection の配下にあり、collection配下に直接collectionを置くこともできない
  - collection → document → sub collection → document という形で交互にネストしていくことは可能


## Create document
- *DocumentRef.Set
    -  documentに対して、IDを指定した上で作成する
	- デフォルトだと、完全に上書きされる
	- optionとして、 merge を指定すると既存のドキュメントとmergeされる

- Add
  - collectionに対して、ドキュメントが新規追加される
 - IDは自動採番される	

> Written with [StackEdit](https://stackedit.io/).
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE0ODIyMDA5NzcsMTU3NTM0MTU1OV19
-->