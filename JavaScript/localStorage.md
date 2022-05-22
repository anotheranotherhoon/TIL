# localStorage로 데이터를 관리하는 것에 대하여

## localStorage에 데이터가 있을 때와 없을 때에 따른 데이터 관리

## 1. 해결과제

* 1. localStorage가 비었을 경우 data를 로컬스토리지에 저장한다.
* 2. 새로운 데이터를 추가할 경우 data의 선두에 저장한다.
* 2-1. 새로고침 했을 때에도 localStorage에 데이터가 저장되어 있어야한다.
* 2-2. 데이터를 추가했을 경우 추가한 데이터가 여전히 선두에 있어야한다.
```
script.js
const data = [
    {
        name: "lee",
        age : 10
    },
    {
        name: "kim",
        age : 12
    },
    {
        name: "park",
        age : 10
    },
    {
        name: "choi",
        age : 10
    },
]
```

## JSON.stringify()
>
참고
  :[mdn JSON.stringify()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/JSON/stringify)

* JSON.stringify() 메서드는 JavaScript 값이나 객체를 JSON **문자열**로 변환합니다.
* JSON.stringify()는 값을 JSON 표기법으로 변환한다.

```
JSON.stringify(data)
console.log(JSON.stringify(data))
console.log(typeof(JSON.stringify(data)))
```
![](https://github.com/anotheranotherhoon/TIL/blob/master/JavaScript/img/json_stringify.png?raw=true)

>* JavaScript 객체인 datafmf JSON문자열로 변환한다는 것이 포인트다.
* object처럼 생겼지만 문자열이다.


## Storage.setItem(keyName, keyValue)
>
참고:[mdn Storage.setItem()](https://developer.mozilla.org/en-US/docs/Web/API/Storage/setItem)


```
localStorage.setItem("data", JSON.stringify(data))
```
![](https://github.com/anotheranotherhoon/TIL/blob/master/JavaScript/img/localStorage_setitem.png?raw=true)

* 로컬스토지에 Key에 keyName을 넣고 Value로 keyValue를 갖게된다.

## JSON.parse()
>
참고:[mdn JSON.parse()](https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/JSON/parse)

* JSON.parse() 메서드는 JSON 문자열의 구문을 분석하고, 그 결과에서 JavaScript 값이나 객체를 생성한다. 

```
const localStorageData = localStorage['data']
console.log(localStorageData)
console.log(typeof localStorageData)
```
![](https://github.com/anotheranotherhoon/TIL/blob/master/JavaScript/img/json_parse.png?raw=true)

* localStorage['data']를 통해 localStorage를 객체 처럼 key 값으로 호출하여 value에 접근할 수 있다.

```
const localStorageData = localStorage['data']
console.log(JSON.parse(localStorageData))
console.log(typeof (JSON.parse(localStorageData)))
```
![](https://github.com/anotheranotherhoon/TIL/blob/master/JavaScript/img/json_parse.png?raw=true)

* JSON.parse를 통해 JSON 문자열을 object가 담긴 배열로 접근할 수 있게 되었다.

```
const parseData = JSON.parse(localStorageData)
console.log(parseData[0]["name"])
```
![](https://github.com/anotheranotherhoon/TIL/blob/master/JavaScript/img/parse_data.png?raw=true)

* 이제 로컬스토리지의 데이터를 자유롭게 사용할 수 있다.

## 문제 해결
```
function unshiftData() {
    data.unshift({name: "missionClear", age : 100})
}
```

```
unshiftData() // 1. unshift함수를 호출하고 
localStorage.setItem("data", JSON.stringify(data)) //새로운 배열을 다시 로컬스토리지에 할당한다.
console.log(JSON.parse(localStorage['data'])[0])
//{name: 'missionClear', age: 100}
```
* script.js 내의 data변수에 할당된 배열에 unshift를 통해 배열의 선두에 새로운 데이터를 추가한다.

```
if(!localStorage['data']){
	localStorage.setItem("data", JSON.stringify(data))
}
```
* 새로고침 할 때 localStorage["data"]에 값이 없을 경우 값을 추가하고 그렇지 않을 경우 로컬스토리지를 재할당 하지 않는다. 

* 여기서 return localStorage.setItem("data", JSON.stringify(data)) 즉, return 을 할 경우 Uncaught SyntaxError: Illegal return statement가 발생하니 주의한다.
