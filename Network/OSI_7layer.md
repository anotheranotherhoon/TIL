# OSI 7계층 모델
* OSI 7계층 모델은 ISO(International Organization for Standardization)라고 하는 국제표준화기구에서 1984년에 제정한 표준 규격이다.

* OSI 7계층 모델은 네트워크를 이루고 있는 구성요소들을 7단계로 나누고, 각 계층의 표준을 정하였다. 
* OSI 7계층 모델의 목적은 표준화를 통하여 포트, 프로토콜의 호환 문제를 해결하고, 네트워크 시스템에서 일어나는 일을 해당 계층 모델을 이용해 쉽게 설명할 수 있다. 
* 또한 네트워크 관리자가 문제가 발생 했을 때 이것이 물리적인 문제인지, 응용 프로그램과 관련이 있는지 등 원인이 어디에 있는지 범위를 좁혀 문제를 쉽게 파악할 수 있다. 

|OSI 7 계층|종류|
|------|---|
|응용 계층|HTTP, DNS, SSL, SMTP, FTP|
|표현 계층|GIF, JPEG, MPEG, MIME, ZIP, ASCII|
|세션 계층|RPC, SQL, NETBOIS, Sockets|
|전송 계층|TCP, UDP, NETBEUI|
|네트워크 계층|IP, ICMP|
|데이터 링크 계층|FDDI, Ethernet, PPP|
|물리 계층|CDMA, GSM, NICs, CSMA/CD, Fiber|

## 계층의 분류

* 1계층 - 물리 계층 : 
  * OSI 모델의 맨 밑에 있는 계층으로서, 시스템 간의 물리적인 연결과 전기 신호를 변환 및 제어하는 계층이다. 
  * 주로 물리적 연결과 관련된 정보를 정의한다. 
  * 주로 전기 신호를 전달하는데 초점을 두고, 들어온 전기 신호를 그대로 잘 전달하는 것이 목적이다.
  * ex) 디지털 또는 아날로그로 신호 변경

* 2계층 - 데이터링크 계층 :
  * 네트워크 기기 간의 데이터 전송 및 물리주소<sup>ex) MAC 주소</sup> 를 결정하는 계층dl다. 
  * 물리 계층에서 들어온 전기 신호를 모아 알아 볼 수 있는 데이터 형태로 처리한다. 
  * 이 계층에서는 주소 정보를 정의하고 출발지와 도착지 주소를 확인한 후, 데이터 처리를 수행한다.
  * ex) 브리지 및 스위치, MAC 주소

* 3계층 - 네트워크 계층 :
  *  OSI 7 계층에서 가장 복잡한 계층 중 하나로서 실제 네트워크 간에 데이터 라우팅을 담당한다. 
  *  이때 라우팅이란 어떤 네트워크 안에서 통신 데이터를 짜여진 알고리즘에 의해 최대한 빠르게 보낼 최적의 경로를 선택하는 과정을 라우팅이라고 한다.
  * ex) IP 패킷 전송

* 4계층 - 전송 계층 :
  * 컴퓨터간 신뢰성 있는 데이터를 서로 주고받을 수 있도록 하는 서비스를 제공하는 계층이다. 
  * 하위 계층에서 신호와 데이터를 올바른 위치로 보내고 신호를 만드는데 집중했다면, 전송 계층에서는 해당 데이터들이 실제로 정상적으로 보내지는지 확인하는 역할을 한다. 
  * 네트워크 계층에서 사용되는 패킷은 유실되거나 순서가 바뀌는 경우가 있는 데, 이를 바로 잡아주는 역할도 담당한다.
  * ex) TCP/UDP 연결

* 5계층 - 세션 계층 :
    * 세션 연결의 설정과 해제, 세션 메시지 전송 등의 기능을 수행하는 계층이다. 
    * 즉, 컴퓨터간의 통신 방식에 대해 결정하는 계층이라고 할 수 있다. 
    * 쉽게 말해, 양 끝 단의 프로세스가 연결을 성립하도록 도와주고, 작업을 마친 후에는 연결을 끊는 역할을 한다.

* 6계층 - 표현 계층 : 
    * 응용 계층으로 전달하거나 전달받는 데이터를 인코딩 또는 디코딩하는 계층이다. 
    * 일종의 번역기 같은 역할을 수행하는 계층이라고 볼 수 있다.
    * ex) 문자 코드, 압축, 암호화 등의 데이터 변환

* 7계층 - 응용 계층 :
    * 최종적으로 사용자와의 인터페이스를 제공하는 계층으로 사용자가 실행하는 응용 프로그램(e.g. Google Chrome)들이 해당 계층에 속한다.
    * ex) 이메일 및 파일 전송, 웹 사이트 조회

## 데이터 캡슐화
* OSI 7계층 모델은 송신 측의 7계층과 수신 측의 7계층을 통해 데이터를 주고 받는다. 
* 각 계층은 독립적이므로 데이터가 전달되는 동안에 다른 계층의 영향을 받지 않는다.

* 데이터를 전송하는 쪽은 데이터를 보내기 위해서 상위 계층에서 하위 계층으로 데이터를 전달한다. 
* 이때 데이터를 상대방에게 보낼 때 각 계층에서 필요한 정보를 데이터에 추가하는데 이 정보를 헤더(데이터링크 계층에서는 트레일러)라고 한다. 
* 그리고 이렇게 헤더를 붙여나가는 것을 캡슐화라고 합니다.

* 마지막 물리 계층에 도달하며 송신 측의 데이터링크 계층에서 만들어진 데이터가 전기 신호로 변환되어 수신 측에 전송된다.

* 데이터를 받는 쪽은 하위 계층에서 상위 계층으로 각 계층을 통해 전달된 데이터를 받게된다. 
* 이때 상위 계층으로 데이터를 전달하며 각 계층에서 헤더(데이터링크 계층에서는 트레일러)를 제거해 나가는 것을 역캡슐화라고 한다. 
* 역캡슐화를 거쳐 마지막 응용 계층에 도달하면 드디어 전달하고자 했던 원본 데이터만 남게 된다.