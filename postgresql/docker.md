# PostgreSQL Docker

compose.yaml
```
version: '3'
services:
  db:
    image: postgres:15
    volumes:
      - postgres_data:/var/lib/postgresql/data/
    environment:
      POSTGRES_USER: postgres
      POSTGRES_PASSWORD: password
      POSTGRES_DB: sample
    ports:
      - "5432:5432"

volumes:
  postgres_data
```

接続コマンド
```
psql -h localhost -U postgres -d sample
```


大量データの挿入方法

```
INSERT INTO favorites (user_id, item_id)
SELECT md5(random()::text), md5(random()::text)
FROM generate_series(1, 10000000);
```
1億レコードだと、かなり時間かかる
1000万レコードくらいなら、10分かからないくらい
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTE0MjMxMjQyMF19
-->