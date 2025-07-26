
대부분의 에러의 원인이 메모리에서 나온다는 것을 해결하기 위해
메모리를 자동으로 정리하지만 메모리를 해제할 때 해제할 메모리를 찾는 오버헤드를 피하기 위해
만들어낸 언어다.
그러니까 메모리는 어디에서 해제될지 컴파일 타임에 알게 된다.

# [Rust 문서 링크](https://doc.rust-kr.org/foreword.html)

# 웹 개발
러스트로도 웹개발이 가능하다.
[링크](https://mycodings.fly.dev/blog/2023-09-04-howto-rust-web-server-web-application-with-actix-web)

# 변수
변수를 생성하면 기본적으로는 수정 불가다.
mut을 붙여야만 수정이 가능하다.

같은 스코프에서 같은 이름의 변수를 생성 가능하다.

# Null
rust는 Null을 만들지 않았다.
왜냐하면 토니 호어라는 과학자가 말했다시피
Null을 만든 걸 수십억 달러짜리 실수라고 말하며 후회했다고 할정도니까
그래서 Optio\<T\>를 만들어 null을 대신했다.

# struct

# trait
