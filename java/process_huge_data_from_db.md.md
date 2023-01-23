# Javaで大量のデータをSQLで読み取る場合の書き方


普通に書くと、メモリに乗り切らずOOMが発生してしまうので

- jdbc の fetchSizeを設定する
https://www.techscore.com/blog/2019/02/27/jdbc-setfetchsize-%E3%81%A7%E3%81%AF%E3%81%BE%E3%81%A3%E3%81%9F%E8%A9%B1/

- MyBatisを利用する場合は、Cursorを利用するhttps://qiita.com/riekure/items/761abcf54c9216db596f


といった対応をする
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTUxNzI4NDQ3N119
-->