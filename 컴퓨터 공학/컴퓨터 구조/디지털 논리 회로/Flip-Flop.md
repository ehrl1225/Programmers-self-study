[[Latch]]에 입력 값을 넣고 클럭을 작동 시키면 출력값에 반영되는 방식이다.
여러가지 Flip-Flop이 있는데

# D-Flip-Flop
D-Flip-Flop의 경우 입력값이 D, Clock이고 출력값이 Q, Q' 라고 하면
D가 High고 한 클럭이 지나면 Q의 값이 High가 된다.
D가 Low고 한 클럭이 지나면 Q의 값이 Low가 된다.

# T-Flip-Flop
T-Flip-Flop의 경우 입력값이 T, Clock이고 출력값이 Q, Q'면
T가 High고 한 클럭이 지나면 지난 Q의 반대 값이 된다.
T가 Low고 한 클럭이 지나면 결과 값은 변하지 않는다.
T가 의미하는게 Toggle이다.
이건 카운터에 쓰기에 좋다.
