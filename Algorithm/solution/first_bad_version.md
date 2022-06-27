# First Bad Version [문제](https://leetcode.com/problems/first-bad-version/)
> binary search
```
var solution = function(isBadVersion) {
    return function(n) {
        let s = 1, e = n
        while(s < e) {
            let m= s + Math.floor((e-s)/2)
            if(isBadVersion(m)) {
                e = m
            } else {
                s = m + 1
            }
        }
        return s
    };
};
```


<img src="https://github.com/anotheranotherhoon/TIL/blob/master/Algorithm/img/first_bad_version1.jpg"  width="600" height="900"/>

<img src="https://github.com/anotheranotherhoon/TIL/blob/master/Algorithm/img/first_bad_version2.jpg"  width="600" height="900"/>

* 이분 탐색 완전히 배제해도 되는 부분이 어디인지 잘 생각해야한다.

* 전형적인 이분 탐색의 경우 타겟 넘버가 맞는지 아닌지 찾아내야 했다면 위 문제의 경우 최초의 참인 값을 찾는 문제였다. 

* 그래서 어떠한 경우에 s와 e 값을 m에서  1을 더 증가시켜야하는지 그냥 m이 되어야하는지 생각하는데 시간이 걸렸다.

* 최초의 true(index가 가장 작은) 따라서 답은 무조건 isBadVersion() 함수에 넣었을 때 true여야한다. 

* true라면 그 값을 제외한 이후의 값들은 모두 답이 되지 않으므로 배제한다.

* false라면 애초에 답이 되지 않으므로 false를 포함한 그 이전 값들은 모두 답이 되지 않으므로 배제한다. 