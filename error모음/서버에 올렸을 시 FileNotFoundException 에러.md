# FildNotFound Exception 
기존 코드

```java
String fileName = "src/main/resources/credentialJson/credential.json";
InputStream in = new FileInputStream(fileName);
```

로컬에서는 잘 실행되었지만 실제 운영 서버에 올리니 FileNotFoundException이 발생하였다.   
java.io가 현재 작업 디렉토리에 의존하기 떄문이다.
## 해결방법

```java
String fileName = "credentialJson/credential.json";
InputStream in = getClass().getClassLoader().getResourceAsStream(fileName);
```
