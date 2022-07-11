# 121. Best Time to Buy and Sell Stock[문제](https://leetcode.com/problems/best-time-to-buy-and-sell-stock/)
> * 입력
>   * 인자 1: arr
>       * number 타입을 요소로 갖는 배열
>       * arr[i] 는 정수
> * 출력
>   * number 타입을 리턴 해야 한다.

* 그날의 주식 가격을 나타내는 배열이 주어진다. arr[i]는 i번째 날의 주식 가격이다.
* 주식을 구매할 날을 선택하고 그 주식을 팔기 위해 미래에 다른 날을 선택함으로써 이익을 극대화하고자 합니다.
* 이 거래에서 얻을 수 있는 최대 이익을 반환하세요. 이익을 얻을 수 없으면 0을 반환하십시오.

> 자신이 구매한 날 이후의 날짜에 그 날짜에 해당하는 주식의 가격으로 팔 수 있으며 그 값을 최대가 되게 하고 최대가되는 그 값을 반환하라.

## 처음 작성한 답안 하지만 시간 초과에 걸리고 만다.
```js
var maxProfit = function(prices) {
    const dy = Array.from({length:prices.length}, ()=>0)
    for(let i = 0 ; i < prices.length; i++){
        for(let j = i+1; j<prices.length; j++){
            if(dy[i] < prices[j]-prices[i]){
                dy[i] = prices[j]-prices[i]
            }
        }
    }
    const answer = Math.max(...dy)
    return answer
};
```
## 풀이 과정 
* dy를 prices의 수 만큼 0으로 초기화 한다.
* 반복문을 두 번 돌아서 첫 번째 반복문(i)은 구매 날짜 두 번쨰 반복문(j)는 판매 날짜로 생각한다. (판매 날짜 이므로 j = i+1 로 시작한다.)
* j를 주식의 마지막 날 가격까지 돌면서 dy[i]와 비교하여 이익이 클 경우 dy[i]를 갱신 해준다. 
* 초기 값을 0으로 했기 때문에 손해를 보더라도 적어도 0을 리턴하여 이익을 얻을 수 없으면 0을 반환한다는 조건을 만족시켜준다.
* 반복문을 돌고난 다음 dy중 최대 값을 answe 변수에 할당하고 최종적으로 answer를 반환한다.
* 하지만 시간 초과에 걸린다.

## DP를 이용한 풀이

```js
var maxProfit = function(prices) {
    const dy = Array.from({length:prices.length}, ()=>0)

    if (prices===[]) return 0

    dy[dy.length-1] = prices[prices.length-1]

    let result = Number.MIN_SAFE_INTEGER

    for(let i = prices.length-2; i>=0; i--){
        dy[i] = Math.max(dy[i+1], prices[i])
    }

    for(let j= 0 ; j<prices.length; j++){
        result = Math.max(result, dy[j]-prices[j])
    }

    return result
    
}
```
<img src="https://github.com/anotheranotherhoon/TIL/blob/master/Algorithm/img/bestTime1.jpg"  width="600" height="900"/>

* 첫 번째 반복문을 통해 얻게 되는 dy는 자신을 포함해서 남은 일수 중 주식의 가장 비싼 가격을 저장한다. 
* dy의 마지막 요소는 그 이후의 남은 일수가 없으므로 자기 자신을 갖는다.

<img src="https://github.com/anotheranotherhoon/TIL/blob/master/Algorithm/img/bestTime2.jpg"  width="600" height="900"/>

* 두 번째 반복문을 통해 자신을 포함해서 남은 일수와 당일 자신이 구매한 주식의 가격 즉, 이익과 현재까지의 최대 이익을 비교한다.

