# 복잡도
> 참고 면접을 위한 CS 전공지식 노트
## 1. 시간 복잡도 Time Complexity
* 시간 복잡도란 '문제를 해결하는 데 걸리는 시간과 입력의 함수 관계'를 가리킨다. 

* 어떠한 알고리즘의 로직이 '얼마나 오랜 시간'이 걸리는지를 나타내는 데 쓰이며, 보통 빅오 표기법으로 나타낸다.

## 2. 빅오 표기법
* 빅오 표기법이란 입력 범위 n을 기준으로 해서 최악의 경우 로직이 몇 번 반복되는지 나타내는 것이다.

* '가장 영향을 많이 끼치는' 항의 상수 인자를 뺴고 나머지 항을 없앤다.

* `ex)` 10n<sup>2</sup> + n 을 빅오 표기법으로 나타내면 O(n<sup>2</sup>)이다.

* 다른 항들이 신경 쓰일 수도 있지만 증가 속도를 고려한다면 그렇지 않다. 

* 입력 크기가 커질수록 연산량이 가장 많이 커지는 항은 n의 제곱이고 다른 것은 미미하므로 신경쓰지 않는다.

## 2. 시간복잡도가 필요한 이유

* 시간복잡도가 필요한 이유는 효율적인 코드로 개선하는데 쓰이는 척도가 되기 때문이다.

* O(n<sup>2</sup>) 보다  O(n)을  그보다  O(1)이 더 효율적인 코드다.


## 4. 공간 복잡도
* 공간 복잡도는 프로그램을 실행 시켰을 때 필요로 하는 자원 공간의 양을 말한다.

* 정적 변수로 선언된 것 말고도 동적으로 재귀적인 함수로 인해 공간을 계속해서 필요로 할 경우도 포함한다.

* 자료 구조의 평균 시간 복잡도
|자료 구조|접근|탐색|삽입|삭제|
|------|---|---|---|---|
|배열(array)|O(1)|O(n)|O(n)|O(n)|
|해시테이블|O(1)|O(1)|O(1)|O(1)|
|이진 탐색 트리(BST)|O(logn)|O(logn)|O(logn)|O(logn)|

* 자료 구조 최악의 시간 복잡도

|자료 구조|접근|탐색|삽입|삭제|
|------|---|---|---|---|
|배열(array)|O(1)|O(n)|O(n)|O(n)|
|해시테이블|O(n)|O(n)|O(n)|O(n)|
|이진 탐색 트리(BST)|O(n)|O(n)|O(n)|O(n)|