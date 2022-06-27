# 버블정렬
* 정수를 요소로 갖는 배열을 입력받아 오름 차순으로 정렬하여 리턴해야 한다.
> * 입력
>   * 인자 1: arr
>       * number 타입을 요소로 갖는 배열
>       * arr[i] 는 정수
> * 출력
>   * number 타입을 요소로 갖는 배열을 리턴해야 합니다.
>   * 배열의 요소는 오름차순으로 정렬되어야 합니다.
>   * arr[i] <= arr[j] (i < j)

## 문제 풀이 
> bubbleSort([1, 2, 43, 100, 100, 21])
```
const bubbleSort = function (arr) {
  for(let i = 0; i<arr.length; i++){
    for(let j = 0; j<arr.length-i-1; j++){
      if(arr[j]>arr[j+1]){
        [arr[j+1], arr[j]] = [arr[j], arr[j+1]]
      }
    }
    if(check===false){
      return arr
    }
  }
  return arr
};
```
* 최초에는 이렇게 풀었고 이게 일반적인 풀이이다. 하지만 Advance에서 수행시간을 단축할 수 있다.
<img src="https://github.com/anotheranotherhoon/TIL/blob/master/Algorithm/img/bubble_sort_1.jpg"  width="600" height="900"/>


<img src="https://github.com/anotheranotherhoon/TIL/blob/master/Algorithm/img/bubble_sort_2.jpg"  width="600" height="900"/>


## Advance 문제풀이
```
const bubbleSort = function (arr) {
  // TODO: 여기에 코드를 작성합니다.
  for(let i = 0; i<arr.length; i++){
    let check = false
    for(let j = 0; j<arr.length-i-1; j++){
      if(arr[j]>arr[j+1]){
        [arr[j+1], arr[j]] = [arr[j], arr[j+1]]
        check=true
      }
    }
    if(check===false){
      return arr
    }
  }
  return arr
};

```
* 수행 시간을 단축하기 위해 check을 추가했다. 
* 배열을 한 바퀴 도는 동안 한번도 교체하지 않았다면 오름차순으로 정렬이 완료된 배열이므로 더 이상 반복을 진행하지 않고 배열을 리턴하고 함수를 종료한다.