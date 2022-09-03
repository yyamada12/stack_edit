
# jq チートシート

https://www.wakuwakubank.com/posts/676-linux-jq/

```
$ cat tmp.json   
{  
  "total_count": 3,  
  "items": [  
    {  
      "id": 111,  
      "name": "aaa",  
      "owner": {  
        "id": 1111111,  
        "type": "Organization"  
      },  
      "size": 10  
    },  
    {  
      "id": 222,  
      "name": "bbb",  
      "owner": {  
        "id": 2222222,  
        "type": "User"  
      },  
      "size": 30  
    },  
    {  
      "id": 333,  
      "name": "ccc",  
      "owner": {  
        "id": 3333333,  
        "type": "Organization"  
      },  
      "size": 25  
    }  
  ]  
}
```


## mapで新しい配列を生成


```json
$ cat tmp.json | jq -r '.items | map({ name: .name, owner_id: .owner.id })'
[
  {
    "name": "aaa",
    "owner_id": 1111111
  },
  {
    "name": "bbb",
    "owner_id": 2222222
  },
  {
    "name": "ccc",
    "owner_id": 3333333
  }
]
```

<!--stackedit_data:
eyJoaXN0b3J5IjpbNzE3NTY4NDg0XX0=
-->