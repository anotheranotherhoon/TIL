## IP와 IP Packet
* 인터넷 망 속 수많은 노드(서버)들을 지나 어떻게 클라이언트와 서버가 통신할 수 있는가?
* 출발지에서 목적지까지 데이터가 무사히 전달되기 위해서 규칙이 필요하지 않을까?

* IP 패킷에서 패킷은 pack과 bucket이 합쳐진 단어로 소포뢰 비유할 수 있다.
* IP 패킷은 이를 데이터 통신에 적용한 것이라 보면 된다.
* IP 패킷은 우체국 송장처럼 전송데이터를 무사히 전송하기 위해 출발지 IP, 목적지 IP와 같은 정보가 포함되어 있다. 
* 패킷 단위로 전송하면 노드(서버)들은 목적지 IP에 도착하기 위해 서로 데이터를 전달한다.
* 이를 통해 인터넷 망 사이에서도 정확한 목적지로 패킷을 전송할 수 있다.
* 서버에서 무사히 데이터를 전송받는다면 서버도 이에 대한 응답을 돌려줘야 한다.
* 서버 역시 IP 패킷을 이용해 클라리언트에 응답을 전달한다.
* 정확한 출발지와 목적지를 파알할 수 있다는 점에서 IP프로토콜은 적절한 통신 방법으로 보이지만 이러한 IP 프로토콜에도 한계가 존재한다.

## IP프로토콜의 한계
- 비연결성
    - 패킷을 받을 대상이 없거나 서비스 불능 상태여도 패킷 전송
- 비신뢰성
  - 중간에 패킷이 사라질 수 있음
  - 패킷의 순서를 보장할 수 없음

### 비연결성
* 패킷을 받을 대상이 없거나 서비스 불능 상태여도 클라이언트는 서버의 상태를 파악할 방법이 없기 때문에 패킷을 그대로 전송하게 된다.

## 비신뢰성
* 중간에 있는 서버가 데이터를 전달하던 중 장애가 생겨 패킷이 소실되더라도 클라이언트는 이를 파악할 방법이 없다.
* 전달 데이터의 용량이 클 경우 이를 패킷 단위로 나눠 데이터를 전달하게 되는데 이때 패킷들은 중간에 서로 다른 노드(서버)를 통해 전달 될 수 있다. 
* 이렇게 되면 클라이언트가 의도하지 않은 순서로 서버에 패킷이 도착할 수 있다.