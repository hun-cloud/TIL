아래 명령어로 docker에 rabbitmq 설치 및 실행

```
docker run -d --name rabbitmq -p 5672:5672 -p 8080:15672 --restart=unless-stopped rabbitmq:management
```
docker 옵션 정보

```
-d : 백그라운드로 실행
--name rabbitmq : 해당 컨테이너 이름을 rabbitmq로 실행
-p 5672:5672 -p 15672:15672 : HOST와 컨테이너간 포트 포워딩 (5672: rabbitmq 기본통신포트, 15672: rabbitmq-server의 통신포트 (이외에 클러스터 구성이 필요하다면 25672도 필요))
--restart=unless-stopped : 해당 컨테이너를 사용자가 멈추기 전까지 계속 재부팅

rabbitmq:management : rabbitmq이미지 중 management기능이 있는 rabbitmq-server까지 포함된 이미지를 실행
```

참조 [https://musclebear.tistory.com/139](https://musclebear.tistory.com/139)
