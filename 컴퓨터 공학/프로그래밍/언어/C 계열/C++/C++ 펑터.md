C++에서 클래스를 정의할 때

```C++
#include <iostream>
class Money{
private:
	int _Money = 0;
public:
	int operator()(){
		return this->_Money;
	}
}
```