

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
  kotlin("jvm")
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
eyJoaXN0b3J5IjpbLTEwMDAyNzkwOTIsMTQ5Mzg5ODIzNSwtMT
c2MDIxMjQxOSwtMTkyMDcyNDc4MywtMTE2NTU4NTQzLC0yMDMx
ODA0NDI4LC05ODYwMjI1MzFdfQ==
-->