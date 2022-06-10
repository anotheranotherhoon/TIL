# useState

## 1. useState와 사용법(구조분해할당)
```
import React, { useState } from "react";
//useState라는 내장 함수를 쓰겠다.
```
* useState('초기 값') array가 남는다. 그 데이터 안에는 두 개의 데이터가 들어있다. [a, b]

* a 에는 '초기 값' 이 그대로 들어가 있다.

* b 에는 데이터(a)를 수정하기 위한 함수가 들어가 있다.

```
// ES6 Destructuring문법 (구조 분해 할당 문법)

let a, b = [1, 2];

console.log(a)/// 1
console.log(b)/// 2

const [data, setData] = useState("hello")

data 에는 "hello"가 들어가 있고
setData 에는 data를 변경하는 함수가 생성되어있다. 
```

## 1. state 특징
1. state는 변수 대신 쓰는 데이터 저장 공간이다.
2. useState()를 사용해 만들어야한다.
3. String, Number, array, Object, Boolean등 모두 저장가능하다

## 2. state의 장점
> 변수를 쓰면 되는데 왜 굳이 state를 써야 할까?
1. 웹이 App처럼 동작하게 만들고 싶어서 사용한다. 
* state는 값이 변경이 될 때, 데이터를 담고 있는 html이 자동으로 즉시 재렌더링된다. 새로 고침없이도 페이지를 재렌더링해준다.
    * 렌더링이되는 조건은 주솟값이 바뀌어야한다.  set에 주솟값이 바뀌면 다시 렌더링된다.

* 변수에 할당된 값이 바뀌어도, html이 재렌더링이 되지 않고 **새로 고침**이 된다.

> 따라서 HTML이 새로고침 없이도 자연스럽게 변경되는 사용자 경험을 제공할 수 있다.

> 그러므로 자주 바뀌는 중요한 데이터는 변수 말고 state로 저장해서 사용해야한다.
