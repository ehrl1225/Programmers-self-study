메서드에서 어느 예외를 던지는 지도 명시할 수 있고
명시를 하면 해당 메소드는 예외를 던질거니까 예외처리를 해야한다.
컴파일 타임에 예외처리를 안했는지 확인이 가능해 좀 더 안전하게 코딩을 할 수 있다.

# Error
복구가 어려운 상황에 발생한다.
보통 [[JVM, JRE, JDK#JVM|JVM]]에서 실행시키기 때문에 대응하기 어렵다.

Throwable을 상속한다.

# Exception
논리적 허점에서 발생한다.
개발자가 처리가 가능하다.

Throwable을 상속한다.


# 예외처리가 필요한 이유
처리를 하지 않고 실행을 하면 결과물이 이상한 값을 가질 수 있다.

# 예외의 계층

## Checked Exception
컴파일 시점에 발생한다.
예외 처리는 필수로 해야한다.
실수로 예외를 무시하는 것을 방지할 수 있다.
불필요한 예외 처리 코드가 증가할 수 있다.


## Unchecked Exception
런타임 시점에 발생한다.
예외 처리를 하지 않아도 된다.
예외 처리 코드가 간결하다.
실수로 예외를 놓칠 수 있다.

# 예외 발생 방법
앞에 throw를 적으면 된다.

# 예외 처리 방법
## 예외 넘기기
함수 뒤에 throws를 사용하여 이 함수를 호출한 함수에서 처리하게 하는 방법도 있고
## try-catch
try-catch를 통해 처리할 수도 있다.

## try-catch-finally
finally는 무조건 실행한다.
자원 반환하는 용도로 자주 사용한다.

## try-with-resources
```java
try (Scanner scanner = new Scanner(System.in)){
}catch(Exception e){
}
```
처럼 자원 반환하는 경우 자동으로 해주는 경우도 있다.

# 예외 종류
Exception을 상속하는 Exception 클래스는 Checked Exception이고
RuntimeException을 상속하는 Exception 클래스는 Unchecked Exception이다.

# 커스텀 예외
커스텀 예외를 통해 어떤 상황에 대한 예외인지 파악이 가능하다.
예외 클래스를 과도하게 정의될 수 있고 예외 처리 코드가 많아질 수 있다.
