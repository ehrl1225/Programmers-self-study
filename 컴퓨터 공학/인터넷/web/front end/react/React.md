
# React 란?
[[DOM]]을 만드는 애
[[Javascript]]를 통해 HTML을 작성하게 한다.

# JSX

함수 안에 HTML을 작성해 직관적으로 변경하려면 [[JSX]]

7react를 통해 나만의 태그를 만들 수 있음

# div
```html
<>
	내용
</>
```
이렇게 작성 가능

# 여러개 한번에

```Javascript
function App(){
	const links =[
		{
			href:...,
			text:...
		}
		...
	];
	return (
		<ul>
			{links.map(
				(link, index) => (
					<li key={link.text}>
						<a href={link.href}>{index+1} : {link.text}</a>
				))
			)}
		</ul>	
	)
}
```

이런식으로 작성 가능
map으로 만들어지는 엘리먼트의 최상위는 key값으로 unique 해야한다고 함
키에 index를 넣어도 되는데 추천하지는 않고 link.text로도 충분히 unique한 경우 link.text를 쓰는게 좋음

# style
```javascript
function text(){
	return <a style={{color:red, display:"inline"}}>테스트</a>;
}
```
이런식으로 작성해야 함
중괄호는 기본적으로 있고
객체 표현식으로 값을 넘겨준거임

# [[React 변수]]

# [[StrictMode]]
