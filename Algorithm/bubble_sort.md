# 거품 정렬
* 거품 정렬 <sup>bubble sort</sup>은  전체 배열을 순회하면서 항목이 다른 항목 보다 큰 경우 두 항목을 교환한다.

* swap은 정렬에 사용되는 일반적인 함수다. swap은 두 배열 항목 값들을 교환한다.
```js
function swap(arr, index){
    const temp = arr[i]
    arr[i] = arr[i+1]
    arr[i+1] = temp
}

[arr[i], arr[i+1]] = [arr[i+1], arr[i]]도 가능하다.
```

* 시간복잡도 O(n<sup>2</sup>) 중첩루프를 사용하기 때문에 시간 복잡도는 O(n<sup>2</sup>)이다.
* 공간복잡도 O(1)

* 거품 정렬은 최악의 종류의 정렬이다. 다른 정렬 알고리즘은 배열의 이미 정렬된 부분을 활용하는데 비해 거품정렬은 모든 가능한 짝을 모두 비교하기 때문이다.
