
CPUTime = Instruction Count / Program \* Clock cycles / Instruction Count \* Seconds / Clock cycles이다.

자세한 설명은 생략하고 싶게 복잡한 이론이다.

간단하게 CPU가 빨리 처리할 수록 성능이 좋고
클럭의 속도가 높으면 높을 수록 성능이 좋고
동일한 프로그램당 필요한 명령어가 많을 수록 성능이 안좋아진다.

근데 클럭을 높이면 명령어가 많아지거나 
명령어를 줄이면 클럭이 내려간다거나 하는  상관관계가 있어서
밸런스를 잘 맞춰서 성능을 올려야 한다.

예를들어 x86이랑 RISC-V랑 비교하면
x86은 명령어 종류가 많고 RISC-V에서는 여러 개의 명령어로 이루어진 것을 하나의 명령어로 실행할 수 있고 명령어의 크기가 여러개라서 명령어를 읽는 과정이 필요하다.
그래서 프로그램당 명령어의 개수가 적고 고전력에서 좋은 성능을 가진다.

RISC는 명령어 종류가 적고 명령어의 크기가 일정하다.
프로그램당 명령어의 개수가 많고 저전력에서도 좋은 성능을 가진다.