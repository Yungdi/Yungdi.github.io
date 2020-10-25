2020-10-26 00:01 월요일
fluent interface 설계 방식 
_예시2_ 와 같은 설계 방식은 코드의 가독성을 향상시키고 로직의 흐름을 이해하기 쉽게 한다. _예시1_ 처럼 생성자에서 모든 값들을 초기화할 수 없는 경우 값을 임시로 담아둘 변수를 만들어야한다. 이 때 객체들을 연결 시키는 데 코드 가독성이 떨어진다. 

_예시1_
```java
private void makeNormal(Customer customer) {
    Order o1 = new Order();
    customer.addOrder(o1);
    OrderLine line1 = new OrderLine(6, Product.find("TAL"));
    o1.addLine(line1);
    OrderLine line2 = new OrderLine(5, Product.find("HPK"));
    o1.addLine(line2);
    OrderLine line3 = new OrderLine(3, Product.find("LGV"));
    o1.addLine(line3);
    line2.setSkippable(true);
    o1.setRush(true);
}
```
_예시2_
```java
private void makeFluent(Customer customer) {
    customer.newOrder()
            .with(6, "TAL")
            .with(5, "HPK").skippable()
            .with(3, "LGV")
            .priorityRush();
}
```

출처: https://martinfowler.com/bliki/FluentInterface.html