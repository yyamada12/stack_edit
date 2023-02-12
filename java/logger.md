# java logging 

とりあえず、めちゃくちゃややこしい

https://qiita.com/kero3/items/0033adca07a585623768

> log4jの後に標準のjava.util.loggingが作られたが、log4jが使いやすかったため、完全には普及しなかった。  
そのためログライブラリに依存しないようなインタフェースが必要とされた。  
ライブラリ毎にログライブラリが異なると、1つのファイルにログをまとめるのが大変になるので、基本的にはSLF4Jを使用するのが良い。

とのこと


https://qiita.com/nisshiee/items/c5388f1d472ec86295e0
これがわかりやすそう

https://www.bunkei-programmer.net/entry/2012/10/20/java%E3%81%AE%E3%83%AD%E3%82%AC%E3%83%BC%E3%81%8C%E5%A4%9A%E3%81%99%E3%81%8E%E3%81%A6%E8%A8%B3%E3%81%8C%E8%A7%A3%E3%82%89%E3%81%AA%E3%81%84%E3%81%AE%E3%81%A7%E6%95%B4%E7%90%86%E3%81%97%E3%81%A6
のまとめとかも良い

https://qiita.com/k_ui/items/7ed7d9f9c15dc9bcc26f も


SLF4jとかの話は
https://qiita.com/NagaokaKenichi/items/9febd2e559331152fcf8 が良い


https://www.alibabacloud.com/blog/java-logging-frameworks-summary-and-best-practices_598223

現時点でのまとめは↑とか↓とか

https://stackify.com/compare-java-logging-frameworks/


https://blog.kengo-toda.jp/entry/2021/05/31/200807 では、SLF4j + Logback はやめて log4j2 を使え、とやたら上位に出てくる

spring frameworkでの議論も見ておきたい
https://github.com/spring-projects/spring-framework/issues/19081

<!--stackedit_data:
eyJoaXN0b3J5IjpbMTY2MzMzMzM2MSw3MzA5OTgxMTZdfQ==
-->