[[어셈블리어]]를 쓰기 힘들어서 만들어낸 언어다.
UNIX 운영체제를 구현하기 위해서 개발했다.

문법으로는 Pointer, 함수, struct, \#define 같은 전처리 기능, include를 통해 헤더 파일을 가져오는 것도 가능하고 이정도 인 것 같다.
Pointer가 어려운 언어라 사람들이 기피하는 언어다.
하지만 C가 은근히 많이 쓰인다.

동적 메모리를 직접 관리해야한다.

# 논리
논리를 따로 지원하지는 않는다.
그래서 \#include \<stdbool.h\>로 0과 1 이상을 false, true로 사용해야한다.

# \#define
코드에 해당 문자열을 넣어준다.
매개변수를 받아서 일종의 함수처럼 쓸 수도 있다.
