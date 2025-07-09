형을 변환할 때 사용한다.

# static_cast
사용법 : static_cast\<변환할 타입\>(변환 대상)
논리적으로 변경 가능한 경우에만 변경을 허용한다.

# const_cast
사용법 : const_cast\<변환할 타입\>(변환 대상)
const 및 volatile을 제거할 떄 사용한다.

사용해서 해결될 문제보다 발생할 문제가 더 많을 수도 있다.
따라서 왠만한 경우 사용하지 말 것

# reinterpret_cast
사용법 : reinterpret_cast \<변환할 타입\>(변환 대상)
명시적 변환과 동작이 동일 함으로 명시적 변환 대신 사용한다.
const를 사용하는 변환 대상은 사용할 수 없다.

이걸 사용하면 객체를 튜플처럼 사용 가능하다.

# dynamic_cast
사용법 : dynamic_cast \<변환할 타입\>(변환 대상)
포인터 간 형 변환시, 안전하게 down casting을 위해 사용한다.
참조 변수간 형 변환시, 안전하게 down casting을 위해 사용한다.
단 parent에 virtual 함수가 존재해야 정상 동작한다.

