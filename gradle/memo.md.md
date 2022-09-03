

# gradle

## 資料集

- [kotlin DSLへの乗り換え](https://blog1.mammb.com/entry/2020/11/14/090000)
- [Gradle のタスク定義のあれこれ](https://qiita.com/opengl-8080/items/0a192b62ee87d8ac7578)

## kotlin DSL

### task 登録の書き方
色々あるの注意
前提ちs
 
```
tasks.register("タスク名") {  
  doFirst {  
    println("hello")  
  }  
}  
```

or  
``` 
val hello by tasks.registering {  
    doFirst {  
        println("hello")  
    }  
}
```
or  
```  
task("タスク名") {  
  doFirst {  
    println("hello")  
  }  
}  
```


## その他 tips
###  build.gradle でバージョンを変数でまとめる方法

buildScript {} に ext で 拡張プロパティを設定してあげると、 build.gradle 内で project.ext.xxxversion とかで参照する必要なく $xxxversion で参照できる


<!--stackedit_data:
eyJoaXN0b3J5IjpbMzE4NTY0NTE5LC05ODYwMjI1MzFdfQ==
-->