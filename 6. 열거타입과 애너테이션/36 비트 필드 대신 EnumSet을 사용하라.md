# 36. 비트 필드 대신 EnumSet을 사용하라

Created: 2024년 1월 13일 오후 3:08
Tags: 열거타입과 애너테이션
다시 보면 좋음: No

- EnumSet
    - 열거한 값들이 단독이 아닌 집합으로 사용되는 경우 비트필드 대신 EnumSet을 사용하자
        - EnumSet.of()

```java
// EnumSet - a modern replacement for bit fields (Page 170)
public class Text {
    public enum Style {BOLD, ITALIC, UNDERLINE, STRIKETHROUGH}

    // Any Set could be passed in, but EnumSet is clearly best
    public void applyStyles(Set<Style> styles) {
        System.out.printf("Applying styles %s to text%n",
                Objects.requireNonNull(styles));
    }

    // Sample use
    public static void main(String[] args) {
        Text text = new Text();
        text.applyStyles(EnumSet.of(Style.BOLD, Style.ITALIC));
    }
}
```