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

## postgresql 해결방법
한 트랜잭션의 Isolation level을 변경한다.

postgresql에서는 repeatable read level에서 같은 데이터에 먼저 update한 tx가 commit되면 나중 tx는 rollback이 된다.
먼저 업데이트 한 트랜잭션이 이긴다고 해서 first-updater-win이라고 부른다.

## mysql 해결방법
mysql에서는 위 개념이 없어서 오류가 발생한다.

읽을 때 Locking read를 한다.
select 문에 for update 또는 for share를 붙여서 locking read를 한다.
for update는 exclusive lock을 획득하고
for share는 share lock을 획득한다.

처음으로 locking read를 하면 lock을 걸어서 읽지 못하게 막는다.
두번쨰로 locking read를 하면 읽지 못하다가 commit이 끝난 후 읽는다.

locking read는 가장 최근의 commit된 데이터를 읽는다.
따라서 업데이트가 된 데이터를 읽는다.

# Write skew
repeatable read isolation level에서
두 개의 트랜잭션이 두 변수에 접근해 각각 다른 변수에 쓰는데
각각 한개의 연산이 무시되어서 이상한 결과를 발생시키는 현상이다.
예시 문제는 transaction 1은 x와 y를 더해서 x에 쓰고
transaction 2는 x와 y를 더해서 y에 쓴다.
## mysql 해결방법
locking read를 사용한다.

## postgresql 해결방법
위와 같은 방식을 사용하면 rollback이 되는 [[MVCC#Lost Update#postgresql 해결방법|문제]]가 발생한다.
그래서 다시 시도를 해야한다.

## serializable
### mysql 방식
repeatable read와 유사하다
트랜잭션의 모든 평범한 select 문은 암묵적으로 select for share 처럼 동작한다.
for update 보다 데드락이 걸릴 가능성이 높기에 주의해야한다.

### postgresql 방식
SSI로 구현한다.
first-committer-winner 방식이다.


# 정리
MVCC는 데이터를 읽을 때 특정 시점 기준으로 가장 최근에 commit된 데이터를 읽는다.
데이터 변화 이력을 관리한다.
read와 write는 서로를 block 하지 않는다.

이렇게 읽는 것을 MySql에서는 Consistent Read라고 부른다.
