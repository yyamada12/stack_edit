# PostgreSQL partition 


公式ドキュメント
https://www.postgresql.jp/document/15/html/ddl-partitioning.html


## trial

テーブル作成
```
CREATE TABLE measurement (
    city_id         int not null,
    logdate         date not null,
    peaktemp        int,
    unitsales       int
) PARTITION BY RANGE (logdate);
```


パーティション作成
```
CREATE TABLE measurement_y2006m02 PARTITION OF measurement
    FOR VALUES FROM ('2006-02-01') TO ('2006-03-01');

CREATE TABLE measurement_y2006m03 PARTITION OF measurement
    FOR VALUES FROM ('2006-03-01') TO ('2006-04-01');
```


データ挿入
```
INSERT INTO measurement VALUES (1, '2006-02-15', 1, 1);
```

パーティションに直接挿入も可能
```
 INSERT INTO measurement_y2006m02 VALUES (2, '2006-02-28', 2, 2);
```

パーティションの範囲外の値はエラーになる
```
INSERT INTO measurement VALUES (1, '2006-01-15', 1, 1);
```
↓
```
ERROR:  no partition of relation "measurement" found for row
DETAIL:  Partition key of the failing row contains (logdate) = (2006-01-15).
```


## ハッシュパーティション
ハッシュの場合も、 MODULES と REMINDER を設定して、おyパーティションを作成する必要がある
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUzMzU0Njg5OV19
-->