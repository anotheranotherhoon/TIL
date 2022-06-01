# Unit3 비동기 

## 동기
* 하나의 작업이 온전히 끝나야 다음 작업이 진행되는 방식

## 비동기
* 하나의 작업이 온전히 끝나지 않아도 다음 작업이 진행되는 방식
* 동시다발적인 업무 처리가 쉽다.
---
## 1. 라이브 세션
```
1번
const sleep = (wait) => {
  return new Promise((resolve) => {
    setTimeout(resolve, wait);
  });
}
2번
const sleep = (wait) => {
  return new Promise((resolve) => {
    setTimeout(() => {
      resolve('hello');
    }, wait);
  });
};
```
* 두 함수의 차이는 2번은 resolve('hello')에 의해 then으로 'hello'를 넘긴다.

```
1번
function runPromise() {
  resetTitle();
  playVideo();

  sleep(1000)
  .then(() => {
    pauseVideo();
    displayTitle();
  })
    .then(sleep.bind(null, 500))
    .then(highlightTitle)
    .then(sleep.bind(null, 2000))
    .then(resetTitle)
}

2번
function runPromise() {
  resetTitle();
  playVideo();

  sleep(1000)
    .then((param) => {
      console.log(param);
      pauseVideo();
      displayTitle();
      return "world";
    })
    .then((param) => {
      console.log(param);
      return sleep(5000);// return에 의해 then으로 전달된다.
    })
    .then(highlightTitle)
    .then(sleep.bind(null, 2000))
    .then(resetTitle);
}

```
* return 을 안하면 then에 undefined가 들어간다. (프로미스 다음 then은 리턴한 결과를 받는다)

* 따라서 5초를 기다리지 않고 동기적으로 실행된다.

---
## 2.정리

## callback을 쓰는 이유
* 실행 순서를 제어하기 위해 콜백을 썼다. 

## Promise의 세 가지 상태
* pending, fulfilled, rejected

## Promise 실행 함수가 가지고 있는 두 개의 파라미터 resolve, reject는 각각 무엇을 의미하는가?
* resolve되면 then을 따라가고
* reject되면 catch를 따라간다.

## Promise.prototype.catch
* catch를 하면 rejected를 fulfiled로 만들어 에러를 없앤다.
* reject를 catch로 안잡으면 rejected와 함꼐 에러를 발생시킨다.

## Promise.prototype.then 메서드는 무엇을 리턴하는가?
* then 자체는 항상 Promise를 리턴한다.
* then 자체는 Promise를 리턴하지만 resolve값을 이용하기 위해서는 꼭 return을 해줘야한다. 

## then() 안에서 undefined가 리턴되어도 이후의 then 체이닝이 계속 이루어진다.
* then은 항상 Promise를 리턴하므로 체이닝이 가능하다.

## await 키워드 다음에 등장하는 함수 실행은 어떤 타입을 리턴할 경우에만 의미가 있는가?
* Promise 타입을 리턴할 경우에만 의미가 있다. 

## await 키워드를 사용할 경우, 어떤 값이 리턴되는가?
* 결과 값이 담긴다. 
* await를 변수에 할당해야 결과값을 담을 수 있다.

## await 다음에 오는 함수에는 체이닝이 안되는가?
* await는 then이랑 똑같은데 보다 일반적인 코드 처럼 짤 수 있다.
* then 이용시 보다 간단하게 이용 할 수 있다. 
* 체이닝을 할 경우 에는 then을 사용한다.
