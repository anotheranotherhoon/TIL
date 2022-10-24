# Redux toolkit
## createSlice
* createSlice는 reducer를 만드는걸 도와준다.
* 객체를 매개 변수로 받는데
* 객체에는
```js
let initialState = {
    productList : [],
    selectedItem : null,
}
export const counterSlice = createSlice({
    name : 'counter', //slice에 대한 이름
    initialState,
    reducers : {
        increment()
    }
})
```
* createSlice안에는 반드시 세가지 필드가 존재해야 한다. 
* 