# PostgreSQL partition 


公式ドキュメント
https://www.postgresql.jp/document/15/html/ddl-partitioning.html


サンプル

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
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTY0ODg5NTc5OF19
-->