# 1. CORS, SOP

* SOP은 Same-Origin-Policy의 줄임말로, 동일 출처 정책을 뜻한다.
> "같은 출처의 리소스만 공유가 가능하다"라는 정책이다. 여기서 말하는 '출처(Origin)'는 다음과 같다.

* 출처는 프로토콜, 호스트, 포트의 조합으로 되어있다. 
* 이 중 하나라도 다르면 동일한 출처로 보지 않는다.

* https:// www.codestates.com:443/course에서

* https:// 프로토콜
* www.codestates.com:443 호스트
* :443 포트
* https:// www.codestates.com:443/ 출처

* `https://www.codestates.com` vs `http://www.codestates.com` => 두 URI는 프로토콜이 다르기 때문에 동일 출처가 아니다.

*  `https://urclass.codestates.com` vs `https://codestates.com`
    * => 두 URI는 호스트가 다르기 때문에 동일한 출처가 아니다.

* `http://codestates.com:81` vs `http://codestates.com`
    * http 프로토콜의 기본 포트는 80이다.
    * => 두 URI는 포트가 다르기 때문에 동일한 출처가 아니다.(:81 / :80)

* `https://codestates.com:443` vs `https://codestates.com`
    * https 프로토콜의 기본 포트는 443입니다.
    * => 두 URI은 프로토콜, 호스트, 포트가 모두 같은 동일한 출처이다.

## 1.1 SOP는 왜 생겨나게 되었을까?

* 동일 출처 정책은 잠재적으로 해로울 수 있는 문서를 분리함으로써 공격받을 수 있는 경로를 줄여준다.

* SOP를 통해 해킹 등의 위협에서 보다 더 안전해질 수 있다.


* SOP는 애초에 다른 사이트와의 리소스 공유를 제한한다. 따라서 타 사이트의 코드에 의해서 새어나가는 것을 방지 할 수 있다.

* 이러한 보안상의 이점 때문에 SOP는 모든 브라우저에서 기본적으로 사용하고 있는 정책이다.

## 1.2 다른 출처의 리소스를 받아오는 방법 CORS
* CORS는 Cross-Origin Resource Sharing의 줄임말로 교차 출처 리소스 공유를 뜻한다.

* 교차 출처 리소스 공유(CORS)는 추가 HTTP헤더를 사용하여, 한 출처에서 실행중인 웹 애플리케이션이 다른 출처의 선택한 자원에 접근할 수 있는 권한을 부여하도록 브라우저에게 알려주는 체제다. 

```
 Access to fetch at ‘https://api.lubycon.com/me’ from origin ‘http://localhost:3000’ has been blocked by CORS policy: No ‘Access-Control-Allow-Origin’ header is present on the requested resource. If an opaque response serves your needs, set the request’s mode to ‘no-cors’ to fetch the resource with CORS disabled.
```
* 위와 같은 에러의 의미
* 다른 출처의 리소스를 가져오려고 했지만 SOP 때문에 접근이 불가능하다. CORS설정을 통해 서버의 응답 헤더에 'Access-Control-Allow-Origin'을 작성하면 접근 권한을 얻을 수 있다.

* 즉, 이 에러는 CORS 때문이 아니라 SOP때문이다. CORS는 에러를 해결할 수 있는 방안이었다.

## 2. CORS 동작 방식

## CORS의 동작 방식 세 가지

## 1. 프리플라이트 요청(Preflight Request)
    * (1) 실제 요청을 보내기 전, OPTION 메서드로 사전 요청을 보내 해당 출처 리소스에 대한 접근 권한이 있는지 확인하는 것을 프리플라이트 요청이라고 한다.
    * (2-1) 응답 헤더의 Access-Control-Origin으로 요층을 보낸 출처가 돌아오면 실제 요청을 보낸다.
    * (2-2) 만약 요청을 보낸 출처가 접근 권한이 없다면 브라우저에서 CORS 에러를 띄우게 되고, 실제 요청은 전달되지 않는다.
> 프리플라이트 요청은 왜 필요할까?
> 1. 실제 요청을 보내기 전에 미리 권한 확인을 할 수 있기 때문에, 실제 요청을 처음 부터 통째로 보내는 것 보다 리소스 측면에서 효율적이다.
> 2. CORS에 대비가 되어있지 않은 서버를 보호할 수 있다. CORS이전에 만들어진 서버들은 SOP요청만 들어오는 상황을 고려하고 만들어졌다. 따라서 다른 출처에서 들어오는 요청에 대한 대비가 되어있지 않았습니다. 이런 서버에 요청을 보내면, 응답을 보내기 전에 우선 요청을 처리하게 된다. 브라우저는 응답을 받은 후에야 CORS 권한이 없다는 것을 인지하지만, 브라우저가 에러를 띄운 후에는 이미 요청이 수행된 상태가 된다. 만약에 들어온 요청이 DELETE나 PUT처럼 서버의 정보를 삭제하거나 수정하는 요청이었다면 데이터가 변하게된다.

## 2. 단순 요청(Simple Request)

* 단순 요청은 특정 조건이 만족되면 프리플라이트 요청을 생략하고 요청을 보내는 것을 말한다.

* 특정 조건은 다음과 같다. 하지만 이 조건들을 모두 만족시키기는 어려우므로, 참고만 하자
    * GET, HEAD, POST 요청 중 하나여야 한다.
    * 자동으로 설정되는 헤더 외에 Accept, Accept-Language, Content-Language, Content-Type 헤더의 값만 수동으로 설정할 수 있다.
        * Content-Type 헤더에는 application/x-www-form-urlencoded, multipart/form-data, text/plain 값만 허용된다.

## 3. 인증정보를 포함한 요청(Credentialed Request)

* 요청 헤더에 인증 정보를 담아 보내는 요청입니다. 

* 출처가 다를 경우에 별도의 설정을 하지 않으면 쿠키를 보낼 수없다.

* 민감한 정보이므로 프론트, 서버 양측 모두 CORS 설정이 필요하다.
     * 프론트 측에서는 요청 헤더에 withCredentials : true 를 넣어줘야한다.
     * 서버 측에서는 응답 헤더에 Access-Control-Allow-Credentials : true 를 넣어줘야 한다.
     * 서버 측에서 Access-Control-Allow-Origin 을 설정할 때, 모든 출처를 허용한다는 뜻의 와일드카드(*)로 설정하면 에러가 발생한다. 인증 정보를 다루는 만큼 출처를 정확하게 설정해주어야 한다.