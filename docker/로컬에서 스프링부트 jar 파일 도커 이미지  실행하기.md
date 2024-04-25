# 로컬에서 스프링부트 jar 파일 도커 이미지 생성, 실행하기

## 1. 도커 설치하기
[https://www.lainyzine.com/ko/article/a-complete-guide-to-how-to-install-docker-desktop-on-windows-10/](https://www.lainyzine.com/ko/article/a-complete-guide-to-how-to-install-docker-desktop-on-windows-10/)   
-> 해당 사이트에서 WSL2 설치, 활성화, 도커 설치를 친절하게 알려주고 있다 참조하자

## 2. 스프링부트 .jar 파일 만들기
[스프링부트 jar 파일 생성방법](https://github.com/JaeHunJaeHun/shortCoding/blob/main/study/springBoot/%5BSpring%20boot%5D%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20jar%ED%8C%8C%EC%9D%BC%20%EC%83%9D%EC%84%B1.md)
-> 해당 글을 보고 jar 파일을 생성하면 된다.

## 3. Dockerfile 작성
-> 사용자가 이미지를 생성할 때 사용해야할 모든 커맨드라인을 담고 있는 일종의 매뉴얼과 같은 텍스트 문서이다. Doker은 Dockerfile의 설명을 읽고 자동으로 이미지를 빌드할 수 있다.   
   Dockerfile은 위치는 bin이 있는 디렉토리에 생성을 한다.
```
FROM openjdk:8-jdk-alpine
ARG JAR_FILE=build/libs/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java","-jar","/app.jar"]
```
- FROM : 이미지를 생성할 때 사용할 기반 이미지이다. openjdk:8-jdk-alpine 이미지에서 레이어를 생성한다.
- ARG : 변수 선언
- COPY : 실행할 jar 파일을 도커 컨테이너 내부에 app.jar라는 이름으로 복사한다. 상대경로로 위치도 같이 설정 가능하다.
- ENTRYPOINT : 컨테이너가 시작될 때 실행할 스크립트 혹은 명령을 정의한다.

## 4. Image Build
(윈도우 기준) 
1. PowerShell을 열고 docker file가 있는 디렉토리로 이동
```
docker build -t admin .
```
- -t    : 특정 이름으로 이미지를 빌드한다는 의미를 가진 옵션
- admin : .jar을 제외한 파일의 이름이다. jar파일이 대문자면 실행되지 않는다.
- .     : Dockerfile의 경로를 나타낸다. 

## 5. 도커 이미지 확인
```
docker images
```
해당 명령어로 생성한 이미지를 조회한다. 존재할 경우 이미지 생성에 성공.

## 6. 컨테이너 실행
```
docker run -it -p 8081:8080 --name test admin
```
- -p 8081:8080 : 호스트 포트를 노출된 컨테이너 포트에 명시적으로 매핑하는 옵션, 로컬의 8081 포트와 컨테이너의 8080 포트를 매핑한다.

### 중지
```
ctrl + c 를 눌러 중지 할 수 있다.
```

## 필요한 명령어
1. 조회
```
docker ps -a
```
2. 정지
``` 
docker stop container-id
```
3. 시작
```
docker start container-id
```
4. 재시작
```
docker restart container-id
```
5. 접속
```
docker attach container-id
```



## 8. 중지된 컨테이너 제거
- 컨테이너가 종료되도 여전히 도커 시스템에 존재한다. 명령어를 사용해서 중지된 컨테이너를 제거할 수 있다.
```
docker container prune
```




### 참조
[window 10] Docker 설치 완벽 가이드   
-> [https://www.lainyzine.com/ko/article/a-complete-guide-to-how-to-install-docker-desktop-on-windows-10/](https://www.lainyzine.com/ko/article/a-complete-guide-to-how-to-install-docker-desktop-on-windows-10/)


로컬에서 Docker 이미지 생성 및 웹 페이지 띄우기   
-> [https://may9noy.tistory.com/530](https://may9noy.tistory.com/530)
   
도커 명령어   
-> [https://leannet.tistory.com/90](https://leannet.tistory.com/90)


