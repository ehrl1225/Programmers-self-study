# 기본 구조
태그 여는건 <태그>로
태그 닫는건 </태그>로
안에 작성할거 없으면 <태그 />로

\<script\> 태그를 통해 [[Javascript]]를 불러온다.
\<link\> 태그를 통해 [[CSS]]를 불러온다.

# \<div\>
분리할 때 사용함
display:block 처리를 한다.
따라서 div + inline = span
# \<span\>
분리할 때 사용한다.
display:inline 처리를 한다.
따라서 span + block = div

# \<input\>
입력을 할 수 있는 element다.


# \<form\>
어딘가로 전송하기 위해서 만드는 것이다.
```HTML
<form action="https://search.naver.com/search.naver" target="_blank">
```
input에 name을 넣고 type이 submit인 Button을 누르면 링크에 파라미터를 넣고 이동한다.