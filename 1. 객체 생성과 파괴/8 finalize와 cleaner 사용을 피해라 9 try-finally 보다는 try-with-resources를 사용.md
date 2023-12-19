# 8. finalize와 cleaner 사용을 피해라 9. try-finally보다는 try-with-resources를 사용하라

Created: 2023년 12월 16일 오전 9:39
Tags: 객체 생성과 파괴

## 8. finalize와 cleaner 사용을 피해라

## 9. try-finally보다는 try-with-resources를 사용하라

- **try-finally**
    - close 해줘야 하는 자원을 사용할 때 finally에 반드시 close를 작성해야 하나 이는 매우 번거롭고 실수할 확률이 높다
    - 만약 이러한 자원을 2개이상 사용할 경우 코드가 매우 복잡해지며 심지어 finally 안에서도 예외가 발생할 수 있게 된다.

- **try-with-resources**
    - 자바 7부터 제공
    - **try (  ){    }**
    - 해당 자원이 **AutoClosable 인터페이스를 구현해야** 한다
    - 짧고 읽기 쉬우며 디버깅에 매우 용이
    - catch절 역시 사용할 수 있어 try 문을 중첩하지 않고 에러를 처리할 수 있다.

```java
static void copy(String src, String dst) throws IOException {
	try (InputStream in = new FileInputStream(src);
			OutputStream out = new FileOutputStream(dst)) {

		byte[] buf = new byte[BUFFER_SIZE];
		int n;
		while((n=in.read(buf) >= 0)
			out.write(buf, 0, n);
	}

}
```