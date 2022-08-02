> 그림으로 쉽게 배우는 운영체제 - 감자님 강의 참조

모니터는 세마포어의 단점을 해결한 상호 배제 메커니즘이다.

모니터는 따로 운영체제가 처리하는 것이 아니라 프로그래밍 언어 차원에서 지연하는 방법이다.

대표적으로 자바에서 모니터를 지원한다.

```
public class Health
{
  private int health = 100;
  
  synchrnized void increase(int amount)
  {
  health += amount;
  }
  synchronized void decrease(int amount)
  {
  health -= amount;
  }
}

```
자바에서 synchronized 키워드가 붙으면 이 키워드가 붙은 함수들은 동시에 여러 프로세스에서 실행시킬 수 없다. 즉, 완벽하게 상호 배제가 이루어진다.

만약 프로세스 A에서 increase()함수를 실행한다면
프로세스 B에서는 increase()함수 뿐 아니라 synchronized가 붙은 decrease()함수도 실행할 수 없다.

모니터의 구현만 완벽하다면 프로그래머는 세마포어 처럼 wait() 함수나 signal()함수를 임계영역에 감싸지 않아도 되서 편리하고 안전하게 코드를 작성할 수 있다.