> 그림으로 쉽게 배우는 운영체제 - 감자님 강의 참조
### 유니프로그래밍
유니프로그래밍은 메모리에 오직 하나의 프로세스가 올라온 것을 말한다.

### 멀티프로그래밍
멀티프로그래밍은 메모리에 여러 개의 프로세스가 올라온 것을 말한다.

### 멀티프로세싱
유니프로그래밍과 멀티프로그래밍은 메모리의 관점으로 정의했다면 

멀티 프로세싱은 CPU관점으로 정리한 것이다.

멀티프로세싱은 CPU가 여러 개의 프로세스를 처리하는 것을 말한다.

**오늘날 OS는 멀티프로그래밍과 멀티프로세싱 두 개가 공존한다.**

메모리에는 여러 개의 프로세스가 올라오는 멀티프로그래밍이 있고

시분할 처리로 CPU가 각각의 프로세스를 짧은 시간 동안 교대로 실행하는 멀티프로세싱이 있다.

과거에는 메모리의 크기가 작아서 멀티프로그래밍이 불가능 했다.

이때는 유니프로그래밍을 하면서 멀티프로세싱을 이용했다.

메모리에 프로세스를 올려서 CPU로 처리를 하고 이 프로세스를 다른 저장장치에 저장한다.

그리고 다른 저장장치에 있던 프로세스를 메모리에 올려서 CPU로 처리하는 멀티프로세싱 기법을 사용했습니다.

이때 메모리에 있는 데이터를 다른 저장장치로 보내고 다른 저장장치에서 메모리에 올리는 것을 스와핑이라고 한다.


