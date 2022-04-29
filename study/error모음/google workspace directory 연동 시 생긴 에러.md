# google workspace directory 연동 시 생긴 에러
일반 프로젝트에서 실행 했을 시에 구글 OAuth 로그인 창이 뜨고 구글 로그인 시 디렉토리 정보를 가져오는 로직을 작성하였다.   
일반 프로젝트에서는 잘 수행이 되었으나...   
   
스프링 부트 MVC 프로젝트에 service에 적용하였으나 구글 로그인 페이지(새창)이 뜨지 않고 console 창에 해당 uri만 보여주었다...

![1](https://user-images.githubusercontent.com/89080095/162391780-6d7d923e-a6d5-4b93-b11c-6027228a8201.PNG)
자동으로 창을 띄우기 위해 이렇게 저렇게 하였으나 잘 되지 않았다ㅠ  
하지만 결국 성공하였다.
### 해결방법
```java
@SpringBootApplication
public class AdminApplication {

//  for dev
	public static void main(String[] args) {
		//SpringApplication.run(Admin.class, args);
		// 구글 연동 시 창이 안뜨는 이슈로  인해 headless false 로 변경
		SpringApplicationBuilder builder = new SpringApplicationBuilder(Admin.class);
		builder.headless(false).run(args);
		
	}
```

----> 리눅스 실 서버에 올리니 에러가 떴다...
```
org.springframework.web.util.NestedServletException: Handler dispatch failed; nested exception is java.lang.NoClassDefFoundError: Could not initialize class sun.awt.X11.XToolkit
```
---> 일단 이렇게 수정
```java
	public static void main(String[] args) {
		//SpringApplication.run(SiteAdminApplication.class, args);
		// 구글 연동 시 창이 안뜨는 이슈로  인해 headless false 로 변경
		SpringApplicationBuilder builder = new SpringApplicationBuilder(SiteAdminApplication.class);
		builder.headless(false); //.run(args);
		System.setProperty("java.awt.headless", "true");
		ConfigurableApplicationContext context = builder.run(args);
		
	}
```
### 원인
Spring Boot 구동원리 공부 후에 올리도록 하겠다.   
java.awt.HeadlessException -> 관련 검색어


