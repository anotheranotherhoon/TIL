# Rest and arguments 
>2022년05월17일

# 기본 문법

- Rest 파라미터(나머지 매개변수)는 매개변수 이름 앞에 세개의 점 ... 을 붙여서 정의한 매개변수를 의미한다.

- Rest 파라미터는 함수에 전달된 인수들의 목록을 배열로 전달받는다.

```
function foo(...rest){
	console.log(rest); // [1, 2, 3, 4, 5]
}

foo(1, 2, 3, 4, 5)
```

- 일반 매개변수와 Rest 파라미터는 함께 사용할 수 있다. 이때 함수에 전달된 인수들은 매개변수와 Rest 파라미터에 순차적으로 할당된다.

```
function foo(param, ...rest){
	console.log(param); // 1
    console.log(rest); // [2, 3, 4, 5]
}
foo(1, 2, 3, 4, 5)
```

- Rest 파라미터는 이름 그대로 먼저 선언된 매개변수에 할당된 인수를 제외한 나머지 인수들로 구성된 배열이 할당된다. 

- 따라서 Rest 파라미터는 반드시 마지막 파라미터이어야 한다.

- Rest 파라미터는 단 하나만 선언할 수 있다.

- Rest 파라미터는 함수 정의 시 선언한 매개변수 개수를 나타내는 함수 객체의 lengh 프로퍼티에 영향을 주지 않는다.

# Rest 파라미터와 arguments 객체

- arguments 객체는 함수 호출 시 전달된 인수들의 정보를 담고 있는 순회 가능한 유사배열 객체 이며 함수 내부에서 지역 변수처럼 사용할 수 있다.

```
function sum() {
	console.log(arguments);
}
sum(1,2); // {lengthL 2, '0' : 1, '1' : 2}
```

- 하지만 arguments 객체는 배열이 아닌 유사 배열 객체이므로 배열 메서드를 사용하려면 
Function.prototype.call 이나 Function.prototype.apply 메서드를 사용해 arguments 객체를 배열로 변환해야한다.

- ES6에서는 rest 파라미터를 사용하여 가변 인자 함수의 인수 목록을 배열로 직접 전달 받을 수 있다.

- 하지만 화살표 ㅎㅁ수는 함수 자체의 arguments 객체를 가지지 않는다.

- 따라서 화살표 함수로 가변 인자 함수를 구현해야 할 때는 반드시 Rest 파라미터를 사용해야 한다.


