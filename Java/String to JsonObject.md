# String -> JsonObject
Json문자열을 JsonObject로 바꾸는 방법
```java
String bodys = rest_response.getBody();

JsonParser jsonParser = new JsonParser();
Object obj = jsonParser.parse(bodys);
JsonObject jsonObj = (JsonObject) obj;
```










