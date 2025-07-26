```python
def simple_generator():
	yeild 1
	yeild 2
	yeild 3
gen = simple_generator()
print(next(gen))
print(next(gen))
print(next(gen))
```
함수를 진행하다가 멈춰서 값을 반환한다.
for each로 반복문을 실행할 수 있다.
메모리 사용 절약이 목적이다.

출처 [링크](https://hyeonql.tistory.com/entry/%ED%8C%8C%EC%9D%B4%EC%8D%AC-Yield-%EC%9D%B4%ED%95%B4%ED%95%98%EA%B8%B0-%EC%98%88%EC%A0%9C%EC%99%80-%ED%95%A8%EA%BB%98-%EC%83%81%EC%84%B8-%EA%B0%80%EC%9D%B4%EB%93%9C)