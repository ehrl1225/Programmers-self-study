생성자와 소멸자가 존재한다.

# 생성자
객체가 생성될 때 실행되는 메소드다.
```c++
class A{
private:
	int a;
public:
	A(int a):a(a){}
}
```
이런식으로 초기화를 할 수 있다.

# 소멸자
객체가 해제될 때 실행되는 메소드다.
```c++
class A{
private:
	int a;
public:
	A(int a):a(a){}
	~A(){}
}
```
이렇게 클래스 이름 앞에 ~를 붙여서 소멸자를 표시합니다.
