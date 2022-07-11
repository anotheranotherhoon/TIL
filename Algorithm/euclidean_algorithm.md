# 유클리드 호제법 
> * 참조 [유클리드호제법](https://www.youtube.com/watch?v=R1gxRwXRpMQ)

* 유클리도 호제법이란 최대 공약수를 쉽게 구하는 방법이다.

## 유클리드 호제법 사용 방법

* 1. 큰 수를, 작은 수로 나눈다.

* 2. 나눈 수를 나머지로 계속 나눈다.

* 3. 나머지가 0일 경우 나눈 수가 최대 공약수다.

<img src="https://github.com/anotheranotherhoon/TIL/blob/master/Algorithm/img/euclide.jpg"  width="600" height="900"/>

## 최소 공배수
* 두 수의 최대소 공배수는 두 수의 곱을 최대공약수로 나눈 값이다.  

```js
function solution(n, m) {
    // 최대공약수 구하기
    // 1. n과 m을 비교하여 큰 값과 작은 값을 찾아내 big, small 변수에 할당한다.
    // 2. big을 small로 나누고 나머지를 (remain변수에 할당한다.)
    // 2-1. big에 small값을 재할당하고 small에 remain값을 재할당한다.
    // 반복하면서 remain(나머지)이 되면 small값이 최대공약수가된다.
        let answer = [];
        let big = Math.max(n, m)
        let small = Math.min(n,m)
        // let temp 
    function gcd(big, small){
        if(big % small === 0){
            answer.push(small)
            return
        }else{
            [big, small] = [small, big % small]
            // temp = big % small
            // big = small
            // small = temp
            gcd(big, small)
    }
    }
    
    gcd(big, small)
    answer.push(n*m / answer[0]) //최대 공배수 구하기
    return answer;
}
```
* 처음에는 큰 수를 작은 수로 꼭 나눠야한다고 생각하여 대소비교를 해주었다.
```js
function solution(n, m) {
        let big = Math.max(n, m)
        let small = Math.min(n,m)
    function gcd(big, small){
        if(big % small === 0){
            answer.push(small)
            return
        }else{
            [big, small] = [small, big % small]
            gcd(big, small)
    }
    }
    gcd(big, small)
    answer.push(n*m / answer[0])
    return answer;
}
```
* 그리고 최종적으로 리팩터링을 통해 위와 같은 답을 만들었다. 
* 하지만 사실 대소비교를 할 필요가 없었다.
* 작은 수를 큰 수로 나눌 경우 몫은 0이 되고 나머지는 작은 수가 그대로 반환된다. 
* 따라서 다음 순서에 나눈 수를 나머지로 나누는 과정에서 큰 수를 작은 수로 나누는 식이 되게 되있다. 

<img src="https://github.com/anotheranotherhoon/TIL/blob/master/Algorithm/img/euclide2.jpeg"  width="600" height="900"/>

```js
function solution(n, m) {
    function gcd(n, m){
        if(n % m === 0){
            answer.push(m)
            return
        }else{
            [n, m] = [m, n % m]
            gcd(n, m)
    }
    }
    gcd(n, m)
    answer.push(n*m / answer[0])
    return answer;
}
```

---

## 정리 
* 유클리드 호제법 (최대 공약수 구하기)
1. 두 수 (순서는 상관 없다.)를 나눈다. 
2. 나눈 수를 나머지로 계속 나눈다.
3. 나머지가 0일 경우 나눈 수가 최대 공약수다.

* 최소 공배수 구하기

두 수의 곱을 최대 공약수로 나눈 수가 최소 공배수이다.