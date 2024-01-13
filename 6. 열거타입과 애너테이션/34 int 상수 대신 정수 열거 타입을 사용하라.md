# 34. int 상수 대신 정수 열거 타입을 사용하라

Created: 2024년 1월 9일 오후 8:21
Tags: 열거타입과 애너테이션
다시 보면 좋음: Yes

- 다시보면 좋을 부분
    - **전략 열거 타입**

- 정수 열거 패턴
    - 타입 안전을 보장할 수도 없고 표현력도 좋지 않다
    - 상수의 값이 바뀌면 클라이언트도 반드시 다시 컴파일 해야 한다

### Enum

- 특징
    - C, C++ 등과 달리 완전한 형태의 클래스로 다른 언어의 열거타입보다 강력
    - **public 외부 생성자 제공 X, 사실상 final**
        - public으로 제공하면 에러 발생
        - 인스턴스 통제되며 싱글턴을 일반화한 형태라고 할 수 있다
    - **타입 안정성을 보장**
    - **열거 타입에 정의된 상수의 개수는 영원고정불변일 필요가 없다**
        - **열거타입에 새로운 상수를 추가/삭제하더라도 새로 컴파일하지 않아도 됨!**
        - 삭제된 상수 참조시 컴파일오류 with 디버깅 메시지!
    - toString의 보다 정확한 표현 가능
    - 필드와 메소드 추가 가능
        - Object 메서드
        - **열거타입은 모두 불변임으로 필드들은 final인 것이 좋음**
        - 메소드는 이유가 있다면 package-private(default)로, 아니면 private로 선언
    - 임의의 인터페이스 구현 가능
        - Comparable
        - Serializable

- 왜 좋은가?
    - 상수 수정에 따른 클라이언트 재 컴파일 불필요
    - enum 사용하여 if문 사용 자제 가능

- 언제 써야 하는가?
    - **필요한 원소를 런타임이 아닌 컴파일타임에 다 알 수 있는 상수 집합이라면 항상 열거타입을 사용하자**
    - 체스 말 종류, 요일, 행성, 메뉴 아이템, 명령줄 플래그 등

- 예시

```java
public enum Planet {
    MERCURY(3.302e+23, 2.439e6),
    VENUS  (4.869e+24, 6.052e6),
    EARTH  (5.975e+24, 6.378e6),
    MARS   (6.419e+23, 3.393e6),
    JUPITER(1.899e+27, 7.149e7),
    SATURN (5.685e+26, 6.027e7),
    URANUS (8.683e+25, 2.556e7),
    NEPTUNE(1.024e+26, 2.477e7);

    private final double mass;           // In kilograms
    private final double radius;         // In meters
    private final double surfaceGravity; // In m / s^2

    // Universal gravitational constant in m^3 / kg s^2
    private static final double G = 6.67300E-11;

    // Constructor
    Planet(double mass, double radius) {
        this.mass = mass;
        this.radius = radius;
        surfaceGravity = G * mass / (radius * radius);
    }

    public double mass()           { return mass; }
    public double radius()         { return radius; }
    public double surfaceGravity() { return surfaceGravity; }

    public double surfaceWeight(double mass) {
        return mass * surfaceGravity;  // F = ma
    }
}
```

- 활용
    - 해당 soutf 대신 toString을 재정의해도 좋다!

```java
public class WeightTable {
   public static void main(String[] args) {
      double earthWeight = Double.parseDouble(args[0]);
      double mass = earthWeight / Planet.EARTH.surfaceGravity();
      for (Planet p : Planet.values())
         System.out.printf("Weight on %s is %f%n",
                 p, p.surfaceWeight(mass));
   }
}
```

- **주요 메서드 (자동 생성됨)**
    - **values() : 열거된 모든 원소를 배열에 담아 순서대로 리턴**
    - **ordinal() : 원소에 열거된 “순서”를 정수값으로 리턴**
    - **valueOf() : 매개변수로 주어진 String과 열거형에서 일치하는 이름을 갖는 원소를 리턴**

```java
enum DevType {
	APPLE, BANANA, KIWI
}

System.out.println(DevType.values().get(0)); // APPLE
System.out.println(DevType.BANANA.ordinal()); // 1
System.out.println(DevType.valueOf("KIWI")); // KIWI

```

- 특정 클래스에서만 사용되면 해당 클래스의 멤버 클래스 (inner class)로 만들어라

- 상수 별로 다른 동작을 하는 Enum을 만들어보자
    - **좋지 않은 예시 (switch)**
        
        ```java
        public enum Operation{
        	PLUS, MINUS, TIMES, DIVIDE;
        
        	public double apply(double x, double y){
        		switch(this) {
        			case PLUS: return x+y;
        			case MINUS: return x-y;
        			case TIMES: return x*y;
        			case DIVIDE: return x/y;
        		}
        		throw new AssertionError("알 수 없는 연산: "+this);
        	}
        }
        ```
        
        - 상수 추가시 case 문 수정해야
        - throw도 상수가 삭제될 것을 대비해서 동작하지도 않을 코드를 만들어두어야 함
        
    - **좋은 예시**
        
        ```java
        public enum Operation {
            PLUS("+") {
                public double apply(double x, double y) { return x + y; }
            },
            MINUS("-") {
                public double apply(double x, double y) { return x - y; }
            },
            TIMES("*") {
                public double apply(double x, double y) { return x * y; }
            },
            DIVIDE("/") {
                public double apply(double x, double y) { return x / y; }
            };
        
            private final String symbol;
        
            Operation(String symbol) { this.symbol = symbol; }
        
            @Override public String toString() { return symbol; }
        
            public abstract double apply(double x, double y);
        }
        ```
        
        - symbol을 추가하였고 상수별 apply 메소드를 재정의함
        - apply 메소드를 추상 메소드로 정의하여 재정의하는 것을 깜빡하지 않도록함 (컴파일 에러 발생하도록)
        
        - **valueOf(String)을 사용한 fromString 제공**
        
        ```java
        // Implementing a fromString method on an enum type (Page 164)
            private static final Map<String, Operation> stringToEnum =
                    Stream.of(values()).collect(
                            toMap(Object::toString, e -> e));
        
            // Returns Operation for string, if any
            public static Optional<Operation> fromString(String symbol) {
                return Optional.ofNullable(stringToEnum.get(symbol));
            }
        ```
        
        - Optional을 반환하는 이유
            - 주어진 문자열이 가리키는 연산이 존재하지 않을 수 있음을 클라이언트에게 알림
            - 이 상황을 대처하도록 유도
        
        - **switch 문을 사용하기 좋은 경우**
            - 기존 열거 타입에 상수별 동작을 서로 혼합해 넣을 때는 좋다
            - 예시로 아래는 각 연산의 반대 연산을 반환하는 메서드
        
        ```java
        public static Operation inverse(Operation op) {
                switch(op) {
                    case PLUS:   return Operation.MINUS;
                    case MINUS:  return Operation.PLUS;
                    case TIMES:  return Operation.DIVIDE;
                    case DIVIDE: return Operation.TIMES;
        
                    default:  throw new AssertionError("Unknown op: " + op);
                }
            }
        ```
        

### 전략 열거 타입

- enum inside enum
- 열거타입 내 상수들에 대해 다른 메소드로 분기해야 할 때
- **열거 타입 내 전략용 열거타입**을 가져감으로서 쉽게 분기 (enum PayType)

```java
enum PayrollDay {
    MONDAY(WEEKDAY), TUESDAY(WEEKDAY), WEDNESDAY(WEEKDAY),
    THURSDAY(WEEKDAY), FRIDAY(WEEKDAY),
    SATURDAY(WEEKEND), SUNDAY(WEEKEND);

    private final PayType payType;

    PayrollDay(PayType payType) { this.payType = payType; }

    int pay(int minutesWorked, int payRate) {
        return payType.pay(minutesWorked, payRate);
    }

    // The strategy enum type
    enum PayType {
        WEEKDAY {
            int overtimePay(int minsWorked, int payRate) {
                return minsWorked <= MINS_PER_SHIFT ? 0 :
                        (minsWorked - MINS_PER_SHIFT) * payRate / 2;
            }
        },
        WEEKEND {
            int overtimePay(int minsWorked, int payRate) {
                return minsWorked * payRate / 2;
            }
        };

        abstract int overtimePay(int mins, int payRate);
        private static final int MINS_PER_SHIFT = 8 * 60;

        int pay(int minsWorked, int payRate) {
            int basePay = minsWorked * payRate;
            return basePay + overtimePay(minsWorked, payRate);
        }
    }

    public static void main(String[] args) {
        for (PayrollDay day : values())
            System.out.printf("%-10s%d%n", day, day.pay(8 * 60, 1));
    }
}
```