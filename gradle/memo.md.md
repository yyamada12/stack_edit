

# gradle

## 資料集

- [kotlin DSLへの乗り換え](https://blog1.mammb.com/entry/2020/11/14/090000)
- [Gradle のタスク定義のあれこれ](https://qiita.com/opengl-8080/items/0a192b62ee87d8ac7578)

## plugin
プラグインの動作は
Gradleのタスク定義のあれこれの[プラグインの章](https://qiita.com/opengl-8080/items/0a192b62ee87d8ac7578#%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3) がわかりやすい

### kotlin 系プラグイン
kotlinのプロジェクトをgradleでビルドするために必要

JVMがターゲットの場合は以下のように書く
```
plugins {
  kotlin("jvm")
}
```
他のターゲットは js や multi platform になる

[公式ドキュメント](https://kotlinlang.org/docs/gradle.html#plugin-and-versions)

`kotlin` は DSL で、`org.jetbrains.kotlin` の https://plugins.gradle.org/search?term=org.jetbrains.kotlin

https://github.com/breandan/kotlin-dsl/blob/70aca202558f2f6e43cd8ead3ec95d669bfd7b33/buildSrc/src/main/kotlin/codegen/GenerateKotlinDependencyExtensions.kt#L78-L88





## kotlin DSL

### task 登録の書き方
色々あるの注意
前提知識: configuration avoidance
 タスクを登録だけして、作成しない、というのが `configuration avoidance` 
 基本的には登録だけする方がパフォーマンスが良い
逆に、タスク登録と同時に作成までする書き方は `eager` な構成という

① configuration avoidance な書き方 
```
tasks.register("タスク名") {  
  doFirst { println("hello") }
}  
```

or  
``` 
val hello by tasks.registering {  
    doFirst { println("hello") }
}
```
↑これはkotlinの委譲を利用した書き方で、本質的には同じ


② eager な書き方
```  
task("タスク名") {  
  doFirst { println("hello") }
}  
```
or
```
tasks.create("タスク名") {
    doFirst { println("hello") }
}
```


## その他 tips
###  build.gradle でバージョンを変数でまとめる方法

buildScript {} に ext で 拡張プロパティを設定してあげると、 build.gradle 内で project.ext.xxxversion とかで参照する必要なく $xxxversion で参照できる


<!--stackedit_data:
eyJoaXN0b3J5IjpbNjUzMTEzNzYwLC0xOTIwNzI0NzgzLC0xMT
Y1NTg1NDMsLTIwMzE4MDQ0MjgsLTk4NjAyMjUzMV19
-->