# 프로그래머스 위장[문제](https://programmers.co.kr/learn/courses/30/lessons/42578)

## 풀이
```js
function solution(clothes) {
    let answer = 1;
    const map = new Map();
    for(let item of clothes){
        const key = item[1];
        if (map.has(key)) map.set(key, map.get(key)+1);
        else map.set(key, 1);
    }
    map.forEach((item)=> answer *= item + 1);
    return answer - 1
}
const clothes = [["yellow_hat", "headgear"], ["blue_sunglasses", "eyewear"], ["green_turban", "headgear"]];
solution(clothes)
```
1. for 반복문을 통해 clothes 배열의 요소들이 하나 씩 item으로 들어온다. 가장 먼저 ["yellow_hat", "headgear"]가 들어온다.

2. key변수에 item의 1번 째 인덱스값 "headgear"가 할당된다.

3. 조건문에 의해서 map은 지금 비어 있기 때문에 key인 headgear를 갖고 있지 않으므로 false 따라서 else문이 실행되어 map에 {"headgear" =>  1}가 추가 된다.

4. 두 번째 요소인 ["blue_sunglasses", "eyewear"] 도 첫 번째 요소와 마찬가지로 진행 되어 {"eyewear" =>  1}가 추가 된다.

5. 특이점은 세 번쨰 요소인 ["green_turban", "headgear"]에서 발생한다. 조건문에서 map은 headgear를 가지고 있으므로 map.set("headgear", map.get(headgear) +1 )즉
("headgear", 2)로 값이 덮어 써진다.<br> `Map객체는 중복된 키를 갖는 요소가 존재할 수 없기 때문에 중복된 키를 갖는 요소를 추가하면 값이 덮어 써진다.`

6. 반복문을 마친 결과 map은 Map(2) {"eyewear" => 1, "headgear" => 2} 이런 상태를 갖는다.

7. map.forEach를 통해 첫 번째 인자만을 가지므로 요소값을 순회한다.
8. answer = answer * (1+1) // answer = 1 * 2 = 2
9. answer = answer * (2+1) // answer = 2 * 3 = 6
10. 그 다음에 answer 에 1을 빼준다.


## 의상을 입는 모든 경우의 수
1. yellow_hat
2. blue_sunglasses
3. green_turban
4. yellow_hat + blue_sunglasses
5. green_turban + blue_sunglasses



## 풀이 아이디어

* 같은 이름을 가진 의상은 존재하지 않으므로 의상의 이름은 알 필요가 없다. 즉 의상의 종류를 구분하여 종류의 갯수를 구한다.

* 각 의상 종류 내에서도 옷을 선택 할 수도 , 안할 수도 있다. 따라서 각 의상 종류 별로 의상을 고르는 경우의 수는 의상 개수 + 1이다.

* 모든 의상 종류 내에서 의상을 고르지 않는 경우, 즉 아무 것도 입지 않는 경우를 빼야한다.(answer - 1)

