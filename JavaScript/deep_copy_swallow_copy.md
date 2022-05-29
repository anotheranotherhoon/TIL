# 깊은  복사 얕은 복사
> 2022년 05월 022일 (일)
## 1. 얕은 복사 Shallow copy
* 자바스크립트에서 원시 값이 아닌 값을 할당한 변수를 다른 변수에 할당할 경우 같은 메모리 주소를 할당 받아 얕은 복사가 일어난다.
```
let obj = {
    name : "lee",
    age : 20
};

let objCopy = obj;
objCopy.age = 30;

console.log(obj, objCopy);
//{name: "lee", age: 30} {name: "lee", age: 30}
```
* 따라서 할당은 얕은 복사이다.
* 
*

## 2. 깊은 복사 Deep copy

### 2-1. 중간 복사

#### 2-1-1 spread 연산자를 사용하는 방법
* ...obj
```
let obj = {
    name : "lee",
    age : 20
};

let spreadObj = {...obj};
spreadObj.age = 30;

console.log(obj, objCopy);
/*
{name: "lee", age: 20} {name: "lee", age: 10}
*/

```

#### 2-1-2 Object.assign() 메서드를 사용하는 방법
> 출처 https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object/assign mbd Object.assign

* Object.assign() 메서드는 출처 객체들의 모든 열거가능한 프로퍼티를 복사해 대상 객체에 붙여 넣는다. 그후 대상 객체를 반환한다.

* Object.assign(target, sources)

* 매개변수 target, sources 

* target 목표 객체, 출처 객체의 프로퍼티를 복사해 반영한 후 반환할 객체이다.

* sources 출처객체, 목표 객체에 반영하고자 하는 속성들을 갖고 있는 객체이다.

```
let obj = {
    name : "lee",
    age : 20
};

let assignObj = Object.assign({}, obj);
assignObj.age = 30;

console.log({obj}, {assignObj});
/* 
{ name : "lee", age : 20} 
{ name : "lee", age : 30}
*/
```
## 하지만 spread 연산자 Object.assign() 메서드도 깊이가 1까지인 경우에만 깊은 복사가 일어난다 따라서 중간복사라고 하겠다.

하지만 객체 안에 다른 객체가 존재할 경우에는 객체 안의 객체 까지 복사하지 못한다.

```
let obj = {
    name : "lee",
    age : 20,
    friend : ["kim", "park", "son"] 
};

let spreadObjFriend = {...obj}
spreadObjFriend.age = 30
spreadObjFriend.friend[0] = "choi"
console.log(obj, spreadObjFriend);
/* 
{ 
    name : "lee", 
    age : 20, 
    friend : ["choi", "park", "son"] ,
} 

{ 
    name : "lee", 
    age : 30, 
    friend : ["choi", "park", "son"] ,
}
*/
```

* assign의 경우에도 마찬가지다.

```
let obj = {
    name : "lee",
    age : 20,
    friend : ["kim", "park", "son"] 
};

let assignObjFriend = Object.assign({}, obj)
assignObjFriend.age = 30
assignObjFriend.friend[0] = "choi"
console.log(obj, assignObjFriend);
// { name : "lee", age : 20, friend : ["choi", "park", "son"] } { name : "lee", age : 30, friend : ["choi", "park", "son"] };
```

## 완벽하게 복사하는 방법

### JSON.stringify 와 JSON.parse를 사용하기

```
let obj = {
    name : "lee",
    age : 20,
    friend : ["kim", "park", "son"] 
};

const perfectCopy = JSON.parse(JSON.stringify(obj));
perfectCopy.age = 30
perfectCopy.friend[0] = 'choi'

console.log(obj, perfectCopy);
/* 
{
    name : "lee", 
    age : 20, 
    friend : ["choi", "park", "son"],
} 

{ 
    name : "lee", 
    age : 30, 
    friend : ["choi", "park", "son"] ,
};
*/
```
* 깊이가 1 뿐만 아니라 더 깊을 경우에도 완벽하게 복사할 수 있다.

```
let obj = {
    name : "lee",
    age : 20,
    friend : ["kim", "park", "son"] ,
    family : {
        parents : ["lee", "ryu"]
    }
};
const perfectCopy = JSON.parse(JSON.stringify(obj));
perfect.age = 30
perfect.friend[0] = 'choi'
perfect.family.parents[1] = "koo"
console.log(perfectCopy);
/*
{
    name : "lee", 
    age : 20, 
    friend : ["choi", "park", "son"],
    family{
        parents:["lee", "ryu"]
        }
}

{ 
    name : "lee", 
    age : 30, 
    friend : ["choi", "park", "son"], 
    family{
        parents:["lee", "koo"]
        }
}
*/
```


```
let obj = {
    name : "lee",
    age : 20,
    friend : ["kim", "park", "son"] ,
    family : {
        parents : ["lee", "ryu"]
    }
};

lodash의 cloneDeep을 사용한 깊은 복사
// npm install lodash 설치 한 후 , Node.js환경에서 실행
const _ = require('lodash');
//깊은 복사
const c2 = _.clone(obj);
console.log(c2 === obj); //false
consoel.log(c2.name === o.name)//false
```

## 요약
* 가장 얕은 복사 : 할당
* 중간 복사 : ...spread, Object.assign()
* 완전한 복사 : JSON.parse(JSON.stringify(obj)) 자바스크립트 객체를 JSON문자열로 바꾸고 다시 자바스크립트 객체로 만들기
