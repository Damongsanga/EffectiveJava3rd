# 14. Comparable을 구현할지 고민하라

Created: 2023년 12월 20일 오후 6:22
Tags: 모든 객체의 공통 메서드

## Comparable

### 정리

- 순서를 고려해야 하는 값 클래스를 작성한다면 꼭 Comparable 인터페이스를 구현하자
- compareTo 메서드에서 필드의 값을 비교할 때 <, > 연산자는 쓰지 말도록 하자.
- 또한 직접 값을 빼는 것도 그리 좋은 방법이 아니다 (오버플로우, 부동소수점 오류)
- 따라서 박싱된 기본타입 클래스가 제공하는 정적 compare 메서드나 Comparator 인터페이스가 제공하는 비교자 생성 메서드를 사용하자

### Comparable

- **equals와 같이 동치성 검사시 반사성, 대칭성, 추이성을 충족해야한다!**
- 마찬가지로 기존 클래스를 확장한 구체 확장 클래스에서 새로운 값 컴포넌트를 추가했다면 규약을 지킬 수 없다
    - 따라서 독립된 클래스를 만들고 이 클래스를 가리키는 필드를 추가하자.
    - 이후 이 내부 인스턴스를 반환하는 뷰 메서드를 제공하면 된다
- TreeSet 같은 경우는 equals 대신 compareTo를 사용한다
    - compareTo와 equals가 일관되지 않는 BigDecimal 클래스
        - new BigDecimal(”1.0”), new BigDecimal(”1.00”)은 equals가 false이지만 compareTo는 같은 원소로 취급한다
- compareTo 메서드 작성시 제네릭 인터페이스인 만큼 해당 클래스를 제네릭으로 사용해야 한다
    - Comparable<>은 컴파일타임에 메서드의 인수타입이 지정되기 때문

### Comparator(비교자)

- **Comparable을 구현하지 않는 필드나 표준이 아닌 순서로 비교할 시 사용**
- 핵심 필드 중 우선순위가 높은 순으로 먼저 비교
- **비교자 생성메서드** : 활용 예시
    - 매우 간결하고 심플하지만 조금의 성능저하가 있을 수 있다.
    - **comparingInt, comparingLong, comparingDouble :** int/long/double → Comparator
    - **thenComparing : Comparator → Comparator**
        1. 인수 0개 : 비교자 하나만 인수로 받아 그 비교자로 순서 지정
        2. 인수 1개 : 키 추출자를 인수로 받아 그 키의 자연적 순서로 보조 순서를 지정
        3. 인수 2개 : 키 추출자 하나와 추출된 키를 비교할 비교자까지 2개의 인수를 받음
    - **comparing**
        1. 키 추출자를 받아서 그 키의 자연적 순서 사용
        2. 키 추출자와 추출된 키를 비교할 비교자까지 2개의 인수를 받음

```java
import java.util.Comparator;

public class Test implements Comparable<Test>{
    
    private int i;
    private String s;
    private Double d;
   
    private static final Comparator<Test> COMPARATOR = 
            Comparator.comparingInt((Test mc) -> mc.i).
                    thenComparing(mc -> mc.s).
                    thenComparing(mc -> mc.d);

    @Override
    public int compareTo(Test o) {
        return COMPARATOR.compare(this, o);
    }
}
```

### Comparator 구현 시 추천되지 않는 방법 & 해결

- 알고리즘 풀 때 자주 사용되는 방법이나 이는 정수 오버플로우가 or 부동소수점 계산 방식에 따른 오류 발생할 수 있음

```java
static Comparator<Objects> hashCodeOrder = new Comparator<Objects>() {
    @Override
    public int compare(Objects o1, Objects o2) {
        return o1.hashCode() - o2.hashCode();
    }
};
```

1. **정적 compare 메서드를 활용한 비교자**

```java
static Comparator<Objects> hashCodeOrder = new Comparator<Objects>() {
    @Override
    public int compare(Objects o1, Objects o2) {
        return Integer.compare(o1.hashCode(), o2.hashCode());
    }
};
```

1. **비교자 생성 메서드를 활용한 비교자**

```java
static Comparator<Objects> hashCodeOrder = 
		Comparator.comparingInt(o -> o.hashCode());
};
```