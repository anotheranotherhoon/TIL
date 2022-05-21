# 삼항조건문
>2022년 05월 16일

삼항연산자로 if else 문처럼 복수의 라인을 실행 시키려고 하면 에러가 발생한다.

```

let a = 1, b = 1, c = 1, d = 1;

a > 0 ? b+=1; c+=1 : d += 1 ; ① ; 사용

a > 0 ? b+=1, c+=1 : d += 1 ; ② , 사용

a > 0 ? b+=1 c+=1 : d += 1 ; ③ 공백 사용


Uncaught SyntaxError: Unexpected token ';'①
Uncaught SyntaxError: Unexpected token ','②
Uncaught SyntaxError: Unexpected identifier ③
```



삼항연산자를 이용해서 복수라인의 코드를 실행하는 두 가지 방법


1. 익명함수로 만든다.
```
let a = 1, b = 1, c = 1, d = 1;

a > 0 ? function(){b+=1; c+=1}() : d += 1 ;

console.log(a, b, c, d)// 1 2 2 1
```

2. 복수라인을 괄호로 감싸고 ,(comma)로 구분해준다.
```
let a =1, b =1, c = 1, d = 1, e = 1, f = 1; 

a > 0 && b > 0 ? (c += 1, d+=1 ) : (e += 1, f +=1 );

console.log(a, b, c, d, e, f); // 1 1 2 2 1 1

```

> 삼항연산자는 일반적으로 간단한 한 줄의 조건과 한 줄의 리턴값을 깔끔하게 나타내기 위한 문법이다. if 구문을 좀 더 멋지고 짧게 나타내기 위함이다.<br>
하지만 복수라인의 경우 삼항 연산자를 쓴 것이 if 구문보다 더 복잡해 보인다.<br>
삼항연산자를 굳이 사용하는 것 보다 if구문을 사용하는 것이 좀 더 가시성과 직관성이 좋다.