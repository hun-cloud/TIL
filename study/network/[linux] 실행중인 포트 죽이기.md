실행중인 포트 확인
```
netstat -nap | grep :8080
```

해당 프로세스 죽이기
```
fuser -k -n tcp 8080
```
