> 그림으로 쉽게 배우는 운영체제 - 감자님 강의 참조

운영체제가 작업을 처리하는 단위는 프로세스다.

사용자가 운영체제에게 작업을 요구하면 그만큼 프로세스의 수가 늘어난다.

프로세스를 생성하면 PCB가 생성되고 메모리에 코드, 데이터, 스택, 힙영역을 만들어 줘야한다.

프로세스의 수가 많아지면 프로세스의 수 만큼 PCB, 코드, 데이터, 스택, 힙영역도 만들어줘야 하기 때문에 너무 무거워 진다.

예를 들어 웹브라우저를 실행시키면 프로세스가 1개 생성된다. 여기서 웹브라우저의 탭을 1개 더 추가하면 기존 프로세스를 복사해서 총 2개의 프로세스가 존재하게 된다. 만약 탭을 20개를 추가한다면 프로세스의 복사가 20번 일어나고 PCB와 코드, 데이터, 스택, 힙영역이 20개 생성된다.

결국 웹브라우저가 메모리를 너무 많이 차지하게 된다. 

웹브라우저의 택들은 서로 통신을 하려면 IPC를 이용해야 하는데 IPC는 통신의 비용이 상대적으로 많이 든다. 컴퓨터 시스템 개발자들은 어떻게 이 문제를 해결할까 고민했다. 그래서 "쓰레드"라는 것을 고안했다. 쓰레드는 프로세스내에 존재하는 것으로 1개 이상이 있을 수 있다.
1개의 쓰레드에 1개 이상의 쓰레드가 있을 수 있고 10개의 쓰레드가 있을 수 있다.

한 프로세스 내에 쓰레드들은 그 프로세스의 PCB, 코드, 데이터, 힙영역을 공유한다. 스택은 공유하지 않고 쓰레드마다 하나 씩 가지고 있는다. 이제 프로세스내에 여러 개의 쓰레드가 있으니 이 쓰레드도 구분해야 할 필요가 생겼다. 

그래서 쓰레드 ID도 부여하고 이 쓰레드를 관리하기 위한 TCB(Thread Control Block)이 생겼다. 이제 운영체제 관점에서 쓰레드도 구분이 가능해졌다. 이제 운영체제가 작업을 처리하는 단위는 프로세스내에 쓰레드이다. 

웹브라우저를 실행하면 프로세스 하나가 생성되고 쓰레드도 하나 생성된다. 여기서 탭을 하나 더 추가하면 프로세스를 복사해서 사용하는 것이 아니라 쓰레드를 하나 더 생성한다.

이렇게 되면 프로세스 내에 쓰레드가 2개가 있는 것이다. 

프로세스와 쓰레드의 장단점 
첫 번째는 안정성이다.
프로세스는 서로 독립적이기 때문에 하나의 프로세스가 문제가 있더라도 다른 프로세스가 영향을 받지 않는다.

반면 쓰레드는 하나의 프로세스내에 존재하기 때문에 해당 프로세스에 문제가 생기면 그 안에 있는 모든 쓰레드에 문제가 생기게 된다.

이러한 이유로 안정성측면에서는 프로세스 방식이 쓰레드 방식보다 더 우수하다.

두 번째는 속도와 자원이다.
각각의 프로세스는 각각의 고유한 자원을 가지고 있다. 코드, 데이터, 힙, 스택영역을 전부 따로 두고 있고 프로세스간의 통신을 하려면 IPC를 이용해야해서 오버헤드가 크고 속도가 느리다.
반면 쓰레드는 한 프로세스내에서 스택영역을 제외한 영역은 모두 공유하기 때문에 오버헤드가 굉장히 작다. 쓰레드간에 통신은 데이터를 공유할 수 있으니 쉽게 할 수 있지만 공유되는 공간에서 문제가 될 수 있다. 이 문제는 프로세스 동기화에서 알아보자.