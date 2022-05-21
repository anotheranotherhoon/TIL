참고 : https://www.youtube.com/watch?v=ocGc-AmWSnQ

### var let
1. var는 한번 선언된 변수를 다시 선언할 수 있다.
```
var name = 'Mike';
console.log(name); // Mike

var name = 'Jane';
console.log(name); //Jane
```
let은 한번 선언한 변수를 다시 선언할 경우. 문제가 발생한다.
```
let name = 'Mike';
console.log(name); Mike

let name = 'Jane'; error!
console.log(name); 
```

2. var는 선언하기 전에 사용할 수 있다.
```
console.log(name); // undefined
var name = 'Mike'
```
위의 식은 아래식과 같다.
```
var name;
console.log(name); // undefined
name = 'Mike'; 
```
var로 선언한 변수는 코드가 실제로 이동하지는 않지만 최상위로 끌어올려진 것 처럼 동작한다 이를 호이스팅(hoisting)이라 한다.
선언은 호이스팅 되지만 할당은 호이스팅 되지 않기 때문에 undefined가 출력된다. 


같은 상황에서 let은 에러가 난다.
```
console.log(name); // ReferenceError
let name = 'Mike';
```
### 호이스팅
let과 const도 호이스팅 된다.
호이스팅 : 스코프 내부 어디서든 변수선언은 최상위에 선언된 것 처럼 행동한다는 뜻이다.

**Temporal Dead Zone**

![](https://github.com/anotheranotherhoon/TIL/blob/master/JavaScript/img/tdz.png?raw=true)
TDZ에 있는 녀석들은 사용할 수 없다.
let과 const는 TDZ의 영향을 받는다. 따라서 할당을 하기 전에는 사용을 할 수 없다. 이는 코드를 예측 가능하게 하고 잠재적인 버그를 줄일 수 있다. 

```
현재 이 코드는 문제가 없다.
let age = 30;
function showAge() {
	console.log(age)
}
showAge();

하지만 이렇게 할 경우 문제가 발생한다. 

let age = 30;
function showAge() {
	console.log(age);
    let age = 20; // 문제를 일으킨다.
}
showAge();
```

많은 사람들이 let은 호이스팅 되지 않는거라고 오해한다. 하지만 그것이 아니다.
호이스팅은 스코프 단위로 일어난다. 여기서 스코프는 함수 내부를 말한다.

![](https://velog.velcdn.com/images/anotherhoon/post/0641fc14-2595-4820-bf7a-d05c69622a05/image.png)

let으로 선언한 두번째 age 변수가 호이스팅을 일으킨다. 만약 호이스팅이 되지 않았다면 함수 바깥에서 선언한 age 30이 정상적으로 찍혀야 한다. 

### 변수의 생성과정
1. 선언단계 2. 초기화 단계 3. 할당 단계

> var 
1. 선언 및 초기화 단계
2. 할당 단계<br>
초기화 : undefined 를 할당 해주는 단계
var는 선언과 초기화가 동시에 된다. 그래서 할당전에 호출하면 에러를 내지않고 undefined가 나온다. 

> let
1. 선언단계
2. 초기화 단계
3. 할당 단계
호이스팅 되면서 선언단계가 이루어지지만. 초기화 단계는 런타임에 발생하기 때문에 ReferenceError가 발생하게 된다.

> const
1. 선언 + 초기화  + 할당 
const는 선언과 할당이 동시에 되어야 한다. let과 var는 선언만 해두고 나중에 할당하는 것을 허용한다. let과 var는 나중에 변수를 바꿀 수 있으니 당연하다.

```
var age ;
age = 30;

let name ;
name = 'Mike';

const gender; // 위에 var 과 let은 괜찮지만 const 부분에서 에러가 발생한다.
gender = 'male'
```


### 스코프

var : 함수 스코프(function-scoped)
let, const : 블록 스코프(block-scoped)
블록 스코프 : 함수, if문, fo문, while문, try/catch 문 등

블록스코프는 모든 코드 블록 내에서 선언된 변수는 코드 블록 내에서만 유효하며 외부에서는 접근 할 수 없다. 즉, 코드 블록 내부에서 선언한 변수는 지역변수이다. 

함수 스코프는 함수내에서 선언된 변수만 그 지역변수가 되는 것이다. 

```
const age = 30;
if(age>19){
	var txt = '성인'
}
console.log(txt); // '성인' 
```

```
function add(num1, num2){
	var result = num1 + num2;
}
add(2,3);
console.log(result); // ReferenceError

유일하게 벗어날 수 없는 스코프가 함수이다. 
```

