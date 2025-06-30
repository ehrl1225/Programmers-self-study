# 트랜잭션 = 영속성 컨텍스트

# 더티채킹
트랜잭션 안에서 값을 수정하고 나서 save를 하지 않아도 변경을 눈치채서 save를 해줌

# Test에서 Rollback
Transactional 어노테이션을 하면 런타임 에러의 경우 Rollback을 하지만
그 외의 오류에는 Rollback을 하지 않음 그래서 Rollback 어노테이션을 통해 항상 rollback되게 함

# Test에서의 클래스에 Transactional 어노테이션
자동으로 Rollback을 붙인다.(main 폴더 내에서는 작동 안함)

# Transaction 설정
Transaction을 시작할 때 auto commit 을 끄는 과정을 거치는데
auto commit을 끄는 설정을 해두면 불필요한 쿼리가 사라진다.
Application.yml에서 수정가능

# flush
트랜잭션이 끝난 후 수행되어야 하는 더티체킹 및 여러가지 작업을 수행한다.
rollback을 하면 취소된다.
