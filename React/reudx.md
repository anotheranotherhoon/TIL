# Redux

## 상태란 무엇인가?

* 상태는 변하는 데이터이다. 

* UI, 프론트엔드 개발에서는 "동적으로 표현되는 데이터"이다.

## Side Effect

* 상태를 다룰 때에는 Side Effect는 주요 고려 대상이다.

* Side Effect의 정의
    * 함수의 입력 외에도 함수의 결과에 영향을 미치는 요인
    * `ex)`네트워크 요청, 백엔드 API 호출이 Side Effect이다.

* React의 주요 개발 원칙 중 하나는 UI를 페이지 단위가 아닌 컴퍼넌트 단위로 보는 것이다.

## React로 사고하기 섹션 읽어 보기

* Redux는 React의 관련 라이브러리, 혹은 하위 라이브러리가 아니다.

* Redux는 React없이도 사용할 수 있는 상태 관리 라이브러리다.

## Action, Dispatcher, Reducer, Store, Redux의 3가지 원칙

## Redux의 상태 관리 동작 순서
1. 상태가 변경되어야 하는 이벤트가 발생하면, 변경될 상태에 대한 정보가 담긴 Action 객체가 생성되어야 한다.
2. 이 Action 객체는 Dispatch 함수의 인자로 전달된다.
3. Dispatch 함수는 Action 객체를 Reducer 함수로 전달해준다.
4. Reducer 함수는 Action 객체의 값을 확인하고, 그 값에 따라 전역 상태 저장소 Store의 상태를 변경한다.
5. 상태가 변경되면, React는 화면을 다시 렌더링 한다.

* **즉, Redux에서는 Action -> Dispatch -> Reducer -> Store 순서대로 데이터가 단방향으로 흐르게된다.**

## Action
* Action은 말 그대로 어떤 액션을 취할 것인지 정의해 놓은 객체로, 다음과 같은 형식으로 구성된다.
```
// payload가 필요 없는 경우
{ type: 'INCREASE' }
// payload가 필요한 경우
{ type: 'SET_NUMBER', payload: 5 }
```

* type은 필수로 지정해주어야 한다. 

* 해당 Action 객체가 어떤 동작을 하는지 명시해주는 역할을 하기 때문이며, 대문자와 Snake Case로 작성한다. 

* 여기에 필요에 따라 payload를 작성해 구체적인 값을 전달한다.

*  Action을 직접 작성하기보다는 Action 객체를 생성하는 함수를 만들어 사용하는 경우가 많다. 

*  이러한 함수를 액션 생성자(Action Creater)라고도 한다.
```
// payload가 필요 없는 경우
const increase = () => {
  return {
    type: 'INCREASE'
  }
}

// payload가 필요한 경우
const setNumber = (num) => {
  return {
    type: 'SET_NUMBER',
    payload: num
  }
}
```

## Dispatch
* Dispatch는 Reducer로 Action을 전달해주는 함수다. Dispatch의 전달인자로 Action 객체가 전달된다.

```
// Action 객체를 직접 작성하는 경우
dispatch( { type: 'INCREASE' } );
dispatch( { type: 'SET_NUMBER', payload: 5 } );

// 액션 생성자(Action Creator)를 사용하는 경우
dispatch( increase() );
dispatch( setNumber(5) );
```
* Action 객체를 전달받은 Dispatch 함수는 Reducer를 호출한다.

## Reducer

* Reducer는 Dispatch에게서 전달받은 Action 객체의 type 값에 따라서 상태를 변경시키는 함수다.

```
const count = 1

// Reducer를 생성할 때에는 초기 상태를 인자로 요구합니다.
const counterReducer = (state = count, action) {

  // Action 객체의 type 값에 따라 분기하는 switch 조건문입니다.
  switch (action.type)

    //action === 'INCREASE'일 경우
    case 'INCREASE':
			return state + 1

    // action === 'DECREASE'일 경우
    case 'DECREASE':
			return state - 1

    // action === 'SET_NUMBER'일 경우
    case 'SET_NUMBER':
			return action.payload

    // 해당 되는 경우가 없을 땐 기존 상태를 그대로 리턴
    default:
      return state;
}
// Reducer가 리턴하는 값이 새로운 상태가 됩니다.
```
* 이 때, Reducer는 순수함수여야 한다. 외부 요인으로 인해 기대한 값이 아닌 엉뚱한 값으로 상태가 변경되는 일이 없어야 하기 때문이다.

* 만약 여러 개의 Reducer를 사용하는 경우, Redux의 combinedReducers 메서드를 사용해서 하나의 Reducer로 합쳐줄 수 있다.

```
import { combineReducers } from 'redux';

const rootReducer = combineReducers({
  counterReducer,
  anyReducer,
  ...
});
```

## Store
* Store는 상태가 관리되는 오직 하나뿐인 저장소의 역할을 한다. 

* Redux 앱의 state가 저장되어 있는 공간이다. 

* 아래 코드와 같이 createStore 메서드를 활용해 Reducer를 연결해서 Store를 생성할 수 있다.

```
import { createStore } from 'redux';

const store = createStore(rootReducer);
```

## Redux Hooks
* Redux Hooks는 React에서 Redux를 사용할 때 활용할 수 있는 Hooks 메서드를 제공한다. 

* useSelector(), useDispatch()

## useSelector()
* useSelector() 는 컴포넌트와 state를 연결하여 Redux의 state에 접근할 수 있게 해주는 메서드다.


## useDispatch()
* useDispatch() 는 Action 객체를 Reducer로 전달해 주는 메서드다. Dipatch를 설명할 때 사용한 dispatch 함수도 useDispatch()를 사용한 것이다.

```
import { useDispatch } from 'react-redux'

const dispatch = useDispatch()
dispatch( increase() )
console.log(counter) // 2

dispatch( setNumber(5) )
console.log(counter) // 5
```

## Redux의 세 가지 원칙

1. Single source of truth
* 동일한 데이터는 항상 같은 곳에서 가지고 와야 한다는 의미이다.
* 즉, Redux에는 데이터를 저장하는 Store라는 단 하나뿐인 공간이 있음과 연결이 되는 원칙이다. 

2. State is read-only
* 상태는 읽기 전용이라는 뜻으로, React에서 상태갱신 함수로만 상태를 변경 할 수 있었던 것처럼, Redux의 상태도 직접 변경할 수 없음을 의미한다. 
* 즉, Action 객체가 있어야만 상태를 변경할 수 있음과 연결되는 원칙이다.

3. Changes are made with pure functions
* 변경은 순수함수로만 가능하다는 뜻으로, 상태가 엉뚱한 값으로 변경되는 일이 없도록 순수함수로 작성되어야 하는 Reducer와 연결되는 원칙이다.

