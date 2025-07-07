함수처럼 쓸 수 있는 클래스다.

C++에서 클래스를 정의할 때

```C++
#include <iostream>
class Money{
private:
	int _Money = 0;
public:
	Money(int money):_Money(money){}

	int operator()(){
		return this->_Money;
	}
}
```

이런 식으로 가능하고
```C++
#include <iostream>

int main(){
	Money money = Money(100);
	std::cout << money() << std::endl;
}
```
