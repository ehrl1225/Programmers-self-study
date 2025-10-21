QueryDSL에서는 조회 결과를 DTO로 직접 변환하기 위한 여러 가지 방법을 제공합니다. `Projections` 클래스를 사용하면 쿼리 결과로부터 바로 DTO 객체를 생성할 수 있어 코드를 간결하게 유지할 수 있습니다. 주요 방법 4가지는 다음과 같습니다.

## 1. `Projections.bean()` - 프로퍼티 접근 (Setter)

이 방법은 자바빈 규약(JavaBean convention)을 따릅니다. 즉, DTO의 기본 생성자와 Setter 메서드를 사용하여 조회 결과를 DTO 객체에 매핑합니다.

-   **장점**: 코드가 직관적이고, DTO 객체의 필드명이 변경되어도 Setter 이름만 맞으면 되므로 유연합니다.
-   **단점**: 실행 시점에 동적으로 객체를 생성하므로, 컴파일 타임에 오류를 잡을 수 없습니다.

```java
// MemberDto.java
public class MemberDto {
    private String username;
    private int age;

    // 기본 생성자 필수
    public MemberDto() {
    }

    // Setter 필수
    public void setUsername(String username) {
        this.username = username;
    }

    public void setAge(int age) {
        this.age = age;
    }
}

// Query
List<MemberDto> result = queryFactory
    .select(Projections.bean(MemberDto.class,
        member.username,
        member.age))
    .from(member)
    .fetch();
```

## 2. `Projections.fields()` - 필드 직접 접근

이 방법은 DTO의 필드에 직접 값을 주입합니다. Setter가 없어도 되지만, DTO의 필드명과 조회 대상의 별칭(alias) 또는 필드명이 일치해야 합니다.

-   **장점**: Setter가 필요 없어 코드가 더 간결해질 수 있습니다.
-   **단점**: 필드에 직접 접근하므로, 캡슐화 원칙에 위배될 수 있습니다. 필드명이 다를 경우 `as()`를 사용하여 별칭을 지정해야 합니다.

```java
// MemberDto.java
public class MemberDto {
    private String username;
    private int age;
    // 기본 생성자 필수
}

// Query
List<MemberDto> result = queryFactory
    .select(Projections.fields(MemberDto.class,
        member.username,
        member.age))
    .from(member)
    .fetch();

// 만약 DTO 필드명과 엔티티 필드명이 다른 경우
List<UserDto> result = queryFactory
    .select(Projections.fields(UserDto.class,
        member.username.as("name"), // DTO의 name 필드에 매핑
        member.age))
    .from(member)
    .fetch();
```

## 3. `Projections.constructor()` - 생성자 사용

이 방법은 DTO의 생성자를 호출하여 객체를 생성합니다. 조회하는 필드의 순서와 타입이 생성자의 파라미터와 정확히 일치해야 합니다.

-   **장점**: 컴파일 시점에 오류를 발견할 수 있습니다 (생성자 시그니처가 맞지 않을 경우). 필드명이 달라도 순서와 타입만 맞으면 되므로 유연합니다.
-   **단점**: 생성자의 파라미터 순서에 의존적이므로, 순서가 변경되면 코드를 수정해야 합니다.

```java
// MemberDto.java
public class MemberDto {
    private String username;
    private int age;

    public MemberDto(String username, int age) {
        this.username = username;
        this.age = age;
    }
}

// Query
List<MemberDto> result = queryFactory
    .select(Projections.constructor(MemberDto.class,
        member.username,
        member.age))
    .from(member)
    .fetch();
```

## 4. `@QueryProjection` - 어노테이션 활용

이 방법은 DTO의 생성자에 `@QueryProjection` 어노테이션을 붙여 사용하는 방식입니다. QueryDSL 플러그인을 설정하여 컴파일 시점에 Q-Type DTO를 생성해야 합니다.

-   **장점**: 컴파일 타임에 타입과 인자 개수를 모두 검증할 수 있어 가장 안전합니다. `Projections.constructor`와 달리 생성자 시그니처가 변경되어도 컴파일 오류로 바로 알 수 있습니다.
-   **단점**: DTO가 QueryDSL에 대한 의존성을 갖게 됩니다. 또한, 빌드 설정(Maven/Gradle)이 추가로 필요합니다.

```java
// MemberDto.java
public class MemberDto {
    private String username;
    private int age;

    @QueryProjection // 이 어노테이션을 추가
    public MemberDto(String username, int age) {
        this.username = username;
        this.age = age;
    }
}

// Gradle/Maven 컴파일 후 생성된 QMemberDto 사용
// Query
List<MemberDto> result = queryFactory
    .select(new QMemberDto(member.username, member.age))
    .from(member)
    .fetch();
```