# オブジェクトリレーション構造パターン

## 一意フィールド
これは単に、primary key を フィールドにしようという話。
- 意味のあるカラムを primary key として使うか、連番のような代理キーを primary key として使うか
- 複数カラムからなる primary key の場合、 Key オブジェクトを作っておくと汎用かできるぜ
的なことがメインで書いてある

## マッピング
テーブル間の1対多、多対多の関係をオブジェクトでどのように表現するかという話

### 1対多の場合
外部キーマッピングと依存マッピングから選択する



- 外部キーマッピング
  - RDB内の表現と同じく、子のフィールドに親のオブジェクトを持つという構成。
  - 
class Album {
  private Artist artist;
}
<!--stackedit_data:
eyJoaXN0b3J5IjpbLTEzMjU3NzcwOTgsLTE5MDAwNjczODZdfQ
==
-->