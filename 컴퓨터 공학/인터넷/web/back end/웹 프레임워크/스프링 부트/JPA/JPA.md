
우리는 개발자 => Srping Data JPA => JPA => 하이버네이트 => JDBC => MySQL의 형태로 사용할 예정

JPA를 설치하면 DB에 연결하지 않으면 실행이 안되는데 H2를 같이 깔면 H2가 메모리 모드로 작동시켜 실행할 수 있다.

자동 생성되는 ID값은 Reflections으로 final이어도 값을 넣어줌
[[ORM]]을 지원한다.

# 객체 생성시 기본 생성자
엔티티 객체를 생성할 때 Reflection을 사용하는데 기본 생성자가 필요하다.
기본 생성자가 

# [[JPA Transaction]]


# [[JPA 명명 규칙]]
JPA는 메소드를 만들어두면 자동으로 메소드를 만들어준다.
