# Map

## 면접 질문

* Q1. 해시 테이블을 설명하세요.
    * 해시 테이블은 무한에 가까운 데이터(키)들을 유한한 개수의 해시 값으로 매핑한 테이블입니다. 이를 통해 작은 크기의 캐시 메모리로도 프로세스를 관리하도록 할 수 있다.
    * 삽입, 삭제, 탐색 시 평균적으로 O(1)의 시간 복잡도를 가지며 unordered_map으로 구현한다. 

## Map DeepDive
> *  Map은 빈도수 정렬에 많이 사용되며
> * 메서드 이름이 명시적인 장점이 있다. (has, get, set, size, delete, clear, forEach)

* Map 객체는 키와 값(key, value)의 쌍으로 이루어진 컬렉션이다. 
* Map 객체는 객체와 유사하지만 다음과 같은 차이가 있다. 

|구분|객체|Map 객체|
|------|---|---|
|키로 사용할 수 있는 값|문자열 또는 심벌 값|객체를 포함한 모든 값|
|이터러블|X|O|
|요소 개수 확인|Object.keys(obj).length|map.size|

## Map 객체의 생성
* Map 객체는 Map 생성자 함수로 생성한다. Map 생성자 함수에 인수를 전달하지 않으면 빈 Map 객체가 생성된다.
```
const map = new Map();
console.log(map); Map(0)
```
* Map 생성자 함수는 이터러블을 인수로 전달 받아 Map 객체를 생성한다. 이 떄 인수로 전달되는 이터러블은 키와 값의 쌍으로 이루어진 요소로 구성되어야 한다.

* Map 생성자 함수의 인수로 전달한 이터러블에 중복된 키를 갖는 요소가 존재하면 값이 덮어 써진다. 따라서 Map 객체에는 중복된 키를 갖는 요소가 존재할 수 없다.

## 요소 개수 확인 size
* Map 객체의 요소 개수를 확인할 때는 Map.prototype.size 프로퍼티를 사용한다.
```
const size = new Map([['key1', 'value1'],['key2', 'value2']])
map.size = 2
```
* size 프로퍼티는 setter 함수 없이 getter 함수만 존재하는 접근자 프로퍼티다. 
* 따라서 size 프로퍼티에 숫자를 할당하여 Map 객체의 요소 개수를 변경할 수 없다.

## 요소 추가 set

* Map 객체에 요소를 추가할 때는 Map.prototype.set 메서드를 사용한다.

* set 메서드는 새로운 요소가 추가된 Map 객체를 반환한다. 따라서 set 메서드를 호출한 후에 set메서드를 연속적으로 호출할 수 있다. 

```
const map = new Map();

map.set('key1','value1').set('key2', 'value2')

console.log(map) // Map(2){'key1' => 'value1', 'key2' => 'value2'}
```
* Map 객체에는 중복된 키를 갖는 요소가 존재할 수 없기 때문에 중복된 키를 갖는 요소를 추가하면 값이 덮어 써진다. 이때 에러가 발생하지 않는다.

## 요소 취득 get

* Map 객체에서 특정 요소를 취득하려면 Map.prototype.get 메서드를 사용한다.

* get 메서드의 인수로 키를 전달하면 Map 객체에서 인수로 전달한 키를 갖는 값을 반환한다.

* Map 객체에서 인수로 전달한 키를 갖는 요소가 존재하지 않으면 undefined를 반환한다.

## 요소 존재 여부 확인 has

* Map 객체에 특정 요소가 존재하는지 확인하러면 Map.prototype.has 메서드를 사용한다. 

* has 메서드는 특정 요소의 존재 여부를 나타내는 불리언 값을 반환한다.

## 특정 요소 삭제  delete (key에 해당하는 것의 key와 값을 모두 삭제함)

* Map 객체의 요소를 삭제하려면 Map.prototype.delete 메서드를 사용한다.

* delete 메서드는 삭제 성공 여부를 나타내는 불리언 값을 반환한다.

* 만약 존재하지 않는 키로 Map 객체의 요소를 삭제하려 하면 에러 없이 무시된다.

* delete 메서드는 삭제 성공 여부를 나타내는 불리언 값을 반환한다. 따라서 set 메서드와 달리 연속적으로 호출<sup>method chaining</sup>할 수 없다. 

## 요소 일괄 삭제 clear
* Map 객체의 요소를 일괄 삭제하려면 Map.prototype.clear 메서드를 사용한다.

* clear 메서드는 언제나 undefined를 반환한다.

## 요소 순회 forEach
* Map 객체의 요소를 순회하려면 Map.prototype.forEach 메서드를 사용한다.

* Map.prototype.forEach메서드는 Array.prototype.forEach 메서드와 유사하게 콜백 함수와 forEach 메서드의 함수 내부에서 this로 사용될 객체를 인수로 전달한다. 
    * 첫 번째 인수 : 현재 순회 중인 요소값
    * 두 번째 인수 : 현재 순화 중인 요소키
    * 세 번쨰 인수 : 현재 순회 중인 Map 객체 자체

```
const lee = { name : 'Lee'};
const kim = { name : 'Kim'};

const map = new Map([[lee, 'developer'], [kim, 'designer']]);
map.forEach((v, k, map)=> console.lgo(v, k , map));

developer {name : "Lee"} Map(2){
    {name : "Lee"} => "developer",
    {name : "Kim"} => "designer"
}
designer {name : "Kim"} Map(2){
    {name : "Lee"} => "developer",
    {name : "Kim"} => "designer"
}

```

* Map 객체는 이터러블이다. 따라서 for ... of 문으로 순회할 수 있으며, 스프레드 문법과 구조분해할당의 대상이 될 수도 있다.

* Map 객체는 이터러블이면서 동시에 이터레이터인 객체를 반환하는 메서드를 제공한다.

|Map 메서드|설명|
|------|---|
|Map.prototype.keys|Map 객체에서 요소키를 값으로 갖는 이터러블이면서 동시에 이터레이터인 객체를 반환한다.|
|Map.prototype.values|Map 객체에서 요소값을 값으로 갖는 이터러블이면서 동시에 이터레이터인 객체를 반환한다.|
|Map.prototype.entries|Map 객체에서 요소키와 요소값을 값으로 갖는 이터러블이면서 동시에 이터레이터인 객체를 반환한다.|


* Map 객체는 요소의 순서에 의미를 갖지 않지만 Map 객체를 순회하는 요소가 추가된 순서를 따른다.


> 참고 모던자바스크립트DeepDive37장 Set과 Map

> 면접을 위한 CS 전공지식 노트