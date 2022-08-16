Spring での Data Sourceの設定

大体公式ドキュメントに書いてる
https://spring.pleiades.io/spring-boot/docs/current/reference/html/howto.html#howto.data-access

DataSourceProperties に対して @Confi


Spring Boot の AutoConfigure を利用する場合は、 application.yml の spring.datasource.url などに設定する

(↓あたりを読み込むしかない)
https://github.com/spring-projects/spring-boot/blob/main/spring-boot-project/spring-boot-autoconfigure/src/main/java/org/springframework/boot/autoconfigure/jdbc/DataSourceAutoConfiguration.java 



<!--stackedit_data:
eyJoaXN0b3J5IjpbNDMyMTQzODA1LDQ4NjkyMTY0MF19
-->