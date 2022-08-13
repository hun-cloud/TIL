# package와 import
## 패키지
패키지란, 클래스의 묶음이다. 패키지에는 클래스 또는 인터페이스를 포함시킬 수 있으며, 서로 관련된 클래스들끼리 그룹 단위로 묶어 놓음으로써
클래스를 효율적으로 관리할 수 있다. 같은 이름의 클래스일지라도 다른 패키지에 존재하는 것이 가능하므로, 자신만의 패키지 체계를 유지함으로써
다른 개발자가 개발한 클래스 라이브러리의 클래스와 이름이 충돌하는 것을 피할 수 있다.   
클래스가 물리적으로 하나의 클래스파일(.class)파일 인 것과 같이 패키지는 물리적으로 하나의 디렉토리이다.

- 하나의 소스파일에는 첫 번째 문장으로 단 한 번의 패키지 선언만을 허용한다.
- 모든 클래스는 반드시 하나의 패키지에 속해야 한다.
- 패키지는 점(.)을 구분자로 하여 계층구조로 구성할 수 있다.
- 패키지는 물리적으로 클래스 파일(.class)를 포한하는 하나의 디렉토리이다.

## 패키지 선언
```java
package 패키지명;

package com.test.test;

class PackageTest {
    
}
```

## import 문
모든 소스파일(.java)에서 import문은 package문 다음에, 그리고 클래스 선언문 이전에 위치해야한다.   
import문은 package문과 달리 소스파일에 여러 번 선언할 수 있다.   
같은 패키지에서 여러 개의 클래스가 사용될 때, import문을 여러번 사용하는 대신 '패키지명.*'을 이용해서
지정된 패키지에 속하는 모든 클래스를 패키지명 없이 사용할 수 있다.   
   
컴파일러는 해당 패키지에서 일치하는 클래스이름을 찾아야하는 수고를 더 해야한다. 실행시 성능상의 차이는 전혀 없다.
```java
import java.util.Calendar;
import java.util.Date;
import java.util.ArrayList;

import java.util.*;
```
지금까지 System과 String 같은 java.lang패키지의 클래스들을 패키지명 없이 사용할 수 있었던
이유는 모든 소스파일에는 묵시적으로 다음과 같은 import문이 선언되어 있기 때문이다.
```java
import java.lang.*;
```
java.lang 패키지는 매우 빈번하게 사용되는 중요한 클래스들이 속한 패키지이기 때문에 따로 import문으로 지정하지 않아도 되는 것이다.

## static import문
static import문을 사용하면 static 멤버를 호출할 때 클래스 이름을 생략할 수 있다. 특정 클래스의 static멤버를 자주사용할 때 편리하다.
코드도 간결해진다.
```java
import static java.lang.Math.random;

Math.random();
->
random(();
```





