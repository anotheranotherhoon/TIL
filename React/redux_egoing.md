## react redux 4인방

* import {Provider, useSelector, useDispatch, connect} from 'react-redux'

## Provider

```
function reducer(currentState, action){
    if(currentState === undefined){
        return{
            number:1
        }
    }
    const newState = {...currentState};
    if(action.type === 'PLUS'){
        newState.number++
    }
    return newState;
}
const store = createStore(reducer);

<Provider store={store}>
    <Left1></Left1>
    <Right1></Right1>
</Provider>
```

## useSelector()
```
function Left1(props){
    const number = useSelector((state) => state.number);
    return (
        <div>
            <h1>Left3 : {number}</h1>
        </div>
    )
}
```

## dispatch 함수 가져오기

```
function Right1(props){
    <div>
        <h1>Right1</h1>
        <input type="button" value="+" onClick={()=>{
            dispatch({ type : 'PLUS'})
        }}>
    </div>
}
```
