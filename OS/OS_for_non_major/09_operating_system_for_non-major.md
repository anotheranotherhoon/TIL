> 그림으로 쉽게 배우는 운영체제 - 감자님 강의 참조

컨텍스트 스위칭은 프로세스를 실행하는 중에 다른 프로세스를 실행하기 위해 실행중인 프로세스의 상태를 저장하고 다른 프로세스의 상태값으로 교체하는 것이다.

컨텍스트 스위칭이 일어날 때 PCB의 내용이 변경된다.

실행중인 프로세스의 작업내용을 PCB에 저장하고 실행될 기존 프로세스의 PCB의 내용대로 PCB가 다시 세팅된다.
컨텍스트 스위칭이 일어날 때 PCB의 변경하는 값들로는 프로세스 상태, 다음 실행할 명령어의 주소를 담고있는 프로그램 카운터, 각종 레지스터값 등이 있습니다.

프로세스 두 개가 컨텍스트 스위칭을 하는 상황을 살펴보겠습니다.
프로세스 A가 실행을 하는데 CPU점유시간을 초과했습니다. 운영체제는 프로세스A가 CPU를 너무 오래 사용했다고 판단하고 인터럽트를 발생시킵니다.

프로세스A는 하던 일을 멈춥니다. 그리고 나중에 현재상태에서 시작되어야 하기 때문에 현재 CPU의 레지스터 값 등을 PCB A에 저장합니다.

이제 PCB B를 참조해서 이전 프로세스 B의 상태로 CPU의 레지스터값을 설정한다.
여기에는 다음 실행할 명령어의 주소를 가지고 있는 프로그램 카운터를 가지고 있기 때문에 바로 프로세스 B를 실행할 수 있다.

프로세스 B가 점유시간동안 CPU를 사용하다가 점유시간이 다되면 운영체제는 다시 인터럽트를 발생시킨다. 

그리고 프로세스 B의 현재 상태를 PCB B에 저장하고 PCB A에서 프로세스 A의 상태를 가져오고 다시 프로세스 A를 실행시킨다. 

이런식으로 메모리에 있는 모든 프로세스들은 컨텍스트 스위칭을 한다. 
컨텍스트 스위칭이 발생하는 이유는 다양하다.
CPU 점유시간이 다 되거나, I/O요청이 있거나 다른 종류의 인터럽트가 있을 때 발생한다.



