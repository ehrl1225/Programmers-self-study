# 파이썬 문법

## 1. 들여쓰기 (Indentation)
파이썬에서는 들여쓰기로 코드 블록을 구분합니다. 보통 공백 4칸을 사용합니다.

```python
if a > 1:
    print("a는 1보다 큽니다")
else:
    print("a는 1과 같거나 작습니다")
```

## 2. 주석 (Comments)
- 한 줄 주석: `#`
- 여러 줄 주석: `"""` 또는 `'''`

```python
# 한 줄 주석

"""
여러 줄
주석
"""
```

## 3. 변수와 자료형 (Variables and Data Types)
변수 선언 시 자료형을 명시할 필요가 없습니다.

- **숫자형**: `int`, `float`
- **문자열**: `str`
- **불리언**: `bool` (`True`, `False`)

```python
number = 10
pi = 3.14
greeting = "안녕하세요!"
is_true = True
```

## 4. 자료 구조 (Data Structures)
- **리스트 (List)**: 순서가 있고, 수정 가능. `[]`
- **튜플 (Tuple)**: 순서가 있고, 수정 불가능. `()`
- **딕셔너리 (Dictionary)**: Key-Value 쌍, 순서 없음. `{}`

```python
my_list = [1, "hello", 3.14]
my_tuple = (1, 2, 3)
my_dict = {"이름": "홍길동", "나이": 30}
```

## 5. 제어문 (Control Flow)
- **조건문**: `if`, `elif`, `else`, `match`
- **반복문**: `for`, `while`

```python
# 조건문
score = 85
if score >= 90:
    print("A")
elif score >= 80:
    print("B")
else:
    print("C")

# match 조건문
score = 1
match:
	case 1:
		print("1")
	case 2:
		print("2")
	case 3:
		print("3)
	case _:
		print("1,2,3중에 골라주세요")

# for 반복문
for i in range(5):
    print(i)

# while 반복문
count = 0
while count < 5:
    print(count)
    count += 1
```

## 6. 함수 (Functions)
`def` 키워드를 사용하여 함수를 정의합니다.

```python
def add(a, b):
    return a + b

result = add(3, 5)
print(result)  # 8
```

# 출처
Gemini-CLI
