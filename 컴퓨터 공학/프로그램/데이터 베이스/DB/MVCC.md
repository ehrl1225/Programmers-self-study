MultiVersion Concurrency Control의 약자다

MVCC는 commit된 데이터만 읽는다.

# Isolation Level
## read commited
read하는 시간을 기준으로 그 전에 commit된 데이터를 읽는다.

## repeatable read
트랜잭션 시작 시간 기준으로 그 전에 commit된 데이터를 읽는다.

## serializable
### mysql
MVCC로 동작하기 보다 lock으로 동작한다.

### postgresql
SSI(Serializable Snapshot Isolation) 기법이 적용된 MVCC로 동작한다.

## read uncommitted
MVCC는 committed된 데이터를 읽기 때문에 
이 level에서는 보통 MVCC가 적용되지 않는다.

postgresql의 경우 read uncommitted level이 존재하지만
read committed level처럼 동작한다.

# Lost Update
두 개의 트랜잭션이 동시에 돌아갈 때 같은 데이터에 접근할 때 둘다 read committed의 경우
한 트랜잭션의 연산을 무시하게 되는데 이 상황을 말한다.

## 해결방법
한 트랜잭션의 Isolation level을 변경한다.

postgresql에서는 repeatable read level에서 같은 데이터에 먼저 update한 tx가 commit되면 나중 tx는 rollback이 된다.
먼저 업데이트 한 트랜잭션이 이긴다고 해서 first-updater-win이라고 부른다.

mysql에서는 위 개념이 없어서 오류가 발생한다.


# 정리
MVCC는 데이터를 읽을 때 특정 시점 기준으로 가장 최근에 commit된 데이터를 읽는다.
데이터 변화 이력을 관리한다.
read와 write는 서로를 block 하지 않는다.

이렇게 읽는 것을 MySql에서는 Consistent Read라고 부른다.
