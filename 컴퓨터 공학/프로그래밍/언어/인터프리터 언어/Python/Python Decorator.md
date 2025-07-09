
함수를 함수로 감싸서 실행하기 위한 방법이다.
간단하게 예시를 보여주자면

```python
import time
def timer(func):
	count = 0
	def inner(*args, **kwargs):
		nonlocal count
		start = time.time()
		result = func(*args, **kwargs)
		elapsed_time = time.time() - start
		print(f"[{count}] elapsed time : {elapsed_time:.02f}")
		count+=1
		return result
	return inner

@timer
def test():
	print("test")

test()
```

이런식으로 함수가 실행하기 전, 함수가 실행 한 후에 기능을 더할 수도 있고
데코레이터 함수에 변수를 둬서 함수를 몇 번 실행시키냐에 따라 출력값이 다르게 할 수도 있다.

```python
import time

def timer(*arg):
	def decorator(func):
		count = 0
		def inner(*args, **kwargs):
			nonlocal count
			start = time.time()
			result = func(*args, **kwargs)
			elapsed_time = time.time() - start
			print(f"[{count}] elapsed time : {elapsed_time:.02f}")
			count+=1
			return result
		return inner
	return decorator

@timer("test")
def test():
	print("test")

test()
```
이런식으로 매개변수를 넣을 수도 있다.

```python
def test1(func):
    print("test1")
    def wrapper():
        return func()
    return wrapper

def test2(func):
    print("test2")
    def wrapper():
        return func()
    return wrapper

@test1
@test2
def test3():
    print("test3")
```
실행할 경우 어떤 값이 발생할까?
> test2
> test1

