# Spring의 핵심 가치 3가지
## 1. IoC / DI
- DI (Dependnecy Injection) 란
객체를 직접 생성하는 것이 아니라 외부에서 생성한 후 주입시켜주는 방식이다.
DI를 통해서 모듈 간의 결합도가 낮아지고 유연성이 높아진다.

- IoC (Inversion of Control)
제어의 역전 이라는 의미로 말 그대로 메소드나 객체의 호출작업을 개발자가 결정하는
것이 아니라, 외부에서 결정 되는 것을 의미한다.

스프링이 모든 의존성 객체를 스프링이 실행 될 때 다 만들어주고 필요한 곳에 주입시켜줌
으로써 Bean들은 싱글턴 패턴의 특징을 가지며 제어의 흐름을 사용자가 컨트롤 하는 것이
아니라 스프링에게 맡겨 작업 처리하게 된다.


## 2. AOP (Aspect Oriented Programming)
"관점지향 프로그래밍" 어떤 로직을 기준으로 핵심적인 관점, 부가적인 관점을
나누어서 보고 그 관점을 기준으로 각각 모듈화 하겠다는 것이다.
여기서 모듈화란 어떤 공통된 로직이나 기능을 하나의 단위로 묶는 것을 말한다.
Aspect로 모듈화하고 핵심적인 비지니스 로직에서 분리해서 재사용하겠다는 것이
AOP의 취지이다.




## 3. PSA (Portable Service Abstraction)

환경의 변화와 관계없이 일관된 방식의 기술로의 접근 환경을 제공하는 추상화 구조를 말한다.
이는 POJO 원칙을 철저히 따른 Spring의 기능으로 Spring에서 동작할 수 있는 Library들은
POJO 원칙을 지키게끔 PSA 형태의 추상화가 되어 있음을 의미한다.
   
즉 PSA = 잘 만든 인터페이스
PSA가 적용된 코드라면 나의 코드가 바뀌지 않고, 다른 기술로 간편하게 바꿀 수 있도록
확장성이 좋고, 기술테 특화되어 있지 않은 코드를 의미한다.
Spring -> Spring web MVC, Spring transaction, Spring Cache 등의 다양한 PSA를 제공한다.


## 그리고 POJO (Plain Old Java Object)
이상적으로, POJO는 자바 언어 사양 외에 어떠한 제한에도 묶이지 않은 자바 오브젝트
라고 할 수 있다.  
예를 들어, ORM(Object Relationship Mapping)이 새롭게 등장 했을 때,
ORM 기술을 사용하고 싶으면 ORM을 지원하는 ORM 프레임워크를 사용해야 한다.
자바 객체가 ORM 기술을 사용하기 위해 Hibernate 프레임워크를 직접 의존하는 순간
POJO라고 할 수 없다. 특정 기술에 종속되었기 때문이다.
   
하지만 Hibernate는 스프링 개발에서 많이 사용하고 있는 기술이다. 특정 기술에 종속적이면
POJO가 아니라면서 스프링에서 어떻게 가능한 걸까, 바로 스프링에서 정한 표준 인터페이스가
있기 때문이다. 스프링 개발자들은 ORM이라는 기술을 사용하기 위해서 JPA 라는 표준 인터페이스
아래, 구현되어 실행된다. 이것이 스프링이 엔터프라이즈 기술을 도입하면서도 POJO를
유지하는 방법이다. (그리고 이러한 방법을 스프링의 PSA라고 한다.)


참조   
[https://dev-coco.tistory.com/83](https://dev-coco.tistory.com/83)   
   
[https://siyoon210.tistory.com/120](https://siyoon210.tistory.com/120)
   
[https://velog.io/@gillog/Spring-DIDependency-Injection](https://velog.io/@gillog/Spring-DIDependency-Injection)
   
[https://engkimbs.tistory.com/746](https://engkimbs.tistory.com/746)
