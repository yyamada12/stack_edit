# MVX アーキテクチャについて

  

## これを見ろ

  

マーチン・ファウラーの記事

https://www.martinfowler.com/eaaDev/uiArchs.html

  

## そもそも解決したいこと

  

多分、、

  

- 関心を分離し、コードを分割したい

- 1 ファイルに、表示・操作・状態・データ・ビジネスロジックの全て書くと、fat になる

  

なぜ MVX が色々登場したのか？

MVC が最初で、それの問題点を解決するために MVP が現れ、さらに発展的に MVVM が現れたっぽい?

  

## 理解のための観点

  

- 前提として、プレゼンテーション層(ユーザーインターフェース)が主題となるアーキテクチャである

よって、フロントエンドやネイティブアプリにおけるアーキテクチャとしてよく出てくる

  

(レイヤードアーキテクチャとかとは視点が違う？)

  

- 出てくる登場人物としては

  

- ブラウザからの入出力

- 表示

- 文字列、数値などのデータを画面に表示する

- 操作

- ボタンのクリック

- フォームへのフォーカス

- スクロール

- 文字列の入力

など

- (ビューの)状態

- ダイアログの表示/非表示

- アコーディオンの開閉

- 入力された文字列

など

- (永続化された)データ

- ユーザーの情報

- ブログ記事

- ビジネスロジック

  

- M, V, X の依存、呼び出し関係

  

- 同期的な呼び出し(リクエスト&レスポンス or メソッド呼び出しで返り値受け取り)

- オブザーバー

- data binding

  

data binding も オブザーバーで実装されているきも。フレームワークやライブラいでやっている場合に data binding と言っていそう

  

- M, V, X の 1:1 or 1:多 の関係

  

-

  

- 時代背景

- そもそも、Web アプリケーション(やネイティブアプリ)のアーキテクチャとしてではなく、もっと昔から現れたもの

- MVC は 1970 年台(※)、MVP は 1990 年台とかに出てきたっぽい

- MVC の論文

- https://ics.uci.edu/~redmiles/ics227-SQ04/papers/KrasnerPope88.pdf

- 作者の note

- https://folk.universitetetioslo.no/trygver/themes/mvc/mvc-index.html

  

※ wiki に論文のリンクあり

https://ja.wikipedia.org/wiki/Model_View_Controller

  

## MVC

  

- 表示

view の責務

view は、model を参照して画面を描画する

  

- 操作

view は、操作を controller に伝える

  

- 状態

View が持つ、という意見(※1)と、View は状態を持たない(※2)、という意見がありそう

  

※1

  

※2

http://stackoverflow.com/a/101561

  

> The view simply renders and is completely stateless. In implementations of MVC, the View usually will not have any logic in the code behind.

  

- データ

model の責務
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTE3MzUzODg3MDFdfQ==
-->