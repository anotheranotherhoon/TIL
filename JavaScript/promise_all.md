# Promise.all
* promise.all은 모든 프로미스가 성공할 경우에만 성공하는 하나의 프로미스를 반환한다.
* promise.all 메서드는 프로미스를 요소로 갖는 배열 등의 이터러블(반복 가능한 객체)을 인수로 전달받는다.
* 전달받은 모든 프로미스가 모두 fulfilled 상태가 되면 모든 처리 결과를 배열에 저장해 새로운 프로미스를 반환한다.

```
const practicePromiseAll = () => {
  return Promise.all([getGeneralProfilePromise(generalOne), getGeneralProfilePromise(generalTwo)])
  .then((data)=>{
    return data.map((profile) => JSON.parse(profile))
  })
}
```

|프로미스의 상태 정보|의미|상태 변경 조건|
|------|---|---|
|pending|비동기 처리가 아직 수행되지 않은 상태|프로미스가 생성된 직후 기본 상태|
|fulfilled|비동기 처리가 수행된 상태(성공)|resolve 함수 호출|
|rejected|비동기 처리가 수행된 상태(실패)|reject 함수 호출|


* 1. getDataFromFilePromise(userOne)과 getDataFromFilePromise(userTwo)가 모두 fullfield 상태가 되었다.
* 2. 따라서 모든 처리 결과를 *배열*에 저장해 새로운 프로미스를 반환한다.
* 3. 모든 프로미스가 fulfilled 상태가 되면 resolve된 처리 결과를 모두 배열에 저장해 새로운 프로미스를 반환한다.
* 4. 이때 만약 첫 번째 프로미스가 가장 나중에 fulfilled 상태가 되어도 Promise.all 메서드는 첫 번째 프로미스가 resolve한 처리 결과부터 차례대로 배열에 저장해 그 배열을 resolve하는 새로운 프로미스를 반환한다. 즉, 처리 순서가 보장된다.

* Promise.all 메서드는 인수로 전달받은 배열의 프로미스가 하나라도 rejected 상태가 되면 나머지 프로미스가 fulfilled상태가 되는 것을 기다리지 않고 즉시 종료한다. 
```
[
  '{\n' +
    '  "name": "이성계",\n' +
    '  "age": 40,\n' +
    '  "gender": "Male",\n' +
    '  "company": {\n' +
    '    "name": "가별초"\n' +
    '  }\n' +
    '}',
  '{\n' +
    '  "name": "최영",\n' +
    '  "age": 59,\n' +
    '  "gender": "Male",\n' +
    '  "company": {\n' +
    '    "name": "고려군"\n' +
    '  }\n' +
    '}'
]
```

* 예제의 경우 위와 같은 배열을 받으므로 map함수를 이용하여 배열의 요소들을 차례로 JSON.parse하여 새로운 배열에 담아준다.


