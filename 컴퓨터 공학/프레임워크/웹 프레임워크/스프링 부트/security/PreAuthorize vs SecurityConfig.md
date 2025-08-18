

|항목|`@PreAuthorize`|SecurityConfig (`authorizeHttpRequests`)|
|---|---|---|
|**적용 대상**|메서드 단위 (Controller, Service 등)|URL 경로 단위 (HTTP 요청)|
|**검사 시점**|메서드 호출 직전|HTTP 요청 처리 직전|
|**필요 설정**|`@EnableMethodSecurity`|`SecurityFilterChain`|
|**표현력**|SpEL 사용 가능 (`hasRole`, `hasAuthority`, `#user.id == ...`)|단순한 역할/경로 매칭|
|**보안 범위**|내부 로직까지 보호 가능|외부 요청만 필터링|
|**우선순위**|`SecurityConfig`가 먼저 적용됨|이후 `@PreAuthorize`가 실행됨|
