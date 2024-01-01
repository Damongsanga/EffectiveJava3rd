# 10. equals는 일반 규칙을 지켜 재정의하라

Created: 2023년 12월 17일 오후 10:44
Tags: 모든 객체의 공통 메서드

## 10. equals는 일반 규칙을 지켜 재정의하라

- equals는 함부로 재정의하는것은 좋지 않다
- 다음 아래에 해당한다면 equals는 재정의하지 말자
    1. 각 인스턴스가 본질적으로 고유한 경우
        - Thread
    2. 인스턴스의 논리적 동치성을 검사할 일이 없는 경우
        - Pattern
    3. 상위클래스에서 재정의한 equals가 하위 클래스에서 들어맞는 경우
        - AbstractSet → Set
        - AbstractList → List
        - AbstractMap → Map
    4. 클래스가 private이거나 private-package라 equals를 쓸 일이 없는 경우

- 언제 재정의하는가?
    - 객체 식별성이 아닌 논리적 동치성을 따져야하는데 상위 클래스의 equals가 이를 재정의하지 않은 경우
        - 값 클래스 (Integer, String) 등
            - 객체가 같은지가 아니라 값이 같은지 비교하고 싶을 것임으로!
        - 그러나 값 클래스라고 해도 값이 같은 인스턴스가 2개 이상 생성되지 않음을 보장한다면 재정의 X
            - 대표적인 예로 Enum

- equals 메서드 재정의시 반드시 일반 규약을 따라야 함

## **동치관계를 구현해야하며 다음을 만족해야한다**

- 동치관계 : 집합을 서로 같은 원소들로 이워진 부분집합으로 나누는 연산
1. **반사성 : null X라면 x.equals(x)는 true다**
2. **대칭성 : null X이고 x.equals(y)가 true라면 y.equals(x)도 true다**
3. **추이성 : null X라면  x.equals(y)가 true고 y.equals(z)도 true라면 z.equals(x)도 true다**
4. **일관성 : null X라면 반복해서 호출한다고 true false가 변환되지 않는다.**
5. **null-아님 : null X라면 x.equals(null)은 false다**

1. **대칭성**
    - 아래 코드를 보면 CaseInstensiveString의 equals는 String을 알지만 String의 equals는 CaseInstensiveString를 알지 못한다는 문제..!
    
    ```java
    public final class CaseInstensiveString {
    	private final String s;
    	public CaseInstensiveString(String s) {
    		this.s = Object.requiredNonNull(s);
    	}
    
    	// 잘못된 코드
    	@Override
    	public boolean equals(Object o){
    		if (o instanceof String){
    			return s.equslIgnoreCase((String) o);		
    		return fasle;
    	}
     
    	// 수정코드 (String의 s 활용)
    	@Override
    	public boolean equals(Object o){
    		return o instanceof CaseIntensiveString 
    				&& ((CaseIntensiveString) o).s.equalsIgnoreCase(s);
    	}
    }
    ```
    
    ```java
    CaseIntensiveString cis = new CaseInstensiveString("Hello");
    String s = "Hello";
    ```
    

1. **추이성**
    - 상위 클래스에 없는 새로운 필드를 하위 클래스에 추가하는 상황을 생각하면 쉽다.
    - **만약 하위 클래스의 equals를 super.equals를 사용하고 추가된 필드에 대해서만 추가 검사를 한다면 안된다 ⇒ 대칭성 위배**
        - A : a, b
        - B : a, b, c
    - **그러면 상/하위 클래스 관계인 경우에는 추가된 필드 비교를 무시하면 되는가? ⇒ 추이성 위배**
        - A : a, b, c
        - B : a, b
        - C : a, b, d
        - A - B : true, B - C : true,  C - A : false가 나와버림
    - **객체지향의 장점을 유지하면서 구체 클래스를 확장해 새로운 값을 추가하면서 equals 규약을 만족시킬 방법은 존재하지 않는다.**
    - 추상 클래스의 하위클래스라면 equals 규약을 지킬 수 있다
        - 상위 클래스 객체를 만들 수 자체가 없기 때문이다!
    
    - **리스코프 치환 원칙**
        - 어떤 타입에 있어 중요한 속성이라면 그 하위 타입에서도 중요해야 한다
        - **즉, 그 타입의 모든 메서드가 하위타입에서도 똑같이 잘 작동해야 한다**
        - 아래 예시에서는 Point의 하위 타입에서는 정상적으로 작동하지 않을 것이다.
        
        ```java
        // 원칙 위배
        @Override
        public boolean equals(Object o) {
        	if (o == null || o.getClass() != getClass())
        		return false;
        	Point p = (Point) o;
        	return p.x == x && p.y == y;
        }
        ```
        
    
    - 이러한 실수가 java 라이브러리 내에도 있다
        - java.sql.TimeStamp가 java.util.Date를 확장함
        - 이 둘은 섞어 쓰지 말자
    
    - 좋은 우회 방법으로 상속대신 **컴포지션을** 사용하는 방법이 있다. (아이템 18)
        - **상위 클래스를 상속받는 대신, 상위 클래스를 private 필드로 두고 이를 반환하는 뷰메서드를 public으로 추가하는 방식**
    
    1. **일관성**
    - 객체가 수정되지 않는 한 앞으로도 영원히 같아야 한다
    - 불변 객체라면 더더욱 그렇다
        - 같다면 영원히 같고, 다르다면 영원히 다르다고 해야 한다
    - 불변 가변 상관 없이 equals의 판단에 신뢰할 수 없는 자원이 있으면 안된다.
        - 예시로 j**ava.net.URL**의 equals는 URL과 매핑된 IP로 비교를 하는데 이는 결과를 보장할 수 없다 (실수임으로 따라하지 말 것)
    
    1. null-아님
    - 모든 객체가 null과 같으면 안된다
    
    ```java
    // 명시적 null 검사 - 불필요!
    if (o==null) return false; 
    
    // 묵시적 null 검사 - 좋은 코드이다
    if (!(o instanceof MyType)) return false; 
    MyType mt = (MyType) o; 
    ...
    ```
    
    - instanceof는 첫 피연산자가 null이면 무조건 false를 던진다 (명시적 null 검사 불필요)
    
    ### **(중요) 좋은** equals 구현 메서드 단계
    
    1. **== 연산자를 사용해 입력이 자기자신의 참조인지 확인**
        - 자기자신이면 true 반환
        - 성능 최적화 용
    2. **instanceof 연산자로 입력이 올바른 타입인지 확인**
        - 그렇지 않다면 false 반환
        - 여기서 타입은 equals가 구현된 클래스인 경우가 대부분이나 이 클래스가 구현한 **인터페이스가 될 수 있다**
        - 대표적인 예시로 List, Set 등이 있다
    3. **입력을 올바른 형태로 형변환한다**
        - instanceof 검사를 했음으로 100% 성공
    4. **입력 객체와 자기 자신의 대응되는 ‘핵심’ 필드들이 모두 일치하는지 하나씩 검사**
        - 하나라도 다르면 false 반환
        - 2번에서 인터페이스를 사용했다면 입력된 필드 값을 가져올 때도 인터페이스의 메소드를 사용해야!
    
    - 기본형
        - float, double은 정적 메서드인 Float.compare, [Double.compare](http://Double.compare) 로 비교 (부동 소수점)
        - 이외 모두 == 비교
    - 참조형
        - equals 비교
    

### 구현 후 확인하자

1. 대칭적인가?
2. 추이성이 있는가?
3. 일관적인가?

### 마지막으로 주의할 점

- 바로 뒤에 나오지만 equals 정의 시 hashcode도 반드시 재정의하자
- 너무 복잡하게 해결하지 말자. 동치성만 검사해도 괜찮다
- **Object 외의 타입을 매개변수로 받는 메서드를 선언하지 말자. 이는 재정의(@Override)가 아니다**
    
    ```java
    // 안됨!! 반드시 Object
    public boolean equals(MyClass o) {
    // ...
    }
    ```
    
- 구글에서 나온 AutoValue 라이브러리를 추천