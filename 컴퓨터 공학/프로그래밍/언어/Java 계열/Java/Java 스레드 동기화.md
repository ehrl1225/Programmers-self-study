
# synchronized 키워드
```java
public synchronized void increment() {
    count++;
}
```
이처럼 함수에 synchronized 키워드를 붙이면 메서드 전체로 동기화를 할 수 있다.

```java
public void increment() {
    synchronized(this) {
        count++;
    }
}
```
블록 단위로 동기화도 가능하고

```java
public static synchronized void log() {
    // ...
}
```
클래스 단위로 동기화도 가능하다

# ReetrantLock
```java
import java.util.concurrent.locks.ReentrantLock;

ReentrantLock lock = new ReentrantLock();

public void safeMethod() {
    lock.lock();
    try {
        // 임계 구역
    } finally {
        lock.unlock();  // 반드시 해제!
    }
}
```
좀 더 유연하게 락 제어를 할 때 사용한다.
# volatile
```java
private volatile boolean running = true;
```
항상 데이터를 가져올 때 메모리에서 가져오게 만든다.(안 할 경우에는 캐시 메모리에 있거나 레지스터에 있을 지도 모른다.)
하지만 원자성은 보장하지 않는다.

# Atomic
```java
import java.util.concurrent.atomic.AtomicInteger;

AtomicInteger counter = new AtomicInteger(0);

public void increment() {
    counter.incrementAndGet();  // 원자적 증가
}
```
락 없이 안전한 연산이 가능하다.

# 출처
코파일럿