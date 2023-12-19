# 11. equals를 재정의하려거든 hashCode도 재정의하라

Created: 2023년 12월 19일 오후 1:29
Tags: 모든 객체의 공통 메서드

### Object 명세서

1. hashcode는 equals 비교에 사용되는 정보가 바뀌지 않는 한 “어플리케이션 실행동안” 일관되게 같은 값을 반환해야 함.
2. equals가 true라면 (같은 객체라면) 반드시 같은 hashcode를 반환해야
3. equals가 false여도 (다른 객체라면) 다른 hashcode일 필요가 없다. 그러나 객체별로 hashcode가 겹치지 않아야 해시테이블의 성능이 좋아진다.

- **만약 모든 객체에 같은 hashcode를 부여한다면?**
    - 해시충돌 상승
    - HashMap은 LinkedList처럼 동작할 것임

### 1. 좋은 Hashcode 구현

- 이상적인 해시 함수는 주어진 서로 다른 인스턴스들을 32 비트 정수 범위에 균일하게 분배해야 함
- **주의할 것은 equals 비교에 사용되지 않을 필드는 반드시 제외해야함**

1. **int 변수 result를 선언 후 첫 필드의 해시코드 값으로 초기화**
2. **각 변수의 해시코드를 계산**
    - 기본타입 필드 : Type.hashcode() (박싱 클래스)
    
    ```java
    Integer.hashcode();
    ```
    
    - 참조타입 필드 : 해당 필드의 hashcode를 재귀적으로 호출
        - 만약 재귀 호출이 복잡한데 값이 반복적이라면 필드의 표준형을 만드는 것도 좋은 방법이다
        - 필드의 값이 null이면 0을 사용한다 (다른 상수도 가능하나 관습적)
    - 배열 필드 : 핵심 원소가 없다면 0, 모두라면 Arrays.hashcode(), 일부만 있다면 각각 계산하여 3번 방식으로 더해줌
        
        ```java
        Arrays.hashcode();
        ```
        
3. **기존 result에 31을 곱하고 더해줌**
    
    ```java
    result = 31 * result + c;
    ```
    
- **예시**

```java
private short s;
private int i;
private String str;
private int id; // equals의 해당 없음 (포함 X)

@Override public int hashCode() {
	int result = Short.hashcode(s);
	result = result * 31 + Integer.hashcode(i);
	result = result * 31 + str.hashcode();
	return result;
}
```

### 2. Objects.hash()

- 위 내용을 매우 간결하게 구현할 수 있음
- 입력 인수를 담기위한 배열 생성 & 박싱과 언박싱 과정 필요
- **성능에 민감하지 않은 상황에서만 사용**

```java
@Override public int hashCode() {
	return Objects.hash(s,i,str);
}
```

### 3. Lazy Initializtion

- 클래스 불변이면서 해시코드 계산 비용이 크다면 캐싱하는 방법을 사용해야
- hashcode가 처음 불릴 때까지 계산을 늦추는 방법
- 여기서 초기값 (0)은 평소 해시값으로 나올 수 없는 값이어야 한다

```java
private int hashCode;

@Override public int hashCode() {
	int retuls = hashCode;
	
	if(result = 0) {
		result = Short.hashcode(s);
		result = result * 31 + Integer.hashcode(i);
		result = result * 31 + str.hashcode();
		hashCode = result;
	}

	return result;
}
```

### 4. 기타

- 성능을 위해 핵심필드를 생략하게 되면 해시 충돌이 급격하게 늘어날 수 있음으로 그러지 말자!
    - 예시로 자바 2에서는 String을 16개만의 문자로 해시코드를 검사 ⇒ 문자열 길이 늘어나면 성능에 큰 악영향
- hashOcde 반환 값의 생성규칙을 API 사용자들에게 자세히 알려주면 안된다.

### **Why does Java's hashCode() in String use 31 as a multiplier?**

```java
s[0]*31^(n-1) + s[1]*31^(n-2) + ... + s[n-1]
```

- 곱셈을 사용하지 않으면 아나그램의 해시코드와 같아짐
    - 아나그램 : 구성하는 철자가 같고 순서만 다른 문자열
- 31을 사용하는 이유는 소수이기 때문
    - 만약 이 숫자가 짝수이고 오버플로우가 발생하면 정보를 잃게됨
    - 시프트 연산과 같은 결과를 나타내기 때문 (?) 이거는 틀린 설명 같기도 함
    - 소수를 곱하는 이유는 명확하지는 않으나 전통적으로 그랬다고 함
        - 이라고 되어있는데 직관적으로만 봐도 소수를 쓰는 것이 충돌될 확률이 낮아보임

[https://stackoverflow.com/questions/299304/why-does-javas-hashcode-in-string-use-31-as-a-multiplier](https://stackoverflow.com/questions/299304/why-does-javas-hashcode-in-string-use-31-as-a-multiplier)