
# 基本概念
- firestore上のデータは全てcollection と document である
  - 常にdocumentはcollection の配下にあり、collection配下に直接collectionを置くこともできない
  - collection → document → sub collection → document という形で交互にネストしていくことは可能


# how to with golang 
## Create document
- *DocumentRef.Set
    -  documentに対して、IDを指定した上で作成する
	- デフォルトだと、完全に上書きされる
	- optionとして、 merge を指定すると既存のドキュメントとmergeされる

```
result, err := client.Collection("dummy").Doc("dummy").Set(ctx, dummy)
```

- *DocumentRef.Create
    -  documentに対して、IDを指定した上で作成する
	- 同一のIDがすでに存在すると、エラーになる
```
result, err := client.Collection("dummy").Doc("dummy").Create(ctx, dummy)
```

- *CollectionRef.Add
  - collectionに対して、ドキュメントが新規追加される
  - IDは自動採番される

```
docRef, result, err := client.Collection("dummy").Add(ctx, dummy)
```

- *CollectionRef.NewDoc()
  - IDの採番だけやってくれる
  - *DocumentRefが返ってくるので、それを使って Setを呼び出す

## Update Document
- *DocumentRef.Set
	- Create 同様

- *DocumentRef.Update
  - []firestore.Updateを利用して更新する
  - 上書きの危険はない

updateのオプション
- firestore.ServerTimestamp
	- current_timestampにupdateする
- firestore.ArrayUnion, firestore.ArrayRemove
	- 配列に対する操作ができる
- パスを.で繋げて指定
	- mapに対する操作ができる
- firestore.Increment
	- 数値の増減ができる
- firestore.Delete
  -   フィールドを削除できる

## Delete Document
- *DocumentRef.Delete
	- これ一択
	- **サブコレクションは削除されない**
	- サブコレクションは、コレクションの中のドキュメントを全て消す必要がある
	- *DocumentRef.Collections でサブコレクションのCollectionRefがiterator で取得できるので、そこから再帰的に消す形になる
	- cloud functionに実装して、それを呼び出すのが良いとされていそう
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTI2Nzg0MjEyMiwtMTYxNDYxNDUzOCwtNj
I3NzE1NjEwLDE1NzUzNDE1NTldfQ==
-->