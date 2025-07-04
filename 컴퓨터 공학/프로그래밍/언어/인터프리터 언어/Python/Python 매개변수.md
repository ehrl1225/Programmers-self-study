파이썬에서는 함수를 정의할 때 매개변수를 여러 개를 작성할 수 있는데 기본 값을 정할 때는 기본 값이 없는 매개변수 이후에 작성해야 한다.

그리고 호출 할 때는 위치에 따라 작성하는 값 다음에 키워드를 통해 작성하는 값을 작성해야하고

파이썬에서는 매개변수를 여러 개를 받을 수 있다.
```python
import sys
def function(*args, **kwargs):
	print(*args, **kwargs)

function("test", file=sys.stderr)
```
이러면 에러로 test가 표시될 것이다.
\*args는 위치에 따라 입력 받는 매개변수고
\*\*kwargs는 키워드를 통해 입력 받는 매개변수다.
그대로 함수에 넣으면 입력 받을 때와 똑같이 입력을 시킬 수 있다.
그러니까 저기 함수에서는 
print("test", file=sys.stderr)로 호출이 되었다는 것이다.

