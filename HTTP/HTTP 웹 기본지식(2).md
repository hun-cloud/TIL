# HTTP 웹 기본지식(2)
## URI, URL, URN
URI는 로케이터(locator), 이름(name) 또는 둘 다 추가로 분류될 수 있다.   
URI안에 URL과 URN이 있다.

## URI
* Uniform : 리소스 식별하는 통일된 방식
* Resource : 자원, URI로 식별할 수 있는 모든 것(제한 없음)
* Identifier : 다른 항목과 구분하는데 필요한 정보

* URL : Uniform Resource Locator : 리소스가 있는 위치를 지정
* URN : Uniform Resource Name : 리소스에 이름을 부여
* URI와 URL은 같은 의미로 생각하면 된다.

## URL
* scheme://[userInfo@]host[:port][/path][?query][#fragment]
* https://www.google.com:443/search?q=hello&hl=ko   
   
* 프로토콜(https)
* 호스트(www.google.com)
* 포트 번호(443)
* 패스(/search)
* 쿼리 파라미터(q=hello&hl=ko)

참조 : [인프런] 모든 개발자를 위한 HTTP 웹 기본 (김영한)
