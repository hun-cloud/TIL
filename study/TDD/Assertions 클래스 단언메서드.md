# Assertions 클래스 단언메서드

### 테스트 지정
메서드를 5가지 어노테이션으로 테스트를 지정할 수 있다.
|어노테이션|설명|
|-|-|
|@Test|테스트를 뜻한다.|
|@ParameterizedTest|매개변수화 된 테스트를 뜻한다.|
|@RepeatedTest|반복적인 테스트를 뜻한다.|
|@TestFactory|동적 테스트를 뜻한다.|
|@TestTemplate|테스트 케이스에 대한 템플릿을 뜻한다.|

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
