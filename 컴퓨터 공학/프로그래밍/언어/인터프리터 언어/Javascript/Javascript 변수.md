var let const로 나뉘어진다.

# var
중복 선언과 재할당이 가능하다.
선언이 되면 선언 전에도 참조가 가능한데 undefined가 뜨면서 에러가 발생하지 않는다.
문제가 많으니 let을 사용하도록

# let
중복 선언을 허용시키지 않으며 에러를 발생시킨다.
재할당은 가능하다.

# const
중복 선언과 재할당을 허용시키지 않는다.

# 문자열에 변수 넣기
```javascript
number = 1;
console.log(`number = ${number}`);
```
이런식으로 문자열에 변수를 넣을 수 있다.
