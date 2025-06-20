변수가 변경되어도 이는 바로 반영되지 않는다.
함수의 UI와 관련된 변수가 변경되면 함수를 다시 실행시켜 변경사항을 반영한다.
사용하는 방법은
```JavaScript
function App(){
	const [number, setNumber] = React.useState(0); // 변수 정의
	setNumber(number+1); // 값 변경
}
```
이런 식으로 사용이 가능하고 변경이 발생하면 
React는 해당 함수를 다시 실행시켜(최적화도 같이 하고) 값의 변경을 반영시킨다.


# [[Javascript]] 구조 분해 할당

```Javascript
function Link(props){
	const {href, text} = props;
}
```

```Javascript
function Link({href, text}){
	return <a href={href}>{text}</a>
}
```
이렇게도 가능

# 함수 매개변수
함수의 매개변수를 통해 중복을 줄일 수 있음

```javascript
function Link(props){
  return (
    <a className="text-red-500 underline hover:text-red-300" href={props.href} target="_blank">{props.text}</a>
  );
}
```

```javascript
<Link text="네이버" href="https://www.naver.com"/>
```

이렇게 매개변수로 넘겨 줄 수 있음