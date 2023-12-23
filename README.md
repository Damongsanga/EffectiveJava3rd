# EffectiveJava3rd

#### 설명
1. 취지 : 자바에 대한 이해를 높이고 보다 객체지향적이며 유지보수하기 좋은 코드를 작성하기 위해
2. 계획 : 주 5회 아이템 1개씩 공부 
3. 기간 : 23.12월부터 시작하여 24.4월까지 마무리하는 것이 목표
4. 목표 : 프로젝트, 취준과 무관하게 꾸준하게 가져가면서 공부하고 실제 프로젝트에 적용해볼 수 있도록
5. 방법 : 교재 중심의 내용 정리 및 타 관련 자료 참고하여 공부
6. 교재 : EffectiveJava 3판

<hr>

### 1. 객체 생성과 파괴
[1. 생성자 대신 정적 팩토리 메소드를 사용해라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/1.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/1%20%EC%83%9D%EC%84%B1%EC%9E%90%20%EB%8C%80%EC%8B%A0%20%EC%A0%95%EC%A0%81%20%ED%8C%A9%ED%86%A0%EB%A6%AC%20%EB%A9%94%EC%86%8C%EB%93%9C.md#%EC%A0%95%EC%A0%81-%ED%8C%A9%ED%86%A0%EB%A6%AC-%EB%A9%94%EC%84%9C%EB%93%9C)

[2. 매개변수가 많다면 빌더 패턴을 사용해라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/1.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/2%20%EB%A7%A4%EA%B0%9C%EB%B3%80%EC%88%98%EA%B0%80%20%EB%A7%8E%EB%8B%A4%EB%A9%B4%20%EB%B9%8C%EB%8D%94%20%ED%8C%A8%ED%84%B4.md)

[3. private 생성자나 열거 타입으로 싱글턴임을 보증하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/1.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/3%20private%20%EC%83%9D%EC%84%B1%EC%9E%90%EB%82%98%20%EC%97%B4%EA%B1%B0%20%ED%83%80%EC%9E%85%EC%9C%BC%EB%A1%9C%20%EC%8B%B1%EA%B8%80%ED%84%B4%EC%9E%84%EC%9D%84%20%EB%B3%B4%EC%9E%A5%ED%95%98%EB%9D%BC%204%20%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4%ED%99%94%EB%A5%BC%20%EB%A7%89%EC%9C%BC%EB%A0%A4%EB%A9%B4%20private%20%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC.md#3-private-%EC%83%9D%EC%84%B1%EC%9E%90%EB%82%98-%EC%97%B4%EA%B1%B0-%ED%83%80%EC%9E%85%EC%9C%BC%EB%A1%9C-%EC%8B%B1%EA%B8%80%ED%84%B4%EC%9E%84%EC%9D%84-%EB%B3%B4%EC%A6%9D%ED%95%98%EB%9D%BC)

[4. 인스턴스화를 막으려거든 private 생성자를 사용하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/1.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/3%20private%20%EC%83%9D%EC%84%B1%EC%9E%90%EB%82%98%20%EC%97%B4%EA%B1%B0%20%ED%83%80%EC%9E%85%EC%9C%BC%EB%A1%9C%20%EC%8B%B1%EA%B8%80%ED%84%B4%EC%9E%84%EC%9D%84%20%EB%B3%B4%EC%9E%A5%ED%95%98%EB%9D%BC%204%20%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4%ED%99%94%EB%A5%BC%20%EB%A7%89%EC%9C%BC%EB%A0%A4%EB%A9%B4%20private%20%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC.md#4-%EC%9D%B8%EC%8A%A4%ED%84%B4%EC%8A%A4%ED%99%94%EB%A5%BC-%EB%A7%89%EC%9C%BC%EB%A0%A4%EA%B1%B0%EB%93%A0-private-%EC%83%9D%EC%84%B1%EC%9E%90%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC)

[5. 자원을 직접 사용하지 말고 의존 객체 주입을 사용해라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/1.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/5%20%EC%9E%90%EC%9B%90%EC%9D%84%20%EC%A7%81%EC%A0%91%20%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80%20%EB%A7%90%EA%B3%A0%20%EC%9D%98%EC%A1%B4%20%EA%B0%9D%EC%B2%B4%20%EC%A3%BC%EC%9E%85%EC%9D%84%20%EC%82%AC%EC%9A%A9.md#5-%EC%9E%90%EC%9B%90%EC%9D%84-%EC%A7%81%EC%A0%91-%EC%82%AC%EC%9A%A9%ED%95%98%EC%A7%80-%EB%A7%90%EA%B3%A0-%EC%9D%98%EC%A1%B4-%EA%B0%9D%EC%B2%B4-%EC%A3%BC%EC%9E%85%EC%9D%84-%EC%82%AC%EC%9A%A9%ED%95%B4%EB%9D%BC-1)

[6. 불필요한 객체 생성을 피하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/1.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/6%20%EB%B6%88%ED%95%84%EC%9A%94%ED%95%9C%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EC%9D%84%20%ED%94%BC%ED%95%98%EB%9D%BC%2C%207%20%EB%8B%A4%20%EC%93%B4%20%EA%B0%9D%EC%B1%84%20%EC%B0%B8%EC%A1%B0%EB%A5%BC%20%ED%95%B4%EC%A0%9C%ED%95%98%EB%9D%BCmd.md#6-%EB%B6%88%ED%95%84%EC%9A%94%ED%95%9C-%EA%B0%9D%EC%B2%B4-%EC%83%9D%EC%84%B1%EC%9D%84-%ED%94%BC%ED%95%98%EB%9D%BC)

[7. 다 쓴 객체 참조를 해제하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/1.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/6%20%EB%B6%88%ED%95%84%EC%9A%94%ED%95%9C%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EC%9D%84%20%ED%94%BC%ED%95%98%EB%9D%BC%2C%207%20%EB%8B%A4%20%EC%93%B4%20%EA%B0%9D%EC%B1%84%20%EC%B0%B8%EC%A1%B0%EB%A5%BC%20%ED%95%B4%EC%A0%9C%ED%95%98%EB%9D%BCmd.md#6-%EB%B6%88%ED%95%84%EC%9A%94%ED%95%9C-%EA%B0%9D%EC%B2%B4-%EC%83%9D%EC%84%B1%EC%9D%84-%ED%94%BC%ED%95%98%EB%9D%BC)

[8.finalize와 cleaner 사용을 피해라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/1.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/8%20finalize%EC%99%80%20cleaner%20%EC%82%AC%EC%9A%A9%EC%9D%84%20%ED%94%BC%ED%95%B4%EB%9D%BC%209%20try-finally%20%EB%B3%B4%EB%8B%A4%EB%8A%94%20try-with-resources%EB%A5%BC%20%EC%82%AC%EC%9A%A9.md#9-try-finally%EB%B3%B4%EB%8B%A4%EB%8A%94-try-with-resources%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC)

[9. try-finally보다는 try-with-resources를 사용하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/1.%20%EA%B0%9D%EC%B2%B4%20%EC%83%9D%EC%84%B1%EA%B3%BC%20%ED%8C%8C%EA%B4%B4/8%20finalize%EC%99%80%20cleaner%20%EC%82%AC%EC%9A%A9%EC%9D%84%20%ED%94%BC%ED%95%B4%EB%9D%BC%209%20try-finally%20%EB%B3%B4%EB%8B%A4%EB%8A%94%20try-with-resources%EB%A5%BC%20%EC%82%AC%EC%9A%A9.md#9-try-finally%EB%B3%B4%EB%8B%A4%EB%8A%94-try-with-resources%EB%A5%BC-%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC)

<br>

### 2. 모든 객체의 공통 메서드
[10. equals는 일반 규칙을 지켜 재정의하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/2.%20%EB%AA%A8%EB%93%A0%20%EA%B0%9D%EC%B2%B4%EC%9D%98%20%EA%B3%B5%ED%86%B5%20%EB%A9%94%EC%84%9C%EB%93%9C/10%20equals%EB%8A%94%20%EC%9D%BC%EB%B0%98%20%EA%B7%9C%EC%B9%99%EC%9D%84%20%EC%A7%80%EC%BC%9C%20%EC%9E%AC%EC%A0%95%EC%9D%98%ED%95%98%EB%9D%BC.md#10-equals%EB%8A%94-%EC%9D%BC%EB%B0%98-%EA%B7%9C%EC%B9%99%EC%9D%84-%EC%A7%80%EC%BC%9C-%EC%9E%AC%EC%A0%95%EC%9D%98%ED%95%98%EB%9D%BC-1)

[11. equals를 재정의하려거든 hashCode도 재정의하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/2.%20%EB%AA%A8%EB%93%A0%20%EA%B0%9D%EC%B2%B4%EC%9D%98%20%EA%B3%B5%ED%86%B5%20%EB%A9%94%EC%84%9C%EB%93%9C/10%20equals%EB%8A%94%20%EC%9D%BC%EB%B0%98%20%EA%B7%9C%EC%B9%99%EC%9D%84%20%EC%A7%80%EC%BC%9C%20%EC%9E%AC%EC%A0%95%EC%9D%98%ED%95%98%EB%9D%BC.md#10-equals%EB%8A%94-%EC%9D%BC%EB%B0%98-%EA%B7%9C%EC%B9%99%EC%9D%84-%EC%A7%80%EC%BC%9C-%EC%9E%AC%EC%A0%95%EC%9D%98%ED%95%98%EB%9D%BC-1)

[12. toString을 항상 재정의하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/2.%20%EB%AA%A8%EB%93%A0%20%EA%B0%9D%EC%B2%B4%EC%9D%98%20%EA%B3%B5%ED%86%B5%20%EB%A9%94%EC%84%9C%EB%93%9C/12%20toString%EC%9D%84%20%ED%95%AD%EC%83%81%20%EC%9E%AC%EC%A0%95%EC%9D%98%ED%95%98%EB%9D%BC.md#12-tostring%EC%9D%84-%ED%95%AD%EC%83%81-%EC%9E%AC%EC%A0%95%EC%9D%98%ED%95%98%EB%9D%BC)

[14. Comparable을 구현할지 고민하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/2.%20%EB%AA%A8%EB%93%A0%20%EA%B0%9D%EC%B2%B4%EC%9D%98%20%EA%B3%B5%ED%86%B5%20%EB%A9%94%EC%84%9C%EB%93%9C/14%20Comparable%EC%9D%84%20%EA%B5%AC%ED%98%84%ED%95%A0%EC%A7%80%20%EA%B3%A0%EB%AF%BC%ED%95%98%EB%9D%BC.md)

<br>

### 2. 모든 객체의 공통 메서드

[15. 클래스와 멤버의 접근 권한을 최소화하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/3.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4/15.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EB%A9%A4%EB%B2%84%EC%9D%98%20%EC%A0%91%EA%B7%BC%20%EA%B6%8C%ED%95%9C%EC%9D%84%20%EC%B5%9C%EC%86%8C%ED%99%94%ED%95%98%EB%9D%BC%2016.%20public%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%97%90%EC%84%9C%EB%8A%94%20public%20%ED%95%84%EB%93%9C%EA%B0%80%20%EC%95%84%EB%8B%8C%20getter%2C%20setter%20%EB%A9%94%EC%84%9C%EB%93%9C%EB%A5%BC%20%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC.md)


[16. public 클래스에서는 public 필드가 아닌 getter, setter 메서드를 사용하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/3.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4/15.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EB%A9%A4%EB%B2%84%EC%9D%98%20%EC%A0%91%EA%B7%BC%20%EA%B6%8C%ED%95%9C%EC%9D%84%20%EC%B5%9C%EC%86%8C%ED%99%94%ED%95%98%EB%9D%BC%2016.%20public%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%97%90%EC%84%9C%EB%8A%94%20public%20%ED%95%84%EB%93%9C%EA%B0%80%20%EC%95%84%EB%8B%8C%20getter%2C%20setter%20%EB%A9%94%EC%84%9C%EB%93%9C%EB%A5%BC%20%EC%82%AC%EC%9A%A9%ED%95%98%EB%9D%BC.md)


[17. 변경 가능성을 최소화하라](https://github.com/Damongsanga/EffectiveJava3rd/blob/main/3.%20%ED%81%B4%EB%9E%98%EC%8A%A4%EC%99%80%20%EC%9D%B8%ED%84%B0%ED%8E%98%EC%9D%B4%EC%8A%A4/16.%20%EB%B3%80%EA%B2%BD%20%EA%B0%80%EB%8A%A5%EC%84%B1%EC%9D%84%20%EC%B5%9C%EC%86%8C%ED%99%94%ED%95%98%EB%9D%BC.md)
