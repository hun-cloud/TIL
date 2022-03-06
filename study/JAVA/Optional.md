# Optional이란?
> T 타입 객체의 래퍼클래스 - Optional<?>
                 
### 래퍼클래스란?
> 8개의 기본 타입에 해당하는 데이터를 객체로 표현하기 위해 포장해주는 클래스
> 모든 종류의 객체를 저장이 가능하다.
> null 또한 가능하다.
### Optional을 사용하는 이유
> - null을 직접 다루는 것은 위험하다.
>   * NPE 가 발생할 수 있다. (NullPointException)
>   * 간접적으로 null을 다룰 수 있다.
>
> - null 체크를 해주어야 한다.
>   * if문이 필수 -> 코드가 지저분해진다.
  
### Optional<?> 객체 생성하기
```java
String str = "abc";
Optional<String> opt = Optional.of(str);
Optional<String> opt2 = Optional.ofNullable(str);
```
##### Optional.of()
> null을 허용하지 않는다. null값 넣을 시 NPE 발생

##### Optional.ofNallable()
> null을 허용한다. null값 넣을 시 NPE 발생X

```java
Optional<String> opt = null; // 널로 초기화 가능, 바람직하지 않음
Optional<String> opt2 = Optional.empty(); // 빈 객체로 초기화
```

### Optional<?> 객체의 값 가져오기   
```java
Optional<String> opt = Optional.of("abc");
String str1 = opt.get(); // opt에 저장된 값을 반환, null 이면 예외발생
String str2 = opt.orElse(""); // opt에 저장된 값이 null일 때 ""fmf qksghks
String str3 = opt.orElseGet(String::new); //orElse와 같으나 람다식을 사용 가능 () -> new String()
String str4 = opt.orElseThrow(NullpointException::new); // null이면 예외 발생 예외 종류를 지정가능
```

#### isPresent() = Optional 객체의 값이 null 이면 false 아니면 true를 반환
```java
if(Optional.ofNullable(str).isPresent()){ // if(str != null)
  System.out.print(str);
}
```
#### ifPresent() - 널이 아닐때만 작업수행, 널이면 아무 일도 안함
```java
Optional.ofNallable(str).ifPresent(System.out::println); // 람다식 사용가능
```

#### 예제는 다음 게시글에서 작성해 보겠습니다.
>참조링크
>[자바의 정석-기초편(남궁성)] : (https://www.youtube.com/watch?v=W_kPjiTF9RI)









