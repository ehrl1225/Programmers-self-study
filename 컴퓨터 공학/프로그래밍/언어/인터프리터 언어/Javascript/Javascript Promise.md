[[비동기 프로그래밍]] 방식이며
[[Javascript 비동기 작동원리]]에 따라 동작한다.
명확하게 하고 싶다.
이거는 병렬 처리 방법이 아니기에
Promise에 연산 작업을 준다고 해서 실행시간이 줄어드는 게 아니다.
그저 [[IO 작업]]을 기다리는 시간에 다른 연산을 할 수 있는 것 뿐이다.

# 사용법
비동기 처리를 수행할 익명 함수를 인수로 전달 받는다.
해당 익명 함수는 성공할 경우의 콜백 함수와 실패할 경우의 콜백 함수를 입력 받는 익명 함수다.

Promise를 생성하면 해당 익명 함수를 실행한다.

```javascript
const promise = new Promise((res, rej) => { 
	console.log('promise');
});
```

이렇게 사용한다.

# 상태

## Pending
초기 상태를 말한다.

## Fulfilled
성공적으로 완료된 상태를 말한다.

## Rejected
실패 상태를 말한다.

## 예제

```javascript
const promise = new Promise((resolve, reject) => {
	console.log("hello");
});

// 1.

promise.then(
	function (result) {},
	function (error) {}
);

// 2.

promise.then(
	function (result) {}
).catch(
	function (error) {}
).finally(
	() => {}
);
```

이렇게 두 가지로 사용할 수 있다.

then의 경우 성공했을 때 실행하고
catch의 경우 실패했을 때
finally의 경우 무조건 실행하게 된다.


# all, race

## all
Promise.all(Promise 배열)로 사용하고 모든 작업이 끝나면 실행한다.

순서대로 실행되지만 앞의 함수를 기다리지 않는다.
처리 순서가 보장된다.
에러가 나면 그 즉시 에러를 반환한다.

## race
Promise.race(Promise 배열)로 사용하고 가장 짧은 작업이 끝나면 실행한다.

동시에 트리거가 된다.
