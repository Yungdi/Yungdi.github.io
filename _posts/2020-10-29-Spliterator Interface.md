2020-10-29 01:15
```java
public interface Spliterator<T> {
    boolean tryAdvance(Consumer<? super T> action);
    Spliterator<T> trySplit();
    long estimateSize();
    int characteristics();
}
```
#### 분할할 수 있는 반복자
java8 부터 Iterable Interface 에 default mehtod 로 Spliterator 구현을 제공한다.
default Spliterator<T> spliterator() {
    return Spliterators.spliteratorUnknownSize(iterator(), 0);
}
