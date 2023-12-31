# EffectiveJava3rd

#### 설명
1. 취지 : 자바에 대한 이해를 높이고 보다 객체지향적이며 유지보수하기 좋은 코드를 작성하기 위해
2. 계획 : 주 5회 아이템 1개씩 공부 
3. 기간 : 23.12월부터 시작하여 24.4월까지 마무리하는 것이 목표
4. 목표 : 프로젝트, 취준과 무관하게 꾸준하게 가져가면서 공부하고 실제 프로젝트에 적용해볼 수 있도록
5. 방법 : 교재 중심의 내용 정리 및 타 관련 자료 참고하여 공부
6. 교재 : EffectiveJava 3판

<hr>

### 2. 객체 생성과 파괴
[1. 생성자 대신 정적 팩토리 메소드를 사용해라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/2.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/1%20%EC%83%9D%EC%84%B1%EC%9E%90%20%EB%8C%80%EC%8B%A0%20%EC%A0%95%EC%A0%81%20%ED%8C%A9%ED%86%A0%EB%A6%AC%20%EB%A9%94%EC%86%8C%EB%93%9C.md)


[2. 매개변수가 많다면 빌더 패턴을 사용해라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/2.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/2%20%EB%A7%A4%EA%B0%9C%EB%B3%80%EC%88%98%EA%B0%80%20%EB%A7%8E%EB%8B%A4%EB%A9%B4%20%EB%B9%8C%EB%8D%94%20%ED%8C%A8%ED%84%B4.md)

[3. private 생성자나 열거 타입으로 싱글턴임을 보증하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/2.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/3%20private%20%EC%83%9D%EC%84%B1%EC%9E%90%EB%82%98%20%EC%97%B4%EA%B1%B0%20%ED%83%80%EC%9E%85%EC%9C%BC%EB%A1%9C%20%EC%8B%B1%EA%B8%80%ED%84%B4%EC%9E%84%EC%9D%84%20%EB%B3%B4%EC%9E%A5%ED%95%98%EB%9D%BC%204%20%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4%ED%99%94%EB%A5%BC%20%EB%A7%89%EC%9C%BC%EB%A0%A4%EB%A9%B4%20private%20%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC.md)

[4. 인스턴스화를 막으려거든 private 생성자를 사용하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/2.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/3%20private%20%EC%83%9D%EC%84%B1%EC%9E%90%EB%82%98%20%EC%97%B4%EA%B1%B0%20%ED%83%80%EC%9E%85%EC%9C%BC%EB%A1%9C%20%EC%8B%B1%EA%B8%80%ED%84%B4%EC%9E%84%EC%9D%84%20%EB%B3%B4%EC%9E%A5%ED%95%98%EB%9D%BC%204%20%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4%ED%99%94%EB%A5%BC%20%EB%A7%89%EC%9C%BC%EB%A0%A4%EB%A9%B4%20private%20%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC.md)

[5. 자원을 직접 사용하지 말고 의존 객체 주입을 사용해라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/2.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/5%20%EC%9E%90%EC%9B%90%EC%9D%84%20%EC%A7%81%EC%A0%91%20%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80%20%EB%A7%90%EA%B3%A0%20%EC%9D%98%EC%A1%B4%20%EA%B0%9D%EC%B2%B4%20%EC%A3%BC%EC%9E%85%EC%9D%84%20%EC%82%AC%EC%9A%A9.md)

[6. 불필요한 객체 생성을 피하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/2.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/6%20%EB%B6%88%ED%95%84%EC%9A%94%ED%95%9C%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EC%9D%84%20%ED%94%BC%ED%95%98%EB%9D%BC%2C%207%20%EB%8B%A4%20%EC%93%B4%20%EA%B0%9D%EC%B1%84%20%EC%B0%B8%EC%A1%B0%EB%A5%BC%20%ED%95%B4%EC%A0%9C%ED%95%98%EB%9D%BCmd.md)

[7. 다 쓴 객체 참조를 해제하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/2.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/6%20%EB%B6%88%ED%95%84%EC%9A%94%ED%95%9C%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EC%9D%84%20%ED%94%BC%ED%95%98%EB%9D%BC%2C%207%20%EB%8B%A4%20%EC%93%B4%20%EA%B0%9D%EC%B1%84%20%EC%B0%B8%EC%A1%B0%EB%A5%BC%20%ED%95%B4%EC%A0%9C%ED%95%98%EB%9D%BCmd.md)

[8.finalize와 cleaner 사용을 피해라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/2.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/8%20finalize%EC%99%80%20cleaner%20%EC%82%AC%EC%9A%A9%EC%9D%84%20%ED%94%BC%ED%95%B4%EB%9D%BC%209%20try-finally%20%EB%B3%B4%EB%8B%A4%EB%8A%94%20try-with-resources%EB%A5%BC%20%EC%82%AC%EC%9A%A9.md)

[9. try-finally보다는 try-with-resources를 사용하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/2.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/8%20finalize%EC%99%80%20cleaner%20%EC%82%AC%EC%9A%A9%EC%9D%84%20%ED%94%BC%ED%95%B4%EB%9D%BC%209%20try-finally%20%EB%B3%B4%EB%8B%A4%EB%8A%94%20try-with-resources%EB%A5%BC%20%EC%82%AC%EC%9A%A9.md)

<br>

### 3. 모든 객체의 공통 메서드
[10. equals는 일반 규칙을 지켜 재정의하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/3.%20%EB%AA%A8%EB%93%A0%20%EA%B0%9D%EC%B2%B4%EC%9D%98%20%EA%B3%B5%ED%86%B5%20%EB%A9%94%EC%84%9C%EB%93%9C/10%20equals%EB%8A%94%20%EC%9D%BC%EB%B0%98%20%EA%B7%9C%EC%B9%99%EC%9D%84%20%EC%A7%80%EC%BC%9C%20%EC%9E%AC%EC%A0%95%EC%9D%98%ED%95%98%EB%9D%BC.md)

[11. equals를 재정의하려거든 hashCode도 재정의하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/3.%20%EB%AA%A8%EB%93%A0%20%EA%B0%9D%EC%B2%B4%EC%9D%98%20%EA%B3%B5%ED%86%B5%20%EB%A9%94%EC%84%9C%EB%93%9C/11%20equals%EB%A5%BC%20%EC%9E%AC%EC%A0%95%EC%9D%98%ED%95%98%EB%A0%A4%EA%B1%B0%EB%93%A0%20hashCode%EB%8F%84%20%EC%9E%AC%EC%A0%95%EC%9D%98%ED%95%98%EB%9D%BC.md)

[12. toString을 항상 재정의하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/3.%20%EB%AA%A8%EB%93%A0%20%EA%B0%9D%EC%B2%B4%EC%9D%98%20%EA%B3%B5%ED%86%B5%20%EB%A9%94%EC%84%9C%EB%93%9C/12%20toString%EC%9D%84%20%ED%95%AD%EC%83%81%20%EC%9E%AC%EC%A0%95%EC%9D%98%ED%95%98%EB%9D%BC.md)

[14. Comparable을 구현할지 고민하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/3.%20%EB%AA%A8%EB%93%A0%20%EA%B0%9D%EC%B2%B4%EC%9D%98%20%EA%B3%B5%ED%86%B5%20%EB%A9%94%EC%84%9C%EB%93%9C/14%20Comparable%EC%9D%84%20%EA%B5%AC%ED%98%84%ED%95%A0%EC%A7%80%20%EA%B3%A0%EB%AF%BC%ED%95%98%EB%9D%BC.md)

<br>

### 4. 클래스와 인터페이스

[15. 클래스와 멤버의 접근 권한을 최소화하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/4.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4/15.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EB%A9%A4%EB%B2%84%EC%9D%98%20%EC%A0%91%EA%B7%BC%20%EA%B6%8C%ED%95%9C%EC%9D%84%20%EC%B5%9C%EC%86%8C%ED%99%94%ED%95%98%EB%9D%BC%2016.%20public%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%97%90%EC%84%9C%EB%8A%94%20public%20%ED%95%84%EB%93%9C%EA%B0%80%20%EC%95%84%EB%8B%8C%20getter%2C%20setter%20%EB%A9%94%EC%84%9C%EB%93%9C%EB%A5%BC%20%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC.md)


[16. public 클래스에서는 public 필드가 아닌 getter, setter 메서드를 사용하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/4.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4/15.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EB%A9%A4%EB%B2%84%EC%9D%98%20%EC%A0%91%EA%B7%BC%20%EA%B6%8C%ED%95%9C%EC%9D%84%20%EC%B5%9C%EC%86%8C%ED%99%94%ED%95%98%EB%9D%BC%2016.%20public%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%97%90%EC%84%9C%EB%8A%94%20public%20%ED%95%84%EB%93%9C%EA%B0%80%20%EC%95%84%EB%8B%8C%20getter%2C%20setter%20%EB%A9%94%EC%84%9C%EB%93%9C%EB%A5%BC%20%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC.md)

[17. 변경 가능성을 최소화하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/4.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4/17.%20%EB%B3%80%EA%B2%BD%20%EA%B0%80%EB%8A%A5%EC%84%B1%EC%9D%84%20%EC%B5%9C%EC%86%8C%ED%99%94%ED%95%98%EB%9D%BC.md)

[18. 상속보다는 컴포지션을 이용하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/4.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4/18%20%EC%83%81%EC%86%8D%EB%B3%B4%EB%8B%A4%EB%8A%94%20%EC%BB%B4%ED%8F%AC%EC%A7%80%EC%85%98%EC%9D%84%20%EC%9D%B4%EC%9A%A9%ED%95%98%EB%9D%BC.md)

[20. 추상 클래스보다는 인터페이스를 우선하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/4.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4/20%20%EC%B6%94%EC%83%81%20%ED%81%B4%EB%9E%98%EC%8A%A4%EB%B3%B4%EB%8B%A4%EB%8A%94%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%A5%BC%20%EC%9A%B0%EC%84%A0%ED%95%98%EB%9D%BC.md)

[21. 인터페이스는 구현하는 쪽을 생각해 설계하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/4.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4/21%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%8A%94%20%EA%B5%AC%ED%98%84%ED%95%98%EB%8A%94%20%EC%AA%BD%EC%9D%84%20%EC%83%9D%EA%B0%81%ED%95%B4%20%EC%84%A4%EA%B3%84%ED%95%98%EB%9D%BC.md)

[22. 인터페이스는 타입을 정의하는 용도로만 사용하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/4.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4/22%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4%EB%8A%94%20%ED%83%80%EC%9E%85%EC%9D%84%20%EC%A0%95%EC%9D%98%ED%95%98%EB%8A%94%20%EC%9A%A9%EB%8F%84%EB%A1%9C%EB%A7%8C%20%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC.md)

[23. 태그 달린 클래스 보다는 클래스 계층구조를 활용하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/4.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4/23%20%ED%83%9C%EA%B7%B8%20%EB%8B%AC%EB%A6%B0%20%ED%81%B4%EB%9E%98%EC%8A%A4%20%EB%B3%B4%EB%8B%A4%EB%8A%94%20%ED%81%B4%EB%9E%98%EC%8A%A4%20%EA%B3%84%EC%B8%B5%EA%B5%AC%EC%A1%B0%EB%A5%B4%201d504f892bd64edd930e3dc85bdfb7de.md)

[24. 멤버 클래스는 되도록 static으로 만들라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/4.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4/24%20%EB%A9%A4%EB%B2%84%20%ED%81%B4%EB%9E%98%EC%8A%A4%EB%8A%94%20%EB%90%98%EB%8F%84%EB%A1%9D%20static%EC%9C%BC%EB%A1%9C%20%EB%A7%8C%EB%93%A4%EB%9D%BC%20147813cc3a1d46e18bf7483b37565b59.md)

[25. 톱 레벨 클래스는 한 파일에 하나만 담으라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/4.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4/25%20%ED%86%B1%20%EB%A0%88%EB%B2%A8%20%ED%81%B4%EB%9E%98%EC%8A%A4%EB%8A%94%20%ED%95%9C%20%ED%8C%8C%EC%9D%BC%EC%97%90%20%ED%95%98%EB%82%98%EB%A7%8C%20%EB%8B%B4%EC%9C%BC%EB%9D%BC.md)

<br>

### 5. 제네릭

[26. 로 타입은 이용하지 말라 (+ 제네릭 전반)](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/5.%20%EC%A0%9C%EB%84%A4%EB%A6%AD/26%20%EB%A1%9C%20%ED%83%80%EC%9E%85%EC%9D%80%20%EC%9D%B4%EC%9A%A9%ED%95%98%EC%A7%80%20%EB%A7%90%EB%9D%BC%20(%2B%20%EC%A0%9C%EB%84%A4%EB%A6%AD%20%EC%A0%84%EB%B0%98).md)

[27. 비검사 경고를 제거하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/5.%20%EC%A0%9C%EB%84%A4%EB%A6%AD/27%20%EB%B9%84%EA%B2%80%EC%82%AC%20%EA%B2%BD%EA%B3%A0%EB%A5%BC%20%EC%A0%9C%EA%B1%B0%ED%95%98%EB%9D%BC.md)

[28. 배열보다는 리스트를 이용하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/5.%20%EC%A0%9C%EB%84%A4%EB%A6%AD/28%20%EB%B0%B0%EC%97%B4%EB%B3%B4%EB%8B%A4%EB%8A%94%20%EB%A6%AC%EC%8A%A4%ED%8A%B8%EB%A5%BC%20%EC%9D%B4%EC%9A%A9%ED%95%98%EB%9D%BC.md)

[29. 이왕이면 제네릭 타입으로 만들라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/5.%20%EC%A0%9C%EB%84%A4%EB%A6%AD/29%20%EC%9D%B4%EC%99%95%EC%9D%B4%EB%A9%B4%20%EC%A0%9C%EB%84%A4%EB%A6%AD%20%ED%83%80%EC%9E%85%EC%9C%BC%EB%A1%9C%20%EB%A7%8C%EB%93%A4%EB%9D%BC.md)
