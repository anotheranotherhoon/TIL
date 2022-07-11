## Express 미들웨어를 사용하는 상황
* 모든 요청에 대해 url이나 메서드를 확인 할 때
* POST 요청 등에 포함된 body(payload)를 구조화 할 떄
* 모든 요청/응답에 CORS 헤더를 붙여야 할 떄


## 미들웨어란 ?
* http의 과정은 요청과 응답이 있다.
* 요청과 응답에서 express는 미들웨어가 있다.
* 요청과 응답 사이에 중간 중간에 미들웨어가 있다.
* cors, experss.json, 

## JSON at position at JSON.parse(<anonymous>) 에러가 뜨는 이요?
* JSON형식이 아닌 것을 파싱하려고해서 에러가 난다.

## express.json(strict: true) 일 경우
* 배열과 객체만 받겠다. strict : false 일 경우 어떤 것이든 받겠다.

## JSON.stringify 대신 쓰는게 res.json()

## app.use를 라우터 분기할 때도 쓴다.
 query parameter
 path parameter
 
