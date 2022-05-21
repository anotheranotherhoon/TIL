# flexbox
>2022년05월03일
```
* {
  box-sizing: border-box;
}

body {
  margin: 0;
  padding: 0;
}
```
기본 스타일링을 제거하는 CSS 코드


## 부모요소에 적용해야 하는 flexbox 속성
자식 요소들의 정렬과 관련이 있었다.

display:flex; 를 자식요소가 아닌 부모 요소에 적용해야 한다.

flex-direction 속성은 자식 요소들을 정렬할 정렬 축을 결정합니다. 입력할 수 있는 값으로는 row, column, row-reverse, column-reverse가 있습니다. **아무 설정도 해주지 않으면 기본적으로 row 정렬을 합니다.**

## 자식 요소에 적용해야 하는 flexbox 속성

```
flex: <grow(팽창 지수)> <shrink(수축 지수)> <basis(기본 크기)>

flex 속성을 따로 설정해주지 않으면 다음과 같은 기본값이 적용되며 왼쪽에서 부터 오른쪽으로 컨텐츠의 크기만큼 배치된다.

flex: 0 1 auto;
```
flex: **0** 1 auto
flex 속성을 설정하기 전에 grow의 기본 값인 0은 빈 공간이 있어도 늘어나지 않음을 의미한다. 

basis: basis(기본 크기) 는 자식 박스가 flex-grow 나 flex-shrink 에 의해 늘어나거나 줄어들기 전에 가지는 기본 크기이다. 

## 스스로 공부한 부분
참고 : https://heropy.blog/2018/11/24/css-flexible-box/

## 부모 요소에 설정해야 하는 flex 속성
dispaly: flex
flex-direction 의 기본 값은 flex-direction : row이다.
그래서 구역별로 flex-direction을 column등 다른 값을 주려고 할 때는 구열의 부모태그에 display:flex;과 flex-direction: 값을 다시 설정 해줘야한다.

## 자식 요소에 설정해야 하는 flex 속성
flex-grow를 제외한 개별 속성은 생략할 수 있다.

만약 flex: 1;로 작성하면 flex-grow: 1;과 같다.
그러면 나머지 속성은 생략했으니 기본값이 적용되어 flex-shrink: 1;, flex-basis: auto;가 될까?
즉 flex: 1; 혹은 flex: 1 1;은 flex: 1 1 auto;와 같다고 생각할 수 있지만 그렇지 않다.

flex-basis의 기본값은 auto이지만 단축 속성인 flex에서 그 값을 생략할 경우 0이 적용됩니다.
다시 정리하면 flex: 1; 혹은 flex: 1 1;은 flex: 1 1 0;이 된다.


## display 프로퍼티
## block 레벨 요소
block 특성을 가지는 요소(block 레벨 요소 또는 block 요소)는 아래와 같은 특징을 갖는다.
- 항상 새로운 라인에서 시작한다.
- 화면 크기 전체의 가로폭을 차지한다.(width: 100%)
- block 레벨 요소 내에 inline 레벨 요소를 포함할 수 있다.
- block 레벨 요소 예
> div
h1 ~ h6
p
ol
ul
li
hr
table
form

## inline레벨 요소
inline 특성을 가지는 요소(inline 레벨 요소 또는 inline 요소)는 아래와 같은 특징을 가진다.

- 새로운 라인에서 시작하지 않으며 문장의 중간에 들어갈 수 있다. 즉, 줄을 바꾸지 않고 다른 요소와 함께 한 행에 위치한다.
- content의 너비만큼 가로폭을 차지한다.
- width, height, margin-top, margin-bottom 프로퍼티를 지정할 수 없다. 상, 하 여백은 line-height로 지정한다.
- inline 레벨 요소 뒤에 공백(엔터, 스페이스 등)이 있는 경우, 정의하지 않은 space(4px)가 자동 지정된다.
- inline 레벨 요소 내에 block 레벨 요소를 포함할 수 없다. inline 레벨 요소는 일반적으로 block 레벨 요소에 포함되어 사용된다.
> span
a
strong
img
br
input
select
textarea
button



## 부모영역에 적용하는 flex 속성(flexcontainer)
flex item이 배치된 방향이 main axis 메인 축이다.
```
.container {
	flex-direction: row 기본값
}
```

"justify"는 메인축(오뎅꼬치)방향으로 정렬
"align"은 수직축(오뎅을 뜯어내는) 방향으로 정렬

justify-content: flex-start(기본 값)

align-items: stretch(기본 값)

여러 행 정렬(align-content) flex-wrap: nowrap (기본 값)
flex-wrap:wrap;이 설정된 상태에서, 아이템들의 행이 2줄 이상 되었을 때의 수직축 방향 정렬을 결정하는 속성이다. 

## 자식요소에 적용하는 flex속성(flexitem)
## flex-basis (flex-basis: auto 기본값)

flex-basis는 flex아이템들의 기본크기를 설정한다. (flex-direction:row일 때는 너비, flex-direction: column일 때는 높이)

## flex-grow
(flex-grow:0 기본 값)
flex-grow에는 숫자값이 들어가는데, 몇이든 일단 0보다 큰 값이 세팅이 되면 해당 아이템이 유연한(Flexible) 박스로 변하고  원래의 크기보다 커지며 빈 공간을 메우기 된다. 기본 값이 0이기 때문에, 따로 적용하기 전까지는 아이템이 늘어나지 않았다.

flex-grow에 들어가는 숫자의 의미는, 아이템들의 flex-basis를 제외한 여백 부분을 flex-grow에 지정된 숫자의 비율로 나누어 가진다고 생각하면 된다. 

