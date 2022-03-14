# [JS] 구글로그인 API 구현하기
### 선행조건
> [https://console.cloud.google.com](https://console.cloud.google.com) 에 접속하여 새 프로젝트를 만들고 인증정보 설정하기


html 파일
```javascript
<html>
<head>
    <meta name="google-signin-client_id" content="클라이언트ID.apps.googleusercontent.com">
</head>
<body>

<div id="my-signin2"></div>
<script>
    function onSuccess(googleUser) {
      console.log('Logged in as: ' + googleUser.getBasicProfile().getName());
    }
    function onFailure(error) {
      console.log(error);
    }
    function renderButton() {
      gapi.signin2.render('my-signin2', {
        'scope': 'profile email',
        'width': 240,
        'height': 50,
        'longtitle': true,
        'theme': 'dark',
        'onsuccess': onSuccess,
        'onfailure': onFailure
      });
    }
  </script>

<script src="https://apis.google.com/js/platform.js?onload=renderButton" async defer></script>
</body>
</html>


```


