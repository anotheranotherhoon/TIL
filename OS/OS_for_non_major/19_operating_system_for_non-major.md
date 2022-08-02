> 그림으로 쉽게 배우는 운영체제 - 감자님 강의 참조

프로세스는 독립적으로 실행되기도 하지만 다른 프로세스와 데이터를 주고 받으며 통신을 하는 경우도 있다.

통신은 한 컴퓨터 내에서 실행되고 있는 다른 프로세스와 할 수 도 있고 네트워크로 연결된 다른컴퓨터에 있는 프로세스와 할 수도 있다.

그럼 프로세스간 통신의 종류를 알아보자.

첫 번째는 한 컴퓨터내에서 프로세스 간 통신을 하는 방법으로 파일과 파이프를 이용하는 방법이다.

1. 파일을 이용하는 방법은 통신하려는 프로세스들이 하나의 파일을 이용해 읽고 쓰는 방법이다. 
2. 파이프를 이용한 방법은 운영체제가 생성한 파이프를 이용해 데이터를 읽고 쓰는 방법이다.

두 번 째로는 쓰레드를 이용한 방법이 있다.
이 방법은 한 프로세스 내에서 쓰레드간 통신을 하는 방법이다.
쓰레드는 코드, 데이터, 힙영역을 공유하고 스택영역만 각자 자기 것을 가지고 있다.
여기서 데이터 영역에 있는 전역변수나 힙을 이용하면 통신이 가능하다.

세 번째 방법은 네트워크를 이용한 방법이다.
운영체제가 제공하는 소켓통신이나 다른 컴퓨터에 있는 함수를 호출하는 RPC(원격 프로시저 호출)를 이용해 통신하는 방법이 있다.




