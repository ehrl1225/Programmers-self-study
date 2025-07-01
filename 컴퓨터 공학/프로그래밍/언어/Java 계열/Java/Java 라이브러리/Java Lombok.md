어노테이션을 사용해서 생성자, getter, setter 등 귀찮은 코드를 줄여주는 라이브러리다.

# @AllArgsConstructor
모든 속성이 포함된 생성자를 만들어준다.

# @NoArgsConstructor
매개변수가 없는 생성자를 만들어준다.

# @RequiredArgsConstructor
필수로 들어가야 하는 속성을 포함한 생성자를 만들어 준다.

# @Getter  
Getter를 만들어 준다.
클래스에 두면 모든 속성에 Getter를 만들어준다.
각각 속성에 따로 해두면 따로 가능하다.

# @Setter  
Setter를 만들어 준다.
클래스에 두면 모든 속성에 Setter를 만들어준다.
각각 속성에 따로 해두면 따로 가능하다.

# @ToString
ToString를 만들어 준다.
클래스에 두면 모든 속성에 ToString를 만들어준다.
각각 속성에 따로 해두면 따로 가능하다.

# @SneakyThrows
try catch를 하지 않아도 컴파일 에러를 발생시키지 않게 한다.
예외를 발생시키지 않는다고 믿을 수 있을 때 사용하는 것이 좋아보인다.
