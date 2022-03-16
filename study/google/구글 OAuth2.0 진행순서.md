# 구글 OAuth2.0 진행순서
Resource Owner : 사용자   
Client : 서비스 제공사 (웹사이트)
Resource Server : 구글   
   
1. 사용자가 서비스 제공사에 접속   
2. 구글 로그인 버튼을 누르면 "https://resource.server/?client_id=1&scope=B,C&redirect_uri=https://client/callback" 주소로 이동(구글)
3. 구글은 사용자가 로그인이 되어있는지 확인하고 안되어 있으면 로그인을 진행하도록 한다.
4. 로그인을 성공하게 된다면 서비스 제공사 아이디값(client_id)이 유효한지 확인   
   유효하지 않다면 작업을 끝마친다.
5. 유효하다면 서비스 제공사가 원하는 사용자 정보를 제공할 것인지 사용자에게 물어봄
6. 허용 시 해당 정보(userId:1, scope: b,c)를 가지고 구글로 이동 구글은 해당 정보를 저장
7. accessToken을 발급 하기 전 사용자에게 Authorization code : 3 을 전달   
   Location:https://client/callback=3 이라는 주소로 이동시키게 함
8. 사용자도 모르게 https://client?/callback?code=3 으로 이동
9. 서비스 제공사는 authorization code : 3을 알게됨
10. 서비스 제공사는 구글에게 “https://resourve.server/token?grant_type=authorization_code&code=3&redirect_uri=https://client/callback&client_id&client_secret=2” 를 요청
11. 맞다면 구글은 accessToken을 서비스제공사에게 제공, 서비스 제공사는 DB or 파일에 저장, 서비스 제공사가 구글에게 accessToken을 가지고 구글에게 요청 시 어느 사용자의 어느 정보를
    제공해줄 것인지 결정할 수 있다.








