# 35. ordinal 메서드 대신 인스턴스 필드를 사용하라

Created: 2024년 1월 13일 오후 3:07
Tags: 열거타입과 애너테이션
다시 보면 좋음: No

> *대부분의 프로그래머는 이 메서드를 쓸 일이 없다. 이 메서드는 enumSet, enumMap같이 열거 타입 기반의 범용 자료구조에 쓸 목적으로 설계되었다.*
> 

**ordinal()** 

- enum의 순서 반환 메서드
- **상수 선언 순서 바꾸는 간 오작동**
- 중간에 값을 비워둘 수도 없어 dummy 값을 사용해야함
- **인스턴스 필드에 저장하자**

```java
public enum Ensemble {
    SOLO(1), DUET(2), TRIO(3), QUARTET(4), QUINTET(5),
    SEXTET(6), SEPTET(7), OCTET(8), DOUBLE_QUARTET(8),
    NONET(9), DECTET(10), TRIPLE_QUARTET(12);

    private final int numberOfMusicians;
    Ensemble(int size) { this.numberOfMusicians = size; }
    public int numberOfMusicians() { return numberOfMusicians; }
}
```