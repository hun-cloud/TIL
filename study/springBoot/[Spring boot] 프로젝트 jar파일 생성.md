# [Spring boot] 프로젝트 jar파일 생성
스프링 부트는 was 를 가지고 있기 때문에 war 파일이 아닌 jar 파일로 생성하여 실행이 가능하다.

### 생성 후 실행 방법
1. cmd 창을 열고 해당 프로젝트의 위치로 이동한다.
```
cd C:\Users\software\git\siteadmin_server\SiteAdmin
```
2. 해당 명령어를 수행한다. (빌드)
```
gradlew bootJar
```
3. jar 파일이 있는 곳으로 이동
```
cd build/libs
```
4. jar 파일이 있는 위치로 가서 해당 명령어를 수행 (실행)
```
java -jar 해당파일이름.jar
```
