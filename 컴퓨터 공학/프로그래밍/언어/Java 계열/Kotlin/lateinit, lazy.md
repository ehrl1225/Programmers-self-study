# Kotlin의 지연 초기화: lateinit과 lazy

Kotlin에서는 프로퍼티(property)의 초기화를 지연시키는 두 가지 메커니즘, `lateinit`과 `lazy`를 제공합니다. 두 키워드 모두 프로퍼티 선언 시점에 초기화하지 않고 나중에 초기화할 수 있게 해주지만, 사용 목적과 방식에 차이가 있습니다.

---

### `lateinit`

`lateinit`은 **나중에 반드시 초기화될 것임을 컴파일러에게 약속**하는 키워드입니다. 주로 의존성 주입(DI)이나 Android의 `onCreate`와 같은 라이프사이클 메서드에서 초기화될 변수에 사용됩니다.

#### 주요 특징
- **`var` 프로퍼티에만 사용 가능**: `val` 프로퍼티는 선언 시점에 초기화되어야 하므로 사용할 수 없습니다.
- **Non-nullable 타입에만 사용 가능**: Nullable이 아닌 타입의 프로퍼티를 `null`로 초기화하지 않고도 선언할 수 있게 해줍니다.
- **기본(Primitive) 타입에는 사용 불가**: `Int`, `Double` 등 기본 타입에는 사용할 수 없습니다.
- **수동 초기화**: 개발자가 직접 프로퍼티를 초기화해야 합니다. 만약 초기화 전에 접근하면 `UninitializedPropertyAccessException` 예외가 발생합니다.
- **스레드 안전성 미보장**: 여러 스레드에서 동시에 접근할 경우 동기화 처리가 필요합니다.

#### 사용 예시
```kotlin
class MyComponent {
    lateinit var service: MyService

    fun setup() {
        // 외부에서 service 객체를 주입받아 초기화
        service = MyService()
    }

    fun useService() {
        // 초기화 여부 확인 (선택 사항)
        if (::service.isInitialized) {
            service.doSomething()
        }
    }
}
```

---

### `lazy`

`lazy`는 **프로퍼티에 처음 접근하는 시점에 초기화**를 수행하는 델리게이트(delegate)입니다. 초기화 비용이 높은 프로퍼티나, 실제로 사용될 때까지 초기화를 늦추고 싶을 때 유용합니다.

#### 주요 특징
- **`val` 프로퍼티에만 사용 가능**: 한 번 초기화되면 값을 변경할 수 없는 읽기 전용 프로퍼티에 사용됩니다.
- **모든 타입에 사용 가능**: Nullable, Non-nullable, 기본 타입을 가리지 않고 사용할 수 있습니다.
- **자동 초기화**: 프로퍼티에 최초로 접근할 때 `lazy` 블록이 실행되어 초기화되고, 그 결과는 캐시되어 이후에는 저장된 값을 반환합니다.
- **스레드 안전성 보장**: 기본적으로 스레드에 안전(`SYNCHRONIZED` 모드)하여 멀티스레드 환경에서도 초기화 블록이 한 번만 실행되도록 보장합니다.

#### 사용 예시
```kotlin
class MyViewModel {
    // database 프로퍼티에 처음 접근할 때 Room 데이터베이스가 생성됩니다.
    val database: AppDatabase by lazy {
        println("데이터베이스 인스턴스를 생성합니다.")
        Room.databaseBuilder(
            context,
            AppDatabase::class.java, "my-database"
        ).build()
    }

    fun getData() {
        // 이 시점에 database가 처음으로 초기화됩니다.
        val data = database.myDao().getAll()
    }
}
```

---

### `lateinit` vs `lazy` 비교 요약

| 구분 | `lateinit` | `lazy` |
| :--- | :--- | :--- |
| **프로퍼티 타입** | `var` (변경 가능) | `val` (읽기 전용) |
| **초기화 시점** | 개발자가 직접, 사용 전 | 최초 접근 시, 자동으로 |
| **값의 재할당** | 가능 | 불가능 |
| **Nullability** | Non-nullable 타입만 가능 | Nullable, Non-nullable 모두 가능 |
| **기본 타입 사용**| 불가능 | 가능 |
| **스레드 안전성** | 보장 안 됨 | 기본적으로 보장됨 |
| **예외 처리** | 초기화 전 접근 시 `UninitializedPropertyAccessException` | 컴파일 시점에 초기화 보장 |

결론적으로, **나중에 변경될 수 있는 변수**를 외부 요인(DI, 라이프사이클)에 의해 초기화해야 할 때는 `lateinit`을, **초기화 비용이 높고 한 번만 초기화되어야 하는 읽기 전용 프로퍼티**에는 `lazy`를 사용하는 것이 좋습니다.
