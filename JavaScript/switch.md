
# switch(){}
>2022년05월06일
switch 문은 주어진 표현식을 평가하여 그 값과 일치하는 표현식을 갖는 case 문으로 실행 흐름을 옮긴다. case 문은 상황을 의미하는 표현식을 지정하고 콜론으로 마친다. 그리고 그 뒤에 실행할 문들을 위치시킨다.

switch 문의 표현식과 일치하는 case문이 없다면 실행 순서는 default문으로 이동한다. default 문은 선택사항으로, 사용할 수도 있고 사용하지 않을 수도 있따. 

```
switch(x) {
  case 'value1':  // if (x === 'value1')
    ...
    break

  case 'value2':  // if (x === 'value2')
    ...
    break

  default:
    ...
   
}
```
if ... else 문의 조건식은 불리언 값으로 평가되어야 하지만 switch 문의 표현식은 불리언 값보다는 문자열이나 숫자 값인 경우가 많다. 

다시 말해, if ... else문은 논리적 참, 거짓으로 실행할 코드 블록을 결정한다. 

switch문은 논리적 참, 거짓보다는 다양한 상황(case)에 따라 실해할 코드 블록을 결정할 때 사용한다. 

default문에는 break문을 생략하는 것이 일반적이다. default문은 switch문의 맨 마지막에 위치하므로 default 문의 실행이 종료되면 switch 문을 빠져나간다. 따라서 break 문이 필요 없다.

만약 if ... else 문으로 해결할 수 있다면 switch 문보다 if ... else 문을 사용하는 편이 좋다. 하지만 조건이 너무 많아서 if ... else 문보다 switch 문을 사용했을 때 가독성이 좋다면 switch문을 사용하는 편이 좋다.


## 모든 자식문 돌면서 확인하기

```
const buttons = calculator.querySelector('.calculator__buttons');
const buttonContainerArray = buttons.children;

for (let i = 0; i < buttonContainerArray.length; i++) {
      const childrenArray = buttonContainerArray[i].children;
      for (let j = 0; j < childrenArray.length; j++) {
        childrenArray[j].classList.remove('isPressed');
      }
    }
```

모든 클래스를 돌면서 "isPressed" 클래스이 있으면 없애준다.


