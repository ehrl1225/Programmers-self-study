
스프링 시큐리티의 `RoleHierarchy`는 권한(Role) 간의 계층 구조를 설정하여 권한 관리를 단순화하고 중복을 줄이는 기능입니다.

## 왜 사용하는가?

예를 들어, 시스템에 `ROLE_ADMIN`, `ROLE_MANAGER`, `ROLE_USER` 세 가지 권한이 있다고 가정해 보겠습니다.
- 관리자(Admin)는 모든 권한을 가져야 합니다.
- 매니저(Manager)는 매니저와 사용자의 권한을 가져야 합니다.
- 사용자(User)는 사용자 권한만 가집니다.

`RoleHierarchy`가 없다면, 관리자에게 `ROLE_ADMIN`, `ROLE_MANAGER`, `ROLE_USER` 세 가지 권한을 모두 부여해야 합니다. 이는 번거롭고 관리가 어렵습니다.

## RoleHierarchy 설정 방법

`RoleHierarchy`를 사용하면 권한 간의 상속 관계를 정의할 수 있습니다.

**예시:** `ROLE_ADMIN` > `ROLE_MANAGER` > `ROLE_USER`

위와 같이 설정하면, `ROLE_ADMIN` 권한을 가진 사용자는 자동으로 `ROLE_MANAGER`와 `ROLE_USER` 권한도 가지게 됩니다.

### SecurityConfig 설정 예제

```java
@Configuration
public class SecurityConfig {

    @Bean
    public RoleHierarchy roleHierarchy() {
        RoleHierarchyImpl roleHierarchy = new RoleHierarchyImpl();
        // " > " 기호를 사용하여 권한 계층을 설정합니다.
        // ADMIN은 MANAGER의 권한을, MANAGER는 USER의 권한을 가집니다.
        roleHierarchy.setHierarchy("ROLE_ADMIN > ROLE_MANAGER\n" +
                                   "ROLE_MANAGER > ROLE_USER");
        return roleHierarchy;
    }

    @Bean
    public MethodSecurityExpressionHandler methodSecurityExpressionHandler(RoleHierarchy roleHierarchy) {
        DefaultMethodSecurityExpressionHandler expressionHandler = new DefaultMethodSecurityExpressionHandler();
        expressionHandler.setRoleHierarchy(roleHierarchy);
        return expressionHandler;
    }

    // ... 기타 SecurityFilterChain 설정
}
```

## 장점

- **중복 제거**: 사용자에게 여러 권한을 일일이 부여할 필요가 없습니다. 최상위 권한만 부여하면 하위 권한은 자동으로 상속됩니다.
- **유지보수 용이**: 권한 정책이 변경될 때, `RoleHierarchy` 설정만 수정하면 되므로 코드 수정이 최소화됩니다.
- **직관적인 권한 체계**: 코드에서 `hasRole('USER')`와 같은 간단한 확인만으로도 상위 권한을 가진 사용자의 접근을 허용할 수 있습니다.
