2020-10-29 00:13 목요일
```java
public interface Future<V> {
  V get() throws ExecutionException, InterruptedException;
  V get(long timeout, TimeUnit timeUnit) throws ExecutionException, InterruptedException;
  boolean cancel(boolean ifRunning);
  boolean isDone();
  boolean isCancelled();
}
```
#### boolean cancel(boolean mayInterruptIfRunning)
작업의 실행을 취소하려는 시도.   
취소 시도는 작업이 **이미 완료됐거나 이미 취소됐거나** 다른 이유에 의해서 취소될 수 없다면 실패한다.   
만약 취소 요청이 호출됐을 때 작업이 아직 실행되기 전이라면 작업은 실행되지 않는다.   
만약 이미 시작됐다면 메소드의 argument 에 따라 실행 중이던 스레드를 인터럽트할 지 말 지 결정한다.  
취소 요청이 ture 반환된 이후에 isDone 과 isCancelled 는 **항상 true 를 반환**한다.  
