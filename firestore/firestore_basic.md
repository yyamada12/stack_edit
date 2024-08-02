
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

## Update Docu
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTExMzA1NzUxNjYsLTYyNzcxNTYxMCwxNT
c1MzQxNTU5XX0=
-->