Spring での Data Sourceの設定

大体公式ドキュメントに書いてる
https://spring.pleiades.io/spring-boot/docs/current/reference/html/howto.html#howto.data-access

1. DataSourceProperties に対して @ConfigurationProperties を利用して application.yml の設定値を適用
2. 上記の properties から、 DataSource を生成

というのが良さそうな組み合わせ

```
properties.initializeDataSourceBuilder().type(HikariDataSource.class).build();
```


Spring Boot の AutoConfigure を利用する場合は、 application.yml の spring.datasource.url などに設定する

(↓あたりを読み込むしかない)
https://github.com/spring-projects/spring-boot/blob/main/spring-boot-project/spring-boot-autoconfigure/src/main/java/org/springframework/boot/autoconfigure/jdbc/DataSourceAutoConfiguration.java 



<!--stackedit_data:
eyJoaXN0b3J5IjpbLTcxMDM3ODI4NCw0ODY5MjE2NDBdfQ==
-->