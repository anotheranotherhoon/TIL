# 프로토타입 Prototype
> 아래 글에 사용될 예시
```
class King {
	constructor(name, firstSon){
		this.name = name;
    this.firstSon = firstSon
    }
	jangja(){
        if(this.firstSon === true){
            console.log("과인 " + this.name +"은/는 적장자다")
        }
        else{
            console.log("끌어내라")
        }
	}
}
const taeJong = new King('이방원', true);
const saeJong = new King('이도', false);
taeJong.jangja() // 과인 이방원은/는 적장자다 
saeJong.jangja() // 끌어내라
```

## 0. Prototype 
* 프로토타입은 클래스, 객체의 내용 복사 없이도 상속을 구현할 수 있게 해주는 방법이다.
* 프로토타입은 상속이 아니라 연결이다.

## 1. new와 함수가 만나면 발생하는 일
* 1. new 연산자가 새로운 빈 객체(인스턴스)를 메모리 상에 생성함.
* 2. 그 후에 King함수 안에 this에 생성된 빈 객체(인스턴스//taeJong)가 바인딩된다.
* 3. 그 상태에서 King안의 내용이 실행되는데 그 내용들이 this의 속성(프로퍼티)를 할당하고 채워준다.
* 4. return 하는 것이 없다면 그렇게 만들어진 this가 return 된다.

## 1-1. 복사 없이 어떻게 상속을 수행할 수 있는 것인가?
* ~~다른언어에서~~ 일반적인 class에서 하나의 class가 부모class로 부터 상속을 받게 되면 자식 class로 인해 만들어진 인스턴스에는 부모와 자식 모두의 내용이 합쳐져서 반영되게 된다.
* 하지만 **자바스크립트** 에서는 **불가능**하다.

* 자바스크립트는 깊은 복사가 일어날 수 없다. 따라서 객체 자체나 코드 내용을 복사하는 것은 불가능하다.

* 복사할 수 있는 것은 원시값과 참조값뿐이다.

* 그래서 자바스크립트는 상속을 흉내내기 위해서 상속이 아닌 연결이라는 개념을 활용한다.


## 2.  `.__proto__`
* 연결은 `.__proto__` 라는 이름의 속성을 바탕으로 실행된다.

* 자바스크립트의 모든 객체들은 `.__proto__` 라는 속성을 가지고 있다. 

* 객체간의 연결 관계 이해하기
  * 1. 다른 객체를 바탕으로 만들어진 객체라면 
  >객체는 자신의 원형이라고 할 수 있는 객체가 있다면 그 객체를 가리키는`.__proto__`링크를 자동으로 가진다.
  * 2. 그냥 객체가 아니라 함수라면 
  >`.__proto__`외에도 함수의 프로토타입 객체를 가진다. 
  * 3. new + 함수로 만들어진 객체라면**
  >만들어진 새로운 객체에 `.__proto__`링크가 King.prototype을 가리키게된다.

![](https://github.com/anotheranotherhoon/TIL/blob/master/JavaScript/img/relationship.jpg?raw=true)


## 2. `[[Prototype]]` vs prototype 프로퍼티
* 모든 객체는 자신의 프로토타입 객체를 가리키는 `[[Prototype]]` 인터널 슬롯(internal slot) 을 갖으며 상속을 위해 사용된다.

* 함수도 객체이므로 `[[Prototype]]` 인터널 슬롯을 갖는다. 그런데 함수 객체는 일반 객체와는 달리 prototype 프로퍼티도 소유하게 된다.


> 주의해야 할 것은 prototype 프로퍼티는 프로토타입 객체를 가리키는 `[[Prototype]]` 인터널 슬롯은 다르다는 것이다. prototype 프로퍼티와 `[[Prototype]]`은 모두 프로토타입 객체를 가리키지만 관점의 차이가 있다.



![](https://github.com/anotheranotherhoon/TIL/blob/master/JavaScript/img/king_prototype.png?raw=true)

![](https://github.com/anotheranotherhoon/TIL/blob/master/JavaScript/img/obj_prototype.png?raw=true)
**모든 객체가`[[Prototype]]`을 가지고 있다.**

* `[[Prototype]]`
  * 함수를 포함한 모든 객체가 가지고 있는 인터널 슬롯
  * 객체의 입장에서 자신의 부모역할을 하는 프로토타입 객체를 가리키며 함수 객체의 경우 Function.prototype을 가리킨다.

```
King.__proto__ === Function.prototype // true
```
* prototype 프로퍼티 
  * 함수 객체만 가지고 있는 프로퍼티이다.
  * 함수 객체가 생성자로 사용될때 이 함수를 통해 생성될 객체의 부모 역할을 하는 객체(프로토타입 객체를)가리킨다.

![](https://github.com/anotheranotherhoon/TIL/blob/master/JavaScript/img/king_taeJong.png?raw=true)

>* const taeJong = new King('이방원', true); 처럼 taeJong의 부모역할을 할 객체(King)을 가리킨다.
>* King.prototype 에는 taeJong 안에 있는 `[[Prototype]]`과 유사한 구조를 가지고 있다. 하지만 `.__proto__`가 가리키는게 서로 다르다.

```
console.log(King.prototype === taejong.__proto__)
```

## 3. constructor 프로퍼티
* 프로토타입 객체는 constructor 프로퍼티를 갖는다. 이 constructor 프로퍼티는 객체의 입장에서 자신을 생성한 객체를 가리킨다.

```
// King() 생성자 함수에 의해 생성된 객체를 생성한 객체는 King() 생성자 함수다.
console.log(King.prototype.constructor === King) // true
// taeJong 객체를 생성한 객체는 King()생성자 함수다. 
console.log(taejong.constructor === King)// true
// King() 생성자 함수를 생성한 객체는 Function() 생성자 함수다.
console.log(King.constructor === Function) // true

```
## 4. prototype을 사용하는 이유
* prototype에서는 해당 함수에 대한 사용법이 들어있다. 
* constructor에서는 해당 함수가 어떤 형식으로 생성되었는지를 알려준다.

> 위의 예제에서 taeJong 과 saeJong 인스턴스 안에는 둘다 jangja라는 메서드가 저장되어있다. 

>따라서 jangja라는 메서드가 taeJong과 saeJong 각각에 저장되어 있고 그만큼의 메모리를 차지 하고 있다.
```
class King {
	constructor(name, firstSon){
		this.name = name;
    this.firstSon = firstSon
    }
}
King.prototype.jangja = function() {
  if(this.firstSon === true){
    console.log("과인 " + this.name +"은/는 적장자다")
    }
    else{
      console.log("끌어내라")
      }
}
const taeJong = new King('이방원', true);
const saeJong = new King('이도', false);
taeJong.jangja() // 과인 이방원은/는 적장자다 
saeJong.jangja() // 끌어내라
```

![](https://github.com/anotheranotherhoon/TIL/blob/master/JavaScript/img/why_use_prototype.png?raw=true)

> class King에서 메서드로 지정해주었던 jangja를 없애고 King.prototype내에 함수를 넣어주었다. 

> 이제 taeJong에는 jangja라는 메서드가 없고 prototype에 jangja 메서드를 넣어주었다.

> 그리고 taeJong은 King.prototype에서 jangja를 상속받아 사용할 수 있다. 

> King.prototyp.jangja에 메모리를 한번만 차지한다.

> 만약 jangja 메서드가 필요한 왕 인스턴스를 매우 많이 만든다면 그만큼 메모리를 효율적으로 사용할 수 있게 된 것이다.







## 5.Prototype Chaining
* prototype을 `.__proto__`를 따라 탐색하기

```
const a = {
	attr1 : 'moohan~',
}

const b = {
	attr2: 'mooyaho~',
}
a.__proto__ = b;
console.log(a.attr2) // 'mooyaho~' 
```
* a객체의`.__proto__`를 직접적으로 b에 연결 시키면 a객체에는 없는 속성이 있어도 `__proto__`통해 b객체로 이동하여 거기서 프로퍼티를 찾아서 a객체에 없는 속성도 b객체에 있다면 프로퍼티를 사용할 수 있다. 



>참고 : [PoiemaWeb](https://poiemaweb.com/js-prototype), [크리스의 Prototype](https://www.youtube.com/watch?v=RYxgNZW3wl0)