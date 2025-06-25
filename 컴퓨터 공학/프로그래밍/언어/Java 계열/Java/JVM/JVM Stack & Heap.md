
# [[JVM, JRE, JDK#JVM|JVM]]
컴파일 플랫폼과 타겟 플랫폼이 다르면 프로그램이 동작하지 않음
자바 바이트코드는 타겟 플랫폼에 상관 없이 JVM 위에서 동작한다.
JVM은 타겟 플랫폼에 의존한다.

## 설계 의도
네트워크에 연결된 모든 디바이스에서 작동하는 것이 목적이었다.


## 실행되기까지 과정
Lexical Analyzer, Syntax Analyzer, Sementic Analyzer, Intermediate Code Generator, Code Optimizer, Code Generator

# [[JVM, JRE, JDK#JVM|JVM]] 내부
## Runtime Data Areas
Method area와 Heap은 모든 [[스레드]]가 공유한다.

### Method Area
클래스 정보, 정적 데이터가 저장된다.
[[메모리 구조]]의 [[메모리 구조#데이터 영역|데이터 영역]]에 해당한다.

### Heap Area
런타임 때 생성한 모든 객체를 저장한다.
[[메모리 구조]]의 [[메모리 구조#힙 영역|힙 영역]]에 해당한다.

## Per Thread
[[스레드]] 마다 존재하는 공간

### Program Counter
각 [[스레드]]는 메서드를 실행하고 PC는 몇 번째 줄을 실행하는지 나타낸다.

### Stack
[[스레드]] 별 1개씩 존재한다.
스택 프레임은 메서드가 호출될 때마다 생성되고
메서드 실행이 끝나면 스택 프레임은 pop되어 스택에서 제거된다.
[[메모리 구조]]의 [[메모리 구조#스택 영역|스택 영역]]에 해당한다.
#### Stack Frame
##### Local Variable array
지역 변수가 저장된다.

##### Operand stack
연산할 때 필요한 값을 임시적으로 저장하는 공간

##### Frame data
Constant Pool, 이전 스택 프레임에 대한 정보, 현재 메서드가 속한 클래스/객체에 대한 참조 등의 정보를 갖는다.

##### Native Method Stack
Java Bytecode가 아닌 다른 언어로 작성된 메서드인 Native Method를 사용할 때 사용된다.

