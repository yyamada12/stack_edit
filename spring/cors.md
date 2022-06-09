Spring アプリケーションのCORS設定。

https://spring.pleiades.io/guides/gs/rest-service-cors/


@SpringBootApplication つけてるクラスに↓みたいなコードを足せば良い。


```
	@Bean
	public WebMvcConfigurer corsConfigurer() {
		return new WebMvcConfigurer() {
			@Override
			public void addCorsMappings(CorsRegistry registry) {
				registry.addMapping("/greeting-javaconfig").allowedOrigins("http://localhost:8080");
			}
		};
	}
```

addMapping()の引数はAPIのパス。
全パスに対して行うときは "/**" と指定すれば良い。
