relational database의 relations들이 언제나 항상 지켜줘야 하는 제약 사항을 말한다.

# implicit constraints

relational data model 자체가 가지는 constraints를 말한다.
relation은 중복되는 tuple을 가질 수 없다.
relation 내에서는 같은 이름의 attribute를 가질 수 없다.

# schema-based constraints
주로 DDL을 통해 schema에 직접 명시할 수 있는 constraints다.
explicit constraints라고 부른다.

## domain constraints
attribute의 value는 해당 attribute의 domain에 속한 value여야 한다.

## key constrainsts
서로 다른 tuples는 같은 value의 key를 가질 수 없다.

## NULL value constraints
attribute가 NOT NULL로 명시됐다면 NULL을 값으로 가질 수 없다.

## entity integrity constraints
primary key는 value에 NULL을 가질 수 없다.

## referential integrity constraints
FK와 PK와 도메인이 같아야 하고 PK에 없는 Value를 FK가 값으로 가질 수 없다.
