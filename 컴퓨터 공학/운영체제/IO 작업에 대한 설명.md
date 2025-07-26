간단하게 말하자면
파일에 쓰고 읽는 것이다.
화면에  화면에 출력하거나 입력하는 것 역시 파일에 읽고 쓰는 것이다.
Socket을 통해 데이터를 주고 받는 것 역시 파일에 쓰고 읽는 것이다.

화면에 출력하는 것이 파일에 쓰는 것이라는 것을 코드로 보여줄 수 있다.
`print`함수에는 file을 통해 파일에 작성하게 할 수 있다.
```python
with open("file.txt", "w") as f:
	print("hello", file=f)
```
이렇게
근데 똑같이

```python
import sys
print("hello", file=sys.stdout)
```
을 하면 화면에 출력된다.

그리고 Socket을 통해 데이터를 주고 받을 때는
소켓 통신 코드를 작성할 때
데이터를 받을 때는 recv, 데이터를 줄 때는 send를 쓰는데
이것 또한 read, write로 변경해도 정상적으로 작동한다.
