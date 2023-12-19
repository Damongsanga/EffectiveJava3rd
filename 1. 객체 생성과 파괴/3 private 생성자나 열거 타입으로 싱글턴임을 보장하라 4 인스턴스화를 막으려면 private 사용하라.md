# 3. private 생성자나 열거 타입으로 싱글턴임을 보증하라, 4. 인스턴스화를 막으려거든 private 생성자를 사용하라

Created: 2023년 12월 13일 오전 10:32
Tags: 객체 생성과 파괴

## 3. private 생성자나 열거 타입으로 싱글턴임을 보증하라

- 싱글턴의 단점
    - 이를 사용하는 클라이언트를 테스트하기 어려움
    - 인터페이스를 구현한 싱글턴이 아니라면 mock(가짜) 구현으로 대체할 수 없기 때문

### **싱글턴 생성 방법**

1. **private 생성자 + public static final 멤버**
    - 장점
        - 누가봐도 싱글턴 & 간결함!
    - 공격 방법 : 권한이 있는 클라이언트의 리블렉션 API  ⇒ private 생성자 호출 가능
    
    ```java
    AccessibleObject.setAccessible
    ```
    
    - 방어 방법 : 생성자 수정하여 두번째 객체 생성시 예외 던지도록 변경
2. 정적 팩토리 메소드
    - 가장 많이 쓰고 간편한 방법 (내가 주로 하던 방법)
    - getInstance()는 항상 같은 객체 참조를 반환함으로 제 2의 객체가 생기지 않는다
    - 장점
        1. 추후에 API 변경 없이 싱글턴이 아니게 변경할 수 있음
            - 팩토리 메소드 (getInstnace()) 를 유일 객체가 아닌 새 객체를 넘겨주도록만 수정하면 됨
        2. 정적 팩터리를 제네릭 싱글턴 팩토리로 변경 쉬움
        3. 정적 팩터리의 메서드 참조를 supplier로 사용 가능
            
            ```java
            Elvis::getInstnace  =>  Supplier<Elvis>
            ```
            

- **1.2 번 방법의 단점**
    1. **자원 낭비 : Static 필드는 클래스 로딩 시간에 초기화되므로 런타임에 해당 클래스를 사용하지 않아도 싱글톤 인스턴스가 생성** 
    2. private 생성자 만들어야함 : 기본 생성자가 생성되는 걸 피하기 위해 코드 블럭에서 하는 일이 없어도 private 생성자를 만들어야 한다
    3. **직렬화 : Serializable 을 구현하더라도 readResolve 메서드 제공해야 가짜 객체 생성 안됨 (아니면 역직렬화시 가짜 객체 생성)**
        
        ```java
        private Object readResolve(){
        	return INSTANCE;
        }
        ```
        
    4. 리플렉션 : 리플렉션시 런타임에 private 생성자 접근 가능
        - 리플렉션이란?
            
            구체적인 클래스 타입을 알지 못하더라도 그 클래스의 메서드, 타입, 변수들에 접근할 수 있도록 해주는 자바 API
            
            💡컴파일 시간이 아닌 실행 시간에 동적으로 특정 클래스의 정보를 추출할 수 있는 프로그래밍 기법
            

1. Enum
    
    ```java
    public enum SingletonEnum {
        INSTANCE;
        int value
    }
    
    public class Test {
        public static void main(String[] args) {
            SingletonEnum singleton = SingletonEnum.INSTANCE;
        }
    }
    ```
    
    - 1번 경우와 비슷하지만 더 간결하고 추가 노력 없이 직렬화 가능
    - 복잡한 직렬화 상황이나 리플렉션 공격에서 제 2의 인스턴스 생성 막아줌
        - enum 타입은 기본적으로 직렬화 가능하므로 Serializable 인터페이스를 구현할 필요가 없고, 리플렉션 문제도 발생하지 않는다.
    - 이펙티브 자바에서는 이 방법을 제일 추천함
        - 인스턴스가 JVM 내에 하나만 존재한다는 것이 100% 보장
    - 단점
        - 만들려는 싱글턴이 다른 클래스를 상속해야한다면 불가능 (중복 상속 X)
    
- 참고

[[Java] Enum과 싱글톤(Singleton)](https://scshim.tistory.com/361)

## 4. 인스턴스화를 막으려거든 private 생성자를 사용하라

- 인스턴스화 방지가 필요한 경우
    1. 정적메소드와 필드만을 담은 클래스가 필요한 경우
        - 예시 : java.lang.Math, java.util.Arrays
    2. 특정 인터페이스를 구현하는 객체를 생성해주는 정적메소드만 담은 클래스가 필요한 경우
        - java 8 이후로는 인터페이스에 정적메소드를 넣을 수 있게 되었다는 것을 참고
        - 예시 : java.util.Collection**s**
    3. final 클래스에 관한 메소드를 모아둘 클래스가 필요한 경우
        - final 클래스를 상속해서 하위 클래스에 메서드를 넣는 것이 불가능하기 때문
        - 따라서 final 클래스의 메소드는 오버라이딩 불가
        - gpt 설명 (예시)
            
            SomeFinalClass 클래스의 메소드를 사용할 FinalClassHelper 클래스
            
            **나 : 그러니까 final 클래스의 메소드를 오버라이드하지 않되 그런 식으로 사용하려고 쓰는건가?**
            
            GPT : 맞습니다. final 클래스는 더 이상 상속이 불가능한 클래스이기 때문에 하위 클래스에서 메소드를 오버라이딩할 수 없습니다. 그러나 final 클래스의 기능을 활용하고자 할 때, 해당 클래스의 메소드를 직접적으로 사용하거나, 필요한 경우 유틸리티 클래스와 같은 도구 클래스를 만들어서 해당 클래스와 관련된 유용한 메소드를 모아둘 수 있습니다.
            
            이렇게 함으로써 final 클래스의 안정성을 유지하면서도 해당 클래스의 기능을 활용할 수 있습니다. 이러한 유틸리티 클래스는 final 클래스에 종속된 기능을 담당하며, final 클래스의 메소드를 그대로 사용하는 형태로 설계될 수 있습니다.
            
            ```java
            public final class SomeFinalClass {
                public void finalMethod() {
                    // final 메소드의 구현...
                }
            }
            ```
            
            ```java
            public class FinalClassHelper {
                public static void someMethodForFinalClass(SomeFinalClass obj) {
                    obj.finalMethod(); // SomeFinalClass의 finalMethod 호출
                    // 다른 로직 수행...
                }
            }
            ```
            

- 추상 클래스는 인스턴스화를 막을 수 없다
    - 하위 클래스로 만들면 되니까
    - 게다가 사용자는 당연히 상속/구현하여 인스턴스해야 한다고 생각할 수 있다
    - **컴파일러는 생성자가 없으면 기본 private 생성자를 자동으로 생성한다는 문제도 존재**
    
- 이를 방지하기 위해 private 생성자를 추가하여 클래스의 인스턴스화 방지
    - 컴파일러는 이미 생성자가 있음으로 추가 생성자를 만들지 않는다
    - 에러를 던지고 주석을 달아놓으면 좋다
    
    ```java
    // 기본 생성자가 만들어지는 것을 방지
    private UtilClass(){
    	throw new AssertionError();
    }
    ```
    

- 위 방법은 상속을 불가능하게 하기도 한다
    - 상속시 명시/묵시적으로 상위 클래스의 생성자를 호출 ( super( ) )
    - 이를 막아버림!