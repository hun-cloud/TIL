# Github로 Pull request 날리기

## 1. 깃 엑세스 토큰 발급 받기
[https://curryyou.tistory.com/344](https://curryyou.tistory.com/344)   
-> 해당 글을 참고하고 액세스 토큰을 비밀번호 입력할 때 사용한다.

## 2. 터미널에서 원하는 폴더에 repository를 클론하기
복사한 repository 주소는 터미널에서 원하는 폴더에 아래와 같이
입력해서 클론해준다.
```
git clone <복사한 레파지토리 주소>
```
## 3. remote url 추가
레파지토리를 클론하면, origin 이라는 이름으로 remote url이 설정 되어 있다.
만약에 포크한 레파지토리가 아닌 원본 리파지토리를 클론한 거라면 이미 remote가
되어있기 때문에 remote url을 또 추가해줄 필요가 없다. 하지만 포크를 했다면,
원본 레파지토리에 코드를 푸쉬하기 위해 remote url을 추가해줘야 한다.
- remote url 설정 상태 확인
```
git remote -v
```
```
git remote add <remote url 이름> <remote url>
```

## 4. Branch 생성
```
git branch <branch 이름>
```
- branch list 확인
```
git branch
```

## 5. branch 이동
- branch를 이동할 수 있다.
```
git checkout <branch 이름>
```

## 6. 코드 수정
- 소스를 수정, 추가 한 후 add, commit, push   

- add
```
git add .           // 수정된 모든 파일을 add 하겠다.
git add <파일 이름> // 몇 개의 파일만 add 하겠다. 
```
- commit
```
git commit -m "메시지 입력"
```
- push
```
git push origin <branch 이름>
```

## 7. pull request 날리기
- push를 하고 나서 github에 해당 레파지토리에 들어가면 pullrequest 버튼이
활성화 되어있다. "Compare & Pull request" 버튼을 클릭해 준다.

## 8. pull request 작성하기
- 메세지를 작성 후 "create pull request" 버튼을 클릭해주면 끝!














