# 스트림이란
지금까지 많은 수의 데이터를 다룰 때, 컬렉션이나 배열에 데이터를 담고 원하는 결과를 얻기 위해 for문이나 iterator를 이용해서 코드를 작성해왔다.
그러나 이러한 방식으로 작성된 코드는 너무 길고 알아보기 힘들다. 그리고 재사용성도 떨어진다.   
또 다른 문제는 데이터 소스마다 다른 방식으로 다뤄야한다는 것이다. Collections이나 Iterator와 같은 인터페이스를 이용해서   
컬렉션을 다루는 방식을 표준화 하기는 했지만, 각 컬렉션 클래스에는 같은 기능의 메서드들이 중복되어 정의되어 있다.   
예를 들어 List를 정렬할 때는 Collections.sort()를 사용해야하고, 배열을 정렬할 때는 Arrays.sort()를 사용해야 한다.  
   
이러한 문제점을 해결하기 위해 만든 것이 스트림이다. 스트림은 데이터 소스를 추상화하고, 데이터를 다루는데 자주 사용되는 메서드를 정의해 놓았다.   
데이터 소스를 추상화 했다는 것은 데이터 소스가 무엇이든 간에 같은 방식으로 다룰 수 있게 되었다는 것과 코드의 재사용성이 높아졌는 것을 의미한다.   
스트림을 사용하면 배열이나 컬렉션 뿐만 아니라 파일에 저장된 데이터도 모두 같은 방식으로 다룰 수 있다.   

예를 들어, 문자열 배열과 같은 내용의 문자열을 저장하는 List가 있을 때,
```java
String[] strArr = {"aaa","ddd","ccc"};
List<String> strList = Arrays.asList(strArr);
```
이 두 데이터 소스를 기반으로 하는 스트림은 다음과 같이 생성한다.
```java
Stream<String> strStream1 = strList.stream(); // 스트림을 생성
Stream<String> strStream2 = Arrays.stream(strArr);// 스트림을 생성
```
이 두 스트림으로 데이터 소스의 데이터를 읽어서 정렬하고 화면을 출력하는 방법은 다음과 같다.   
데이터소스가 정렬되는 것은 아니라는 것에 유의하자
```java
strStream1.sorted().forEach(System.out::println);
strStream2.sorted().forEach(System.out::println);
```
두 스트림 데이터 솟는 서로 다르지만 정렬하고 출력하는 방법은 완전히 동일하다.   
예전에는 아래와 같이 
```java
Arrays.sort(strArr);
Collections.sort(strList);
for(String str : strArr)
  System.out.println(str);
for(String str : strList)
  System.out.println(str);
```
스트림을 사용한 코드가 간결하고 이해하기 쉬우며 재사용도 높다는 것을 알 수가 있다.
## 스트림은 데이터 소스를 변경하지 않는다.
그리고 스트림은 데이터 소스로 부터 데이터를 읽기만 할 뿐, 데이터 소스를 변경하지 않는다는 차이가 있다.   
필요하다면 정렬된 결과를 컬렉션이나 배열에 담아서 반환할 수도 있다.
```java
//정렬된 결과를 새로운 List에 담아서 반환한다.
List<String> sortedList = strStream2.sorted().collect(Collections.toList());
```
## 스트림은 일회용이다.
스트림은 Iterator처럼 일회용이다. Iterator로 컬렉션의 요소를 모둘 읽고나면 다시 사용할 수 없는 것처럼   
스트림도 한번 사용하면 닫혀서 다시 사용할 수 없다. 필요하다면 다시 스트림을 생셩해야한다.
```java
strStream1.sorted().forEach(System.out::println);
int numOfStr = strStream1.count(); // 에러 스트림이 이미 닫혔음.
```
## 스트림은 작업을 내부 반복으로 처리한다.
스트림을 이용한 작업이 간결할 수 있는 비결중의 하나가 바로 '내부 반복'이다. 내부 반복이라는 것은 반복문을 메서드 내부에 숨길 수   
있다는 것을 의미한다. forEach()는 스트림에 정의된 메서드 중에 하나로 매개변수가 대입된 람다식을 데이터 소스의 모든 요소에 적용한다.
```java
for(String str : strList)
  System.out.println(str)
  
=>
  
stream.forEach(System.out::println);
```
## 스트림의 연산
스트림이 제공하는 다양한 연산을 이용해서 복잡한 작업들을 간단히 처리할 수 있다.   
마치 데이터베이스에 select문으로 질의 하는 것과 같은 느낌이다.   
   
스트림이 제공하는 연산은 중간연산과 최종연산으로 분류할 수 있는데, 중간 연산은 연산 결과를 스트림으로 반환하기 때문에 중간 연산을 연속해서   
연결할 수 있다. 반면에 최종 연산은 스트림의 요소를 소모하면서 연산을 수행하므로 단 한번만 연산이 가능하다.
> 중간연산 연산 결과가 스트림인 연산. 스트림에 연속해서 중간 연산을 할 수 있음
> 최종연산 연산 결과가 스트림이 아닌 연산. 스트림의 요소를 소모하므로 단 한번만 가능
```java
stream.distinct().limit(5).sorted().forEach(System.out::println);
//     중간연산   중간연산  중간연산  최종연산
```
모든 중간 연산의 결과는 스트림이지만 연산 전의 스트림과 같은 것은 아니다. 위의 문장과 달리 모든 스트림 연산을 나누어 쓰면 아래와 같다. 각 연산의
반환타입을 눈여겨보자.
```java
String[] strArr = {"dd","aaa","cc","CC","b"};
Stream<String> stream = stream.of(strArr); // 문자열 배열이 소스인 스트림
Stream<String> fiteredStream = stream.filter(); // 갈라내기(중간 연산)
Stream<String> distinctedStream = stream.distincct(); // 중복제거(중간 선언)
Stream<String> sortedStream = stream.sort(); // 정렬(중간선언)
Stream<String> limitedStream = stream.limit(5); // 스트링자르기 (중간 선언)
int total = stream.count(); // 요소 갯수 세기
```
출처 : [자바의 정석(남궁성)]
