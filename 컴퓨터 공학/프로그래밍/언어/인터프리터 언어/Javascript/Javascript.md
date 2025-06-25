
정적인 HTML에 동적인 면을 추가해주는 녀석
객체 기반의 [[인터프리터 언어]]다.
구조적 프로그래밍과 [[함수형 프로그래밍]]을 지원한다.

# [[Javascript 변수]]


# 함수 만들기
```javascript
function plus(a,b){
	return a+b;
}
```
리턴 타입이랑 매개변수에 타입을 붙이지 않음


함수는 변수에 넣을 수 있음
```javascript
const plus = function(a, b) {return a+b;}
```

익명함수는
```javascript
const plus = (a,b) => {
	return a+b;
}
```
이렇게 가능

```javascript
const plus = (a, b) => a+b;
```
이렇게 줄이는거 가능

# [[Javascript stream]]

# setTimeout(func)
급한 일을 먼저 실행한 후 매개변수의 함수를 실행한다.
따라서 HTML 중간에 넣어두면 HTML을 다 load하고 실행한다.

