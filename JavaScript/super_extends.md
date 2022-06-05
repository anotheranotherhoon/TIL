# super 와 extends

## super
* super 키워드는 부모 오브젝트의 함수를 호출할 때 사용된다.

* super 키워드는 부모 클래스를 참조(Reference)할 때 또는 부모 클래스의 constructor를 호출할 때 사용한다.

* 생성자에서는 super 키워드 하나만 사용되거나 this 키워드가 사용되기 전에 호출되어야 합니다. 

* 또한 super 키워드는 부모 객체의 함수를 호출하는데 사용될 수 있습니다.

## extends
* extends 키워드는 클래스를 다른 클래스의 자식으로 만들기 위해 class 선언 또는 class 식에 사용됩니다.

* extends 키워드는 내장 객체뿐만 아니라 사용자 정의 클래스를 하위 클래스로 만들기 위해 사용될 수 있습니다.

---
## super와 extends를 키워드로 사용할 수 있는 클래스와 생성자 함수의 차이점

* 클래스와 생성자 함수는 모두 프로토타입 기반의 인스턴스를 생성하지만 전확히 동일하게 동작하지는 않는다.

1. 클래스를 new 연산자 없이 호출하면 에러가 발생한다. 하지만 생성자 함수를 new 연산자 없이 호출하면 일반 함수로서 호출된다.

2. 클래스는 상속을 지원하는 extends와 super 키워드를 제공한다. 하지만 생성자 함수는 extends와 super키워드를 지원하지 않는다.

3. 클래스는 호이스팅이 발생하지 않는 것처럼 동작한다. 하지만 함수 선언문으로 정의된 생성자 함수는 함수 호이스팅이, 함수 표현식으로 정의한 생성자 함수는 변수 호이스팅이 발생한다.

4. 클래스 내의 모든 코드에는 암묵적으로 strict mode가 지정되어 실행되며 strict모드를 해재할 수 없다. 하지만 생성자 함수는 암묵적으로 strict mode가 지정되지 않는다. 

5. 클래스의 constructor, 프로토타입 메서드, 정적 메서드는 모두 프로퍼티 어트리뷰트 `[[Enumerable]]`의 값이 false다. 다시 말해 열거되지 않는다.

* 생성자 함수와 클래스는 프로토타입 기반의 객체지향을 구현했다는 점에서 매우 유사하다.

* 하지만 클래스는 생성자 함수 기반의 객체 생성 방식보다 견고하고 명료하다. 

* 특히 extends와 super키워드는 상속 관계 구현을 더욱 간결하고 명료하게 한다.

## 상속에 의한 클래스 확장

* 상속에 의한 클래스 확장은 기존 클래스를 상속받아 새로운 클래스를 확장<sup>extends</sup> 하여 정의하는 것이다. 

* 클래스는 상속을 통해 기존 클래스를 확장할 수 있는 문법{extends}이 제공된다.

* extends 키워드를 사용한 클래스 확장은 간편하고 직관적이다. 

## extends 키워드

* 상속을 통해 클래스를 확장하려면 extends 키워드를 사용하여 상속받을 클래스를 정의한다.

```
// 슈퍼(베이스/부모)클래스
class King {}
// 서브 (파생/자식)클래스
class choseonKing extends King{}
```

* 상속을 통해 확장된 클래스를 서브클래스<sup>subclass</sup> 라 부르고, 

* 서브클래스에게 상속된 클래스를 수퍼클래스<sup>super class</sup>라 부른다.

* 서브클래스를 파생 클래스<sup>derived class</sup> 또는 자식 클래스<sup>child class</sup>

* 수퍼클래스를 베이스 클래스<sup>base class</sup> 또는 부모 클래스 <sup>parent class</sup> 라고 부르기도 한다.

* extends 키워드는 클래스뿐만 아니라 생성자 함수를 상속받아 클래스를 확장할 수도 있다. 

* 단 extends 키워드 앞에는 반드시 클래스가 와야한다.

* extends 키워드 다음에는 클래스뿐만이 아니라 `[[Construct]]` 내부 메서드를 갖는 함수 객체로 평가될 수 있는 모든 표현식을 사용할 수 있다. 

* 이를 통해 동적으로 상속받을 대상을 결정할 수있다.

## 서브클래스의 constructor
* 클래스에서 constructor를 생략하면 클래스에 다음과 같이 비어있는 constructor가 암묵적으로 정의된다.

```
constructor(){}
```

* 서브클래스에서 constructor를 생략하면 클래스에 다음과 같은 constructor가 암묵적으로 정의된다.
```
constructor(...args) {super(...args)}
```

* super()는 수퍼클래스의 constructor를 호출하여 인스턴스를 생성한다.

* 수퍼클래스와 서브클래스에서 constructor를 생략한 경우 암묵적으로 constructor가 정의된다.
```
// 수퍼클래스
class King{}

// 서브클래스
class choseonKing extends King{}

// 수퍼클래스에 암묵적으로 constructor를 정의 했다. 
class King{
    constructor(){}
}
// 서브클래스에 암묵적으로 constructor를 정의 했다. 
class choseonKing extends King{
    constructor(...args){super(...args);}
}

```

## super 키워드
* super 키워드는 함수처럼 호출할 수도 있고 this와 같이 식별자 처럼 참조할 수 있는 특수한 키워드다. super키워드는 다음과 같이 동작한다.

> * super를 호출하면 수퍼클래스의 constructor를 호출한다.
> * super를 참조하면 수퍼클래스의 메서드를 호출할 수 있다. 

## super ghcnf

* super를 호출하면 수퍼클래스의 constructor를 호출한다.

* 수퍼클래스의 constructor 내부에서 추가한 프로퍼티를 그대로 갖는 인스턴스를 생성한다.

```
class King{
    constructor(a, b){
        this.a = a;
        this.b = b;
    }
}
class choseonKing extends King {}

const taeJong = new choseonKing (1, 2);
console.log(taeJong); // choseonKing{ a : 1, b: 2}
```
## super를 호출할 때 주의할 사항

1. 서브클래스에서 constructor를 생략하지 않는 경우 서브클래스의 constructor에서는 반드시 super를 호출해야한다. 

2. 서브클래스의 constructor에서 super를 호출하기 전에는 this를 참조할 수 없다.

3. super는 반드시 서브클래스의 constructor에서만 호출한다. 서브클래스가 아닌 클래스의 constructor나 함수에서 super를 호출하면 에러가 발생한다. 

---

## super 참조
> 메서드 내에서 super를 참조하면 수퍼클래스의 메서드를 호출할 수 있다.

1. 서브클래스의 프로토타입 메서드 내에서 super.sayHi는 수퍼클래스의 프로토타입 메서드 sayHi를 가리킨다.

```
class King{
    constructor(name){
        this.name = name;
    }
    sayHi(){
        return `오냐 내 이름은 ${this.name}이다`;
    }
}
class choseonKing extends King{
    sayHi(){
        return `${super.sayHi()}, 무엄하다`;
    }
}
const taeJong = new choseonKing('방원');
console.log(taeJong.sayHi()); // 오냐 내 이름은 방원이다, how 무엄하다
```
* super 참조를 통해 수퍼클래스의 메서드를 참조하러면 super가 수퍼클래스의 메서드가 바인딩된 객체, 즉 스퍼 클래스의 prototype 프로퍼티에 바인딩된 프로토타입을 참조할 수 있어야 한다.


* super는 자신을 참조하고 있는 메서드가 바인딩되어 있는 객체의 프로토타입을 가리킨다.

* 따라서 super.sayHi는 King.prototype.sayHi를 가리킨다. 

```
class King{
    constructor(name){
        this.name = name;
    }
    sayHi(){
        return `오냐 내 이름은 ${this.name}이다`;
    }
}

class choseonKing extends King{
    constructor(name,age, firstSon){
        super(name) // 상위 클래스의의 name을 가져온다.
        this.age = age;
        this.firstSon = firstSon;
    }
}

const taeJong = new choseonKing('방원',40, true);
//choseonKing {name: '방원', age: 40, firstSon: true}
```


참조[super](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Operators/super), [extends](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Classes/extends), 모던자바스크립트DeepDive