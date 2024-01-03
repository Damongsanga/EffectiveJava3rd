# 31. 한정적 와일드카드를 사용해 API 유연성을 높이라

Created: 2024년 1월 3일 오후 11:05
Tags: 제네릭
다시 보면 좋음: Yes

### 한정적 와일드카드

- 매개변수화 타입은 **불공변** ⇒ 매개변수의 상/하위 타입 관계와 무관하게 서로 상/하위 타입 관계가 아니다
    - 상위 클래스에서 정상 작동시 하위 클래스에서도 정상 작동해야 한다는 리스코프 치환 원칙에 어긋남
- 한정적 와일드카드를 사용하여 유연성 증가!
- <Number> ⇒ <? extends Number>
    - Integer와 같은 하위 타입도 가능
- <Number> ⇒ <? super Number>
    - Object와 같은 상위 타입도 가능

### PECS (Get and Put Principle) ⇒ 중요!!

- **producer-extends, consumer-super**
- 생산자는 <? extends T>
- 소비자는 <? super T>
- **Producer-Consumer Pattern**
    - 작업물을 가운데 위치시키고 작업을 생성 / 처리로 분리하는 설꼐방법
    - 작업을 생성하고 처리하는 부분이 각각 비동기적으로 처리하여 부하를 조절
    - 대표적인 예시 : MQ(Message Queue), MVVM
- 주의
    - 반환타입에는 한정적 와일드카드를 사용하지 마라
    - 입력 매개변수가 생산자와 소비자의 역활을 동시에 한다면 와일드카드 사용의 의미가 없어진다
    - Java 8 부터 아래 코드가 정상적으로 컴파일될 것이다
        - Java 7 까지는 타입 추론 능력이 부족하여 명시적 타입 인수를 추가해야한다
        
        ```java
        public static <E> Set<E> union(Set<? extends E> s1, Set<? extends E> s2) {...}
        
        Set<Integer> integers = Set.of(1,3,5);
        Set<Double> doubles = Set.of(2.0, 4.0, 6.0);
        Set<Number> numbers = union(integers, doubles);
        ```
        

- 어려운 예시
    
    ```java
    // 수정 전
    public static <E extends Comparable<E>> E max(List<E> list)
    
    // 수정 후
    public static <E extends Comparable<? super E>> E max(List<? extends E> list)
    ```
    
    - 매개변수
        - producer니까 extends
    - 타입변수 E
        - Comparable<E>는 E를 소비
        - **Comparable은 항상 소비자임으로 Comparable<E> 보다는 Comparable<? super E>가 좋다**
    

### 비한정적 타입매개변수 vs 비한정적 와일드카드

```java
public static <E> void swap(List<E> list, int i, int j); // 1.
public static void swap(List<?> list, int i, int j); // 2.
```

- 기본 규칙 : 메서드 선언에 타입 매개변수가 한 번만 나오면 와일드카드로 대체하라
- 그러나 이 방법에는 이러한 문제가 있다
    
    ```java
    public static void swap(List<?> list, int i, int j){
    	list.set(i, list.set(j, list.get(i)));
    }
    ```
    
    - List<?>에는 null 외에는 어떠한 값도 넣을 수 없다
    - **와일드카드**(**`?`**)를 사용한 리스트는 원소의 타입을 알 수 없기 때문에 컴파일러는 **원소를 추가하거나 가져오는 작업을 허용하지 않음**
    - 도우미 메소드를 사용해야 하는데 이 방법은 결국 첫번째 방법과 동일하게 생겼다
    
    ```java
    public static void swap(List<?> list, int i, int j){
    	swapHelper(list, i, j);
    }
    
    public static <E> void swapHelper(List<E> list, int i, int j){
    	list.set(i, list.set(j, list.get(i)));
    }
    ```