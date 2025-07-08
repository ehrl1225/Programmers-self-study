내부적으로 스웨거를 사용해 [[OPEN API]]문서를 만들어준다.

[[스프링]]에서 추천하는 방법은 아니라서 직접 implement 해야한다.
[링크](https://mvnrepository.com/artifact/org.springdoc/springdoc-openapi-starter-webmvc-ui)를 통해 implement 코드를 얻을 수 있다.


```kotlin
implementation("org.springdoc:springdoc-openapi-starter-webmvc-ui:2.8.9")
```

# 로그인
@SecurityScheme 추가하면 Open API 문서에 로그인 버튼이 추가된다.

