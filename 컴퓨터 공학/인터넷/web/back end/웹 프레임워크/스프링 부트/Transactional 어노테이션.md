스프링 부트는 @Transactional 어노테이션이 들어간 메소드가 발견되면 
스프링은 해당 객체를 만들 때 Transaction 기능을 담은 프록시로 만든다.
[[Proxy Pattern]]이 뭔지 모른다면 여기에 참조

그리고 @Transactional 어노테이션이 있는 메소드를 실행하기전 Transaction을 시작하고
메소드가 종료되면 Transaction을 종료한다. 

이 프록시에서 메소드를 실행하지 않고 객체에서 메소드를 실행하면 Transaction기능이 작동하지 않는다.

그리고 안에서는 어떤일이 일어나냐면 [[JPA Transaction]]
