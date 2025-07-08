
# 변수

파이썬은 타입을 명시할 수 있다.
그렇다고 타입 체크를 하지는 않는다.
```python
a:int = 10
```
이런 방식으로 작성이 가능하고 IDE에서는 이를 확인해서 경고까지는 띄우지만 실행할 때 에러를 발생시키지는 않는다.

# 함수

```python
def hello( a:int, b:int) -> int:
	return 1
```
이 방식으로 함수 중 매개변수가 어떤 타입을 가질 것이고 어떤 타입을 반환할지 명시 가능하다.

# list
```python
arr:list[int] = [1,2,3]
```
이처럼 리스트에 어노테이션이 가능하다.

# tuple
```python
t : tuple[int,str, bool] = (1, "a", False)
```
튜플은 하나하나 다 적어 줘야 한다.

# dict
```python
dictionary: dict[str, int] = { "a" : 1}
```

# class
```python
class Test:
	pass

t:Test = Test()
```
클래스는 이렇게 클래스 이름을 작성하면 된다.

# Callable
```python
from typing import Callable

def test(func : Callable[[int], str], arg:int) -> str:
	return func(arg)


test(lambda x: str(x), 1)
```
이처럼 함수를 입력으로 받을 경우 매개변수와 반환값의 타입을 어노테이션을 할 수 있다.

# Generics
```python
from typing import Sequence, TypeVar

T = TypeVar('T')      # Declare type variable

def first(l: Sequence[T]) -> T:   # Generic function
    return l[0]
```
이처럼 list\<T\>를 사용할 수 있다.

```python
from typing import TypeVar

AnyStr = TypeVar('AnyStr', str, bytes)

def concat(x: AnyStr, y: AnyStr) -> AnyStr:
    return x + y
```
타입을 제한 할 수도 있고

```python
from typing import TypeVar, Generic

T = TypeVar('T')

class LoggedVar(Generic[T]):
    def __init__(self, value: T, name: str, logger: Logger) -> None:
        self.name = name
        self.logger = logger
        self.value = value

    def set(self, new: T) -> None:
        self.log('Set ' + repr(self.value))
        self.value = new

    def get(self) -> T:
        self.log('Get ' + repr(self.value))
        return self.value

    def log(self, message: str) -> None:
        self.logger.info('{}: {}'.format(self.name message))
```
처럼 MyClass\<T\>와 같은 것을 만들 수 있다.

# 출처
[링크](https://engineer-mole.tistory.com/182)