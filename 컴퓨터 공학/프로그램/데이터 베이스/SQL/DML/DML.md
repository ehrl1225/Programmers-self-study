# SELECT

explain을 앞에 넣어서 사용하면 검색을 어떻게 했는지 알 수 있다.
## union
두 개의 테이블을 하나로 합친다.
join과 다르게 수직적으로 커진다.

## join
두 개의 테이블을 하나로 합친다.
union과 다르게 수평적으로 커진다.

# INSERT

INSERT 안에 SELECT를 넣을 수 있다.
예시)
```SQL
INSERT INTO member (regDate, loginId, loginPw, name)
SELECT NOW(), UUID(), 'pw', '아무개'
form member;
```
# UPDATE
# DELETE

