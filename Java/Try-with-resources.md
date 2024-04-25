# Try-with-resources

리소스 작업을 포함하는 애들의 예외 처리를 도와준다. 자바 1.7 부터 사용 가능   
기존 try-catch의 문제점
```java
public class TryCatchResources {

	public static void main(String[] args) {
		FileWriter f = null;

		try {
			f = new FileWriter("data.txt");
			f.write("hello");
		} catch (IOException e) {

			e.printStackTrace();
		} finally {

			if(f != null) {
				try {					
					f.close();
				} catch (Exception e) {
					e.printStackTrace();
				}
			}
		}
	}
}
```
1. 코드가 너무 더럽고 길다.
2. 닫아주는 구문을 여러 곳에서 사용해야 하는 경우가 있다.

### 그래서 그 문제점을 해결한 try-with-resources 문 !!

```java
public class TryCatchResources {

	public static void main(String[] args) {
		
		try(FileWriter f = new FileWriter("data.txt")){			
			f.write("hello");
			//f.close(); 필요 없다 
		}catch(Exception e) {
			e.printStackTrace();
		}		
	}
}
```
> 너무 깔끔한 코드가 되었다.
> 보기에도 좋다.

[출처] 생활코딩 youtube [https://www.youtube.com/watch?v=fYHsOyvnzAs](https://www.youtube.com/watch?v=fYHsOyvnzAs)


