# [spring boot] Docker Hub에 간단하게 이미지 올리는 방법

프로젝트를 jar 파일로 생성해야 한다.   
방법 =>
[프로젝트 jar 파일 생성](https://github.com/JaeHunJaeHun/shortCoding/blob/main/study/springBoot/%5BSpring%20boot%5D%20%ED%94%84%EB%A1%9C%EC%A0%9D%ED%8A%B8%20jar%ED%8C%8C%EC%9D%BC%20%EC%83%9D%EC%84%B1.md)   

## Dockerfile 생성
프로젝트 루트 폴더에 생성한다.
```
FROM openjdk:17
ARG JAR_FILE=build/libs/*.jar
COPY ${JAR_FILE} app.jar
ENTRYPOINT ["java", "-jar", "/app.jar"]
```

## Dockerfile.bat 생성
Docker Hub에 올리기 쉽게 같은 폴더에 bat 파일을 생성한다.
```
docker build -t rabbitmq-receiver .
docker tag rabbitmq-receiver jhl9838/rabbitmq-receiver:dev
docker push jhl9838/rabbitmq-receiver:dev
```

그리고 PC에 깔아둔 Docker desktop을 실행시키고 bat 파일을 실행시킨다. 끝😁😁😁
