# Jnit5 문법 정리

# Method Annotations

### 테스트 지정
메서드를 5가지 어노테이션으로 테스트를 지정할 수 있다.
|어노테이션|설명|
|-|-|
|@Test|테스트를 뜻한다.|
|@ParameterizedTest|매개변수화 된 테스트를 뜻한다.|
|@RepeatedTest|반복적인 테스트를 뜻한다.|
|@TestFactory|동적 테스트를 뜻한다.|
|@TestTemplate|테스트 케이스에 대한 템플릿을 뜻한다.|

### 라이프 사이클
테스트 실행 전 & 후에 실행할 메서드를 지정할 수 있다.
|어노테이션|설명|
|-|-|
|@BeforeAll|현재 클래스의 모든 테스트가 실행되기 전에 한번 실행된다.|
|@BeforeEach|각각 테스트가 실행 전에 실행된다.|
|@AfterEach|각각 테스트가 실행 후에 실행한다.|
|@AfterAll|현재 클래스의 모든 테스트가 실행된 후에 한번 실행된다.|

### 시간 제한
테스트 & 라이프사이클 어노테이션에 같이 사용된다.
|어노테이션|설명|
|-|-|
|@Timeout|지정된 제한 시간을 초과하면 실패처리한다.|

### 실행 순서
테스트 실행 순서를 지정한다.
|어노테이션|설명|
|-|-|
|@Order|테스트 메서드의 실행 순서를 지정한다.|

# Class Annotations
### 인스턴스 전략
인스턴스 생성 전략을 지정한다.
|어노테이션|설명|
|-|-|
|@TestInstance|현재 클래스의 모든 테스트가 실행되기 전에 한번 실행된다.|

### 실행 순서
|어노테이션|설명|
|-|-|
|@TestMethodOrder|테스트 클래스의 실행 순서를 지정한다.|

### 이름 표기
|어노테이션|설명|
|-|-|
|@DisplayNameGeneration|테스트 이름을 표기하는 방법을 설정한다.|

### non-static
|어노테이션|설명|
|-|-|
|@Nested|해당 클래스가 non-static 내부 클래스임을 나타낸다. @Before, @AfterAll을 사용할 수 없다.|

### 확장
|어노테이션|설명|
|-|-|
|@ExtendWith|확장자를 선언적인 등록에 사용된다.|
|@RegisterExtension|프로그래밍으로 확장자를 등록하는데 사용한다.|

# Class & Method Annotations
### 필터
|어노테이션|설명|
|-|-|
|@Tag|테스트 그룹을 만들고 원하는 그룹만 테스트할 수 있다.|

### 이름 표시
|어노테이션|설명|
|-|-|
|@DisplayName|클래스명 & 메서드명 대신 노출한 이름을 지정한다.|

### 비활성화
|어노테이션|설명|
|-|-|
|Disabled|지정한 클래스, 메서드를 실행하지 않는다.|

# Parameter Annotations

### 임시 디렉토리
테스트 & 라이프사이클 어노테이션에 같이 사용된다.
|어노테이션|설명|
|-|-|
|@TempDir|필드 및 파라미터 주입을 통해 임시 디렉토리로 사용된다.|

# 매개변수 테스트를 도와주는 Annotations
### ParameterizedTest를 사용하다보면 다양한 인자값이 필요한데, 이를 지원해주는 어노테이션이다.
|어노테이션|설명|
|-|-|
|@ValueSource|지정된 타입 & 배열 값을 넘겨준다.|
|@NullSource|Null 값을 넘겨준다.|
|@EmptySource|비어있는 값을 넘겨준다.|
|@NullAndEmptySource|Null과 비어있는 값을 넘겨준다.|
|@EnumSource|지정된 Enum을 넘겨준다.|
|@MethodSource|지정된 메서드의 반환값을 넘겨준다.|
|@CvsSource|문자열로 이뤄진 배열 값을 넘긴다. 각 문자열은 특정 구분자로 분리되어 여러 타입으로 넘어온다.|
|@CvsFileSource|지정된 경로의 csv 파일을 읽어 값을 넘긴다.|
|@ArgumentSource|커스텀 데이터 값을 주입한다.|


### Assertions 클래스가 제공하는 주요 단언 메서드
|메서드|설명|
|----------------|-------------|
|assertEquals(expected, actual)|실제값(actual)이 기대하는 값(expected)과 같은지 검사한다.|
|assertNotEquals(unexpected, actual)|실제값(actual)이 특정값(unexpected)과 같은지 검사한다.|
|assertSame(Object expected, Object actual)|두 객체가 동일한 객체인지 검사한다.|
|assertNotSame(Object unexpected,Object actual)|두 객체가 동일하지 않은 객체인지 검사한다.|
|assertTrue(boolean condition)|값이 true인지 검사한다.|
|assertFalse(boolean condition)|값이 false인지 검사한다.|
|assertNull(Object actual)|값이 null인지 검사한다.|
|assertNotNull(Object actual)|값이 null이 아닌지 검사한다.|
|fail()|테스트를 실패 처리한다.|



참고 블로그
[https://loopstudy.tistory.com/279?category=1003677](https://loopstudy.tistory.com/279?category=1003677)
