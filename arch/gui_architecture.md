# GUI Architecture

  

Martin Fowler の Further Patterns of Enterprise Application Architecture の 一部

https://www.martinfowler.com/eaaDev/uiArchs.html

  

- 概念
  - form
    - ユーザーが入力を行うためのパーツのまとまりのことをさしていそう
    - HTML でいえば、 form タグがそれに当たりそう
  - control
    - ユーザーが入力を行うためのパーツのことをさしていそう
    - HTML で言えば、 input タグがそれに当たりそう
  - widget
    - control と同じものを指していそう
    - widget というからには、form 以外のパーツに対しても widget というかも
  - 3 つの data
    - record state
      - データベースに永続化されたデータ
    - session state
       - アプリケーションのメモリ上に存在するデータ
      - メモリ上の record set にある、という表現が使われている (PoEEE に出てくる table data gateway のレコードセットのことだと思われる)
      - ユーザーがデータの保存操作をすると、record state とマージされる
    - screen state
      - GUI コンポーネント自体の中にある状態で、画面上に表示されているデータ
      - session state とどのように同期を取るかが重要
  - data binding
    - session state と screen state の同期を取るための方法
    - 一方の変更が、すぐにもう一方に反映されるための仕組み
    - 無限ループ(session state が更新され、それによって screen state が更新され、さらにそれによって session state が更新され、、、)を避ける必要があり、flow sync が使われる
  - application model, presentation model, view model
    - すべて同じものを指していそう?
    - 発展的に application model → presentation model → view model と進化していった?
    - (後の例の variance のような)ドメインに関係のない表示ロジックや表示用の state も管理できるような、view のための model
    -  > The main difference between using an application model and classic MVC is that we now have an intermediate class between the domain model class (Reader) and the widget - this is the application model class.

  - flow sync vs observer sync
    - observer sync は observer パターン で同期する
      - 更新される側は、あらかじめ更新を通知すべき object が登録されている。
      - 更新される側は、登録されている object に関しては知らない。observer interface さえ満たしていれば良い。
      - 更新された際には、登録されている object 全てに更新を通知する。
    - flow sync は手続き的に更新する
      - A を更新した際に、どの object に反映させなければならないかを知っているオブジェクトが存在。
    - view を描画する際に、明示的にモデルからデータを取得して反映するとか、ある control の更新を他の control に反映するために、form が手続き的に更新するとか。
- サンプルで出てくる UI 要素の種類
  - セレクトボックス
  - text を入力する field
    - 入力した値が、そのまま DB に保存される
  - text を出力する field
    - DB に保存されている値が、そのまま表示される
  - 他の text field から計算された値が表示される field
    - さらに、計算された値によって表示(色)が変化する
- サンプルアプリケーション
  - アイスクリーム粒子濃度管理システム
    - アイスクリーム濃度を記録し、目標値との差分を表示するためのシステム
  - 以下を含む form から形成される
    - Station ID
      - station ID を リストから選択できる control
    - Date
      - date を入力する control
    - Target
      - 設定された target を表示する control
    - Actual
      - actual を入力する control
    - Variance
      - actual と target の差を計算し、色付きで表示してくれる control
        - target を 10% 以上下回る場合は赤色
        - target を 5% 以上上回る場合は緑色

  

## Forms and Controls

  

- Form が複数の Control を含む形で作られる

- 個々の Control の screen state は、 control の property (Web であれば、HTML の name 属性とかになりそう) に session state の 名前を指定することで、data binding を行う

- 基本的にはこれによって、session state の値を screen state に反映するし、

ユーザーが入力した値(screen state)を session state に反映する

- 一方で、Variance に関しては、 Control と 1:1 ではなく、 Actual と Target によって値が決まるので、Form が Actual の変更イベントを検知して、Variance の screen state を更新する (これによって、 data binding で session state も更新される)
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTkzNTU1MTg0N119
-->