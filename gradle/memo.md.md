

# gradle

## 資料集

- [kotlin DSLへの乗り換え](https://blog1.mammb.com/entry/2020/11/14/090000)
- [Gradle のタスク定義のあれこれ](https://qiita.com/opengl-8080/items/0a192b62ee87d8ac7578)

## plugin
プラグインの動作は
Gradleのタスク定義のあれこれの[プラグインの章](https://qiita.com/opengl-8080/items/0a192b62ee87d8ac7578#%E3%83%97%E3%83%A9%E3%82%B0%E3%82%A4%E3%83%B3) がわかりやすい

利用しているpluginのソースコードやドキュメントは、それぞれ気合いで探すしかない模様

gradle plugin portal にはほぼ情報ない、、



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

`kotlin` は DSL で、[`org.jetbrains.kotlin` のplugin]( https://plugins.gradle.org/search?term=org.jetbrains.kotlin
) を設定するためのもの
[参考](https://github.com/breandan/kotlin-dsl/blob/70aca202558f2f6e43cd8ead3ec95d669bfd7b33/buildSrc/src/main/kotlin/codegen/GenerateKotlinDependencyExtensions.kt#L78-L88)

### spring boot プラグイン
```
plugins {
  id("org.springframework.boot") version "2.7.0"
}
```
[ソースコード](https://github.com/spring-projects/spring-boot/tree/main/spring-boot-project/spring-boot-tools/spring-boot-gradle-plugin)
[公式ドキュメント](https://spring.pleiades.io/spring-boot/docs/current/gradle-plugin/reference/htmlsingle/)

- bootRunやbootJar タスクを追加
- 他のプラグインが適用された場合に、プロジェクト設定に変更を加える
	- kotlin プラグインがあると、spring boot のkotlinバージョンをプラグインのバージョンに合わせる、など
- spring boot 用の gradle DSL を追加
などの動作が行われる

### spring boot dependency management プラグイン
```
id("io.spring.dependency-management") version "1.0.11.RELEASE"
```

[ソースコード](https://github.com/spring-gradle-plugins/dependency-management-plugin)

spring bootの依存関係管理のためのプラグイン
一応spring boot を使ってなくても使える

前述のspring boot プラグインを入れていると、このプラグインを入れることで自動的に適用してくれる

バージョンを管理しているライブラリの具体的なバージョンを知りたいときは下記レポジトリを参照すれば良い
https://github.com/spring-projects/spring-boot/blob/main/spring-boot-project/spring-boot-dependencies/build.gradle

### plugin.spring プラグイン
```
kotlin("plugin.spring") version "1.6.21"
```
[アノテーション付与でopenにしてくれる「kotlin-spring」の正体を見てみる](
https://bottoms-programming.com/archives/kotlin-spring.html) に全部書いてた
元々は [all-open-plugin](https://kotlinlang.org/docs/all-open-plugin.html#gradle) というやつらしく、
kotlin の デフォルト final だと spring が困るので、 `@Component` などのアノテーションがついたクラスに open 修飾子をつけるようにするプラグインの模様。


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
eyJoaXN0b3J5IjpbLTg5OTYyNDg5NCwtNzU5OTEwNDAzLDE0OT
M4OTgyMzUsLTE3NjAyMTI0MTksLTE5MjA3MjQ3ODMsLTExNjU1
ODU0MywtMjAzMTgwNDQyOCwtOTg2MDIyNTMxXX0=
-->