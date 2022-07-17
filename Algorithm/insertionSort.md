# 삽입정렬
> 삽입정렬이 삽입정렬인 이유 정렬을 할때 알맞은 자리를 찾아서 삽입을 하기 때문이다.

## 동작 방법 

1. 정렬된 partial 어레이를 유지하며 한 칸씩 늘려가며 정렬
2. 한 칸 늘릴 때 새로 삽입된 데이터를 정렬된 array에서 맞는 자리로 위치시킨다.
3. 탐색 범위
    * Outer : 1 → n
    * Inner : j >= 0 && arr[i] > key
      * 정렬된 array를 끝까지 탐색을 안했고,(그리고)
      * 현재 값 보다 키가 더 작으면 → 왼쪽으로 이동하라
4. 시간 복잡도 
    * Worst O(n<sup>2</sup>)
    * Average O(n<sup>2</sup>)
    * Best O(n<sup></sup>)

## 예시
```
arr = [7, 8, 2, 9, 4, 6]
const insertionSort = function (arr) {
  for(let i = 1; i < arr.length; i++){
    let key = arr[i];
    let j = i - 1;

    while(j >= 0 && arr[j] > key){
      arr[j + 1]= arr[j]
      j--;
    }
    arr[j+1] = key 
  }
  return arr
};
```
<img src="https://github.com/anotheranotherhoon/TIL/blob/master/Algorithm/img/insertionSort1.jpg"  width="600" height="900"/>

<img src="https://github.com/anotheranotherhoon/TIL/blob/master/Algorithm/img/insertionSort2.jpg"  width="600" height="900"/>

* while 반복문에서 j>=0이 false 인 경우
    * j가 -1 경우가 유일한 경우이다. 
    * arr의 가장 왼쪽 즉 가장 작은 수가 될경우 arr[0] 즉, 가장 작은 수로 key를 할당해준다.

* while 반복문에서 arr[j] > key가 false 일 경우 
  * arr[j]가 key 보다 작거나 같을 경우이다. 
  * 즉, arr[j]보다 key가 크거나 같다는 의미이다.
  * 따라서 arr[j+1]을 key로 할당해 준다.
