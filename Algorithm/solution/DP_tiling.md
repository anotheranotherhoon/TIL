# 타일링 문제
* 세로 길이 2, 가로 길이 n인 2 x n 보드가 있습니다.
* 2 x 1 크기의 타일을 가지고 이 보드를 채우는 모든 경우의 수를 리턴하라.


## 입력
* 인자 1: n
    * number 타입의 1이상의 자연수

## 출력
* number 타입을 리턴해야한다.

## 풀이

<img src="https://github.com/anotheranotherhoon/TIL/blob/master/Algorithm/img/DP_tiling.jpg"  width="600" height="900"/>

```js
let tiling = function (n) {
  const dy = [0, 1, 2];
  if (n <= 2) return dy[n];
  for (let i = 3; i <= n; i++) {
    dy[i] = dy[i - 1] + dy[i - 2];
  }
  return dy[n];
};
```

* 타일이 가로로 무수히 많더라도 
    * 1. 맨 끝에 한 칸이 2x1(세로 * 가로)로 놓일 경우와 (i-1)
    * 2. 맨 끝에서 두 번째 칸 2x2(세로 * 가로)가 타일 두 개가 모두 가로로 놓을 경우 (i-2) 
    * 3. 맨 끝에서 두 번째 칸 2x2(세로 * 가로)가 타일 두 개가 모두 세로로 놓일 경우는 1번의 상황에 포함되는 상황이므로 배제한다.

* 두 가지 경우 밖에 없다. 따라서 dy[i-1]과 dy[i-2]를 더한 값이 정답이된다.
