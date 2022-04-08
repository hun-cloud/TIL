# Spring-boot security 적용 시 Post 404 에러
Spring security 적용 시 기본적으로 csrf를 막기 위하여 활성화가 되어있다. 때문에 csrf체크를 하여   
@GetMapping 호출 시 문제가 없지만 @PostMapping 호출 시 404에러를 발생한다. 이것을   
해결 하기 위해 security 설정 파일에서 csrf().disable()를 삽입하면 해결 가능하다.
```java
@Override
  protected void configure(HttpSecurity http) throws Exception{
    http
        .csrf().disable();
  }
```
### csrf 란
> 웹 어플리케이션 취약점 중 하나로 사용자가 자신의 의지와 무관하게 공격자가 의도한 행동을 하여
> 특정 웹 페이지를 보안에 취약하게 한다거나 수정, 삭제 등의 작업을 하게 만드는 공격 방법을 의미합니다.


[출처] [https://pooney.tistory.com/55](https://pooney.tistory.com/55)   
[참조] [https://brownbears.tistory.com/251](https://brownbears.tistory.com/251)
