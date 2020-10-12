병렬 프로그래밍
===========

#### 스레드를 사용하는 이유
- 시스템 자원을 효율적으로 활용
- 시스템이 갖고 있는 능력을 최대한 사용
 
#### 성능
- 성능을 높인다 = 더 적은 자원을 사용하면서 더 많은 일을 하도록한다.
- 자원이란 CPU, 메모리, 네트워크 속도,디스크 속도, 데이터베이스 처리 속도, 디스크 용량 등이다.

#### Executor.execute (진행시켜! (나몰라라...)) vs ExecutorService.submit (공손하게 제출하면서 진행상황 및 종료여부를 확인할 수 있는 Future 를 돌려줌)
```
Executor.execute 와 ExecutorService.submit 은 예외 처리 전략에 차이가 있다.  
Executor.execute 의 기본 처리 전략은 예외 발생 시 UncaughtExceptionHandler 가 stacktrace 를 콘솔에 출력한다. (custom handler 사용 가능) 
ExecutorService.submit 는 Future 의 get 메소드 호출 시 ExecutionException 발생시킨다.
```

**의문점**
``` 
ExecutorService 의 <T> Future<T> submit(Runnable task, T result) 는 왜 존재할까? 설계 목적이 뭘까? 
```

```java
public interface ExecutorService {
    <T> Future<T> submit(Runnable task, T result);
}
```
#### 용어 정리
- 처리량(throughput): 병렬로 실행되는 여러개의 작업 각자가 작업을 끝내는 속도
- 응답성(responsiveness): 요청이 들어온 이후 작업을 마치고 결과를 줄 때까지의 시간. = latency
- 확장성(scalability): 자원을 확보할 때마다 그에 따라 처리할 수 있는 작업량이 늘어나는 정도
- 활동성(liveness):
- 안전성(safety): 
