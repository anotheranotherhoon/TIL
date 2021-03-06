> 그림으로 쉽게 배우는 운영체제 - 감자님 강의 참조

스케줄링의 목표는 여러 개가 있다.

첫 번째는 리소스 사용률이다.
CPU 사용률을 높이는 것을 목표로 할 수도 있고 I/O 디바이스의 사용률을 높이는 것을 목표로 할 수도 있다.

두 번째는 오버헤드 최소화이다.
스케줄링을 하기 위한 계산이 너무 복잡하거나 컨텍스트 스위칭을 너무 자주하면 배보다 배꼽이 더 커지는 상황이 나온다. 스케줄러는 이런 오버헤드를 최소화하는 것을 목표로 한다. 

세 번째는 공평성이다.
모든 프로세스에게 공평하게 CPU가 할당되어야 한다.
특정 프로세스에게만 CPU가 계속 할당된다면 불공평하다.
여기서 공평의 의미는 시스템에 따라 달라질 수도 있다.
자율주행 자동차의 운영체제의 경우 음악재생, 온도체크 보다 자율주행 프로세스에 더 많은 CPU를 할당하는게 공평하다.

네 번째는 처리량이다.
같은 시간내에 더 많은 처리를 할 수 있는 방법을 목표로 한다.

다섯 번째는 대기시간이다.
작업을 요청하고 실제 작업이 이루어지기 전까지 대기하는 시간이 대기하는 시간이 짧은 것을 목표로 한다.

여섯 번째는 응답시간이다.
대화형 시스템에서 사용자의 요청이 얼마나 빨리 반응하는지가 중요하기 때문에
응답시간이 짧은 것을 목표로 한다.

위의 목표들을 모두 최고의 수준으로 유지하기는 힘들다.
그 이유는 목표간에 서로 상반되는 상황이 있기 때문이다.

예를 들어 처리량을 높이기 위해서는 하나의 프로세스에 CPU를 오래 할당해야 한다. 
반면 응답시간을 줄이기 위해서는 여러프로세스에 골고루 CPU를 할당해야 하기에 서로 상반되기 때문에 처리량과 응답시간의 목표를 함께 달성할 수 없다.

이때는 사용자가 사용하는 시스템에 따라서 목표를 다르게 설정한다.
터치스크린과 같이 사용자에게 빠른 응답시간이 필요한 경우는 응답시간에 초점을 맞추고
과학 계산과 같은 경우는 처리량이 높도록 초점을 맞춘다.

일반 사용자의 경우는 특별한 목적이 없다면 어느 한 쪽에 치우치지 않도록 밸런스를 유지하는게 중요하다. 
