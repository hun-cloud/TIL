# Cmd 창에서 원하는 포트 죽이기
#### 기존에는 이러한 방법을 많이 썼다.
1. netstat -a -o
2. 원하는 포트의 pid를 찾기
3. taskkill /f /pid pid번호
#### 내 방법
1. netstat -aon | findStr "8080
2. taskkill /f /pid pid번호   

### 훨씬 빠르고 편하다👍👍👍👍
