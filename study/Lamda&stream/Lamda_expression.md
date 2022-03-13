## 람다식
> 람다식의 도입으로 인해 자바는 객체지향언어인 동시에 함수형 언어가 되었다. 
> 이 변화를 잘 받아들이기만 한다면 람다식이라는 더 강력한 무기를 얻게 될 것이다.

## 람다식이란?
> -	람다식은 간단히 말해서 메서드를 하나의 식으로 표시한 것이다. 람다식은 함수를 간략하면서도 명확한 식으로 표현할 수 있게 해준다.
> -	메서드를 람다식으로 표현하면 메서드의 이름과 반환값이 없으므로 람다식을 익명 함수(anonymous function)이라고도 한다.

```java
int[] arr = new int[5];
Arrays.parallelSetAll(arr,(i) -> (int)Math.random()*5+1);

//(i) -> (int)Math.random()*5+1 이 부분이 람다식!! 아래 메서드와 동일한 역할을 한다.
public int method() {
	return (int) Math.random()*5 + 1;
}
```
## 람다식의 장점
> - 메서드보다 람다식이 간결하면서도 이해하기 쉽다는 것에 이견이 없을 것이다.
> 게다가 모든 메서드는 클래스에 포함되어야 하므로 클래스도 새로 만들어야 하고 객체도 생성해야한
> 이 메서드를 호출할 수 있다. 그러나 람다식은 이 모든 과정없이 오직 람다식 자체만으로도 이 메서드의 역할을 대신 할 수 있다.
> - 게다가 람다식은 메서드의 매개변수로 전달되어지는 것이 가능하고, 메서드의 결과로 반환될 수 있다. 람다식으로 인해 메서드를
> 변수처럼 다루는 것이 가능해진 것이다.

## 람다식 작성하기
> 람다식은 '익명 함수'답게 메서드에서 이름과 반환타입을 제거하고 매개변수 선언부와 몸통 {} 사이에 '->'를 추간한다.
```java
반환타입 메서드이름(매개변수 선언){
  문장들
}  
=>
  
  (매개변수 선언) -> {}

```
예시
> - 반환값이 있는 메서드의 경우, return 문 대신 식으로 대신할 수 있다. 식의 연산결과가 자동으로 반환값이 된다.
> 이때는 문장이 아닌 식이므로 끝에 ; 를 붙히지 않는다. 
> - 람다식에 선언된 매개변수의 타입은 추론이 가능한 경우는 생략할 수 있는데, 대부분의 경우에 생략이 가능하다.
> 람다식에 반환타입이 없는 이유도 항상 추론이 가능하기 때문이다.
```java
int max(int a, int b) {
	return a > b? a : b;
}
=>
(a,b) -> a > b? a: b
```

아래와 같이 선언된 매개변수가 하나뿐인 경우에는 괄호()를 생략할 수 있다.
단, 매개변수의 타입이 있으면 괄호()를 생략할 수 없다.
```java
(a) 0 -> a * a      =>      a -> a * a //OK
(int a) -> a * a    =>      int a -> a * a //에러
```

마찬가지로 괄호{} 안의 문장이 하나일 경우 괄호{}를 생략할 수 있다. 이 때 문장의 끝에는 ';'을
붙이지 않아야 한다는 것을 주의하자.
```java
(String name, int i ) -> {System.out.println(name + "=" + i);}
=>
(String name, int i) -> System.out.println(name + "=" + i)
```
* 그러나 괄호{} 안의 문장이 return 문일 경우 괄호 {}를 생략할 수 없다.
```java
(int a, int b) -> { return a > b ? a : b;} // ok
(int a, int b) ->  return a > b ? a : b // error
```
예제
```java
int max(int a, int b){ return a > b ? a : b;}
=>
(a,b) -> a > b ? a : b

void printVar(String name, int i){
	System.out.println(name + "=" + i);
}
=>
(name, i) -> System.out.println(name + "=" + i)

int square(int x){
	return x * x;
}
=>
x -> x * x

int roll(){ return (int) (Math.random() * 6);}
=>
() -> (int) (Math.random() * 6)

int sumArr(int[] arr){
	int sum = 0;
	for(int i : arr)
		sum+=i;
	return sum;
}
=>
(int[] arr) -> {
	int sum = 0;
	for(int i : arr)
		sum+=i;
	return sum;
} 

```


출처 : Java의 정석 (3rd Edition) 남궁 성 지음





