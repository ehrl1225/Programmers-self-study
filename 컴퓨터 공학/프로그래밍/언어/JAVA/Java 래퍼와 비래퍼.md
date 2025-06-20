여기서 예시를 int와 Integer로 표현하자면

int는 기본 자료형이고
Integer은 래퍼 클래스임

그러니까 int는 스택에 저장되고 Integer은 힙에 저장됨

그렇기에 int는 null의 값을 가지는게 불가능하고
Integer은 null의 값을 가지는게 가능함
그런데 그러면 new를 통해 Interger를 만들어야 하는거 아닌가 생각할 수 있는데
자동으로 해준다고 하네 그래서 new를 쓸 필요 없고 new를 쓰면 메모리 낭비라고 하네