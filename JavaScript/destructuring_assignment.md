# 디스트럭처링 할당 (구조 분해 할당)

## 0. 구조 분해 할당
```js
let [firstName, lastName] = "방원 이".split(' ');
console.log(firstName); // 방원
console.log(lastName); // 이
```
* 분해(destructuring)는 파괴(destructive)를 의미하지 않는다.
    * 구조 분해 할당이란 명칭은 어떤 것을 복사한 이후에 변수로 '분해(destructurize)'해준다는 의미 때문에 붙여졌다.
    * 이 과정에서 분해 대상은 수정 또는 파괴되지 않는다. 원본이 바뀌지 않는다.


## 1. 배열 구조 분해 할당
* 디스트럭처링 할당<sup>destructuring assignment</sup>(구조 분해 할당)은 구조화된 배열과 같은 이터러블 또는 객체를 destructuring(비구조화, 구조 파괴)하여 1개 이상의 변수에 개별적으로 할당하는 것을 말한다. 

* ES6의 배열 구조 분해 할당은 배열의 각 요소를 배열로부터 추출하여 1개 이상의 변수에 할당한다.

* 이떄 배열 구조 분해 할당의 대상(할당문의 우변)은 이터러블이어야 하며, 할당 기준은 배열의 인덱스다. 

* 즉, 순서대로 할당된다.

* 배열 디스트럭처링 할당을 위해서는 할당 연산자 왼쪽에 값을 할당받을 변수를 선언해야 한다. 

* 이때 변수를 배열 리터럴 형태로 선언한다.

```js
const [x, y] = [1, 2]
```
* 이때 우변에 이터러블을 할당하지 않으면 에러가 발생한다.

* 배열 디스트럭처링 할당의 변수 선언문은 다음처럼 선언과 할당을 분리할 수도 있다. 

* 이 경우 const는 재할당이 불가능 하므로 let으로 선언한 경우만 가능하다.

```js
let x, y;
[x, y] = [1, 2]
```

* 배열 디스트럭처링의 기준은 배열의 인덱스다. 즉, 순서대로 할당한다. 

* 이때 변수의 개수와 이터러블의 요소 개수가 반드시 일치할 필요는 없다. 

```js
const [c, d] = [1];
console.log(c, d) = 1 undefined

const [e, f] = [1, 2, 3,]
console.log(e, f); / 1 2 

const [g, , h] = [1, 2, 3]
console.log(g, h); 1 3
```

* 배열 구조 분해 할당을 위한 변수에 기본값을 설정할 수 있다.
```js
const [a, b, c=3] = [1, 2];
console.log(a, b, c); 1 2 3
const [d, e=10, f=3] = [1, 2]
console.log(d, e, f) = 1 2 3
```

* 배열 구조 분해 할당은 배열과 같은 이터러블에서 필요한 요소만 추출하여 변수에 할당하고 싶을 떄 유용하다. 

* 배열 구조 분해 할당을 위한 변수에 Rest 파라미터와 유사하게 Rest 요소<sup>Rest element</sup> ...을 사용할 수 있다.

* Rest 요소는 Rest 파라미터와 마찬가지로 반드시 마지막에 위치해야한다. 나머지 요소의 오른쪽 뒤에 쉼표가 있으면 syntaxError가 발생한다. 

```js
const [x, ...y] = [1, 2, 3]
console.log(x, y) = 1. [2, 3]
```

## 구조 분해 할당을 통한 변수 값 교환하기
```js
let a = 1;
let b = 3;
[a, b] = [b, a]
console.log(a) // 3 
console.log(b) // 1
```

## 객체 구조 분해 할당

* ES5에서 객체의 각 프로퍼티를 객체로 부터 디스트럭처링하여 변수에 할당하기 위해서는 프로퍼티 키를 사용해야 한다. 

```js
let user = { firstName : '방원', lastName : '이'};
let firstName = user.firstName;
let lastName = user.lastName;
```

console.log(firstName, lastname); // 방원 이

* ES6의 객체 구조 분해 할당은 객체의 각 프로퍼티를 객체로 부터 추출하여 1개 이상의 변수에 할당한다. 

* 이때 객체 구조 분해 할당의 대상(할당문의 우변)은 객체이어야 하며, 할당 기준은 프로퍼티 키다. 

* 즉, 순서가 의미가 없으며 선언된 변수 이름과 프로퍼티 키가 일치하면 된다.

```js
const user = {firstName : '방원', lastName : '이'};
const {lastName, firstName} = user;

console.log(firstName, lastName); // 방원 이
```

```js
const {lastName, firstName} = user;

const {lastName : laseName, firstName : firstName} = user
```
> 참고 모던자바스크립트DeepDive, [모던JavaScript튜토리얼](https://ko.javascript.info/destructuring-assignment)