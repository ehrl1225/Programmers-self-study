64비트의 레지스터 32개를 가졌다.

# 레지스터
0번 레지스터는 항상 0의 값을 가지고 값을 쓰는게 허용되지 않는다.
1번 레지스터는 주소 값을 가지고 있다. 수정하지 말 것
2번 레지스터는 스택 포인터를 가지고 있다. 필요에 따라 수정하면 된다.
3번 레지스터는 전역 포인터를 가지고 있다.
4번 레지스터는 스레드 포인터를 가지고 있다.
5~7번 레지스터는 임시 값을 가질 때 사용한다.
8~9번 레지스터는 Saved 값을 가질 때 사용한다.
10~17번 레지스터는 매개변수값, 결과값을 가질때 사용한다.
18~27번 레지스터는 Saved 값을 가질 때 사용한다.
28~31번 레지스터는 임시 값을 가질 때 사용한다.
## 쓰면 안되는 레지스터
0~4번 레지스터
## 써도 되는 레지스터
그 외 전부
위는 관례 상으로 저렇게 쓰라는 거지 마음대로 써도 문제는 없다.

# 크기
byte는 1바이트를 말하고
halfword는 2바이트를 말하고
word는 4바이트를 말하고
doubleword는 8바이트를 말한다.
[[X86 어셈블리]]와는 다른 크기를 말하니까 조심해야한다.
# 연산
## mov
mov가 없다.
따라서 예를들어 10번 레지스터에 값을 넣으려면
add x10, x0
를 통해 값을 대입한다.

## add
두 개의 레지스터로 부터 더한 값을 한 레지스터로 넣는 작업을 한다.

