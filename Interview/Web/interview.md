## 1. 브라우저 렌더링 (작동) 원리에 대해 설명하세요.

## 2. Client Side Rendering 과 Server Side Rendering 의 차이에 대해서 설명하세요.
1. 클라이언트 사이드 렌더링은

CSR은 사용자의 요청에 따라 필요한 부분만 응답을 받아와 렌더링 하는 방식입니다.

CSR의 장점으로 첫째 필요한 만큼, 변경된 만큼만 받아서 변경하기 때문에 속도가 빠르고, 트래픽을 감소 시킬수 있습니다, 두번째는 새로고침이 발생하지 않아 우수한 사용자 경험을 제공합니다.
단점으로는 검색엔진최적화가 좋지 않다는 단점이 있습니다.
CSR을 채택한 SPA는 자바스크립트를 사용하여 사용자와 상호작용 후에 페이지 내용을 로드하기 때문에 웹 크롤러가 접근 할 수 없어 검색사이트에 노출되지 않습니다.

2. 서버 사이드 렌더링은 사용자가 웹 페이지에 접근할 때, 서버로부터 완전하게 만들어진 html파일은 받아와 페이지 전체를 렌더링하는 방식입니다.

장점 ssr은 서버로부터 화면을 렌더링 하기 위한 필수적인 요소를 먼저 가져 오기 때문에 CSR보다 초기 로딩속도가 빠르다. , 이로 인해 검색엔진이 웹을 크롤링할 경우 화면을 구성하는 각각의 페이지가 있기 때문에 검색엔진 최적화에 유리하다.

단점 매번 페이지를 요청할 때마다 새로고침 되기 때문에 사용자 경험이 떨어진다.
페이지를 요청할 때마다 서버에서 페이지를 구성하는 모든 리소스를 준비해서 응답하므로 서버 부담이 증가한다.

## 3. AJAX에 대해 설명해주세요.

## 4. HTTP 프로토콜에 대해 설명해주세요.

## 5. URL과 URI의 차이점이 무엇인가요?

## 6. REST API란 무엇인가요?

## 7. CORS에 대해 설명해주세요. 

## 8. SOP과 same origin에 대해 설명해주세요. 

## 9. Session과 Cookie 그리고 Token 인증방식에 대해 설명해주세요. 

## 10. 