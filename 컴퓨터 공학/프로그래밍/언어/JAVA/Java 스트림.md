내가 보기엔 함수형 프로그래밍 방식을 채택한 것으로 보임
파이썬의 range와 listcomprehension과 비슷한 것으로 보인다.

# 전체적인 흐름
stream을 통해 열고
filter를 통해 거르고
map을 통해 매핑 시켜서
collect를 통해 완성품을 만들어냄


# IntStream

```java
IntStream.rangeClosed(1, 10).forEach(
	new IntConsumer(){
		@Override
		public void accept(int value){
		System.out.println(value);
		}
	}
);

```

이걸 극단적으로 줄이면

```java
IntStream.rangeClosed(1, 10)
                .forEach(System.out::println);
```
가 된다.

# filter
조건문을 통해 걸러내는 것이다.
```
IntStream.rangeClosed(1, 10)
	.filter(e -> e % 2 != 0)
	.forEach(e -> {
		System.out.println(e);
});
```
이렇게


# mapToObj
객체로 만듬

# mapToInt
int 배열로 만듬
이걸 해두면 sum, average 가능

# toMap()
각각 key와 value에 값을 넣어 Map을 만들어낸다.
