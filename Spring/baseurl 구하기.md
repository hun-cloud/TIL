# baseurl 구하기
baseurl을 사용하여 http 통신을 해야할 일이 생겼다.
스프링에서 제공하는 클래스로 간단하게 baseurl를 구할 수 있었다.   

```java
String baseUrl = ServletUriComponentsBuilder.fromCurrentContextPath().build().toUriString();
```
