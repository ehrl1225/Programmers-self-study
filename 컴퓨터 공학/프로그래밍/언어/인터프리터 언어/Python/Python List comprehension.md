for 문을 통해서 리스트를 만드는걸 간략하게 만든 것이다.

```python
size:int = 10
arr:list[int] = list()
for i in range(size):
	arr.append(i)
```
이 리스트를 만드는 걸 한 줄로 줄일 수 있다.

```python
arr:list[int] = (lambda size : [i for i in range(size)])(size:=10)
```
size에 10을 넣는 것을 시키기 위해서 상당히 복잡하게 보인다 그냥 size 변수를 없애자

```python
arr:list[int] = [i for i in range(10)]
```
엄청 간단해졌다.

짝수를 없애고 싶다면

```python
arr:list[int] = [i for i in range(10) if i%2!=0]
```
이런식으로 필터링도 가능하다.

# 출처
[링크](https://shoark7.github.io/programming/python/about-list-comprehension-python)