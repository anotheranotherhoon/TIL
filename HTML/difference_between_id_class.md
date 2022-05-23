# id 속성과 class 속성의 차이

## 1. id
 * id의 전역특성<sup>Global attributes</sup> 은 문서 전체에서 유일한 고유식별자라는 것이다.
* 고유식별자의 목적은 프래그먼트 식별자를 사용해 요소를 가르킬 때와 스크립트 및 스타일 적용 시 특정 요소를 식별하기 위함이다. 

> 프래그먼트란 문서내에서 바로가기 버튼 처럼 일종의 북마크와 같이 기능한다. 

> HTML 문서 상에서, 브라우저는 앵커가 정의된 지점으로 스크롤 될 것이다.

![](https://github.com/anotheranotherhoon/TIL/blob/master/HTML/img/difference_between_id_class.mov?raw=true)

```
<a href="#one"></a>
<p id="one">one</p>
```

## 1-1. id의 특징
* id 특성의 값이 공백(스페이스나 탭)을 포함해서는 안된다. 하지만 class는 공백을 통해서 복수의 class를 가질 수 있다.

* 따라서 하나의 요소는 하나의 ID만 가질 수 있다.
* 만약 공백이 있다면 브라우저는 공백마저도 ID의 일부로 취급한다.

* ASCII문자, 숫자, _, -, 및 . 을 제외한 문자는 HTML4에서 허용되지 않았므로 호환성의 문제가 발생할 수 있다.
* 이러한 제한은 HTML5에서는 해제되었으나 호환성을 위해 ID는 위의(ASCII문자, 숫자, _, -, 및 . ) 문자로 시작해야한다.

## 2. class
* class의 전역특성<sup>Global attributes</sup>은 공백으로 요소 클래스의 목록으로, 대소문자를 구분하지 않는다. 클래스는 CSS나 JavaScript에서 클래스 선택자나 DOM메서드의 document.getElementsByClassName()과 같은 메서드를 통해 요소에 접근할 수 있는 방법이다.

* 

## 2-1. class의 특징
* 클래스의 명칭에 대한 요구사항을 제시하지는 않지만 개발자는 해당 요소의 표시 방식보다 *요소의 의미*와 목적을 설명하는 명칭을 사용하는 것이 좋다.

여러가지 스타일링을 한꺼번에 적용해야 할 때는 클래스(class)를 사용하고 한가지만 적용하고 싶다면 아이디(id)를 사용하면된다.

id는 고유하다.
getElementById id를 여러번 쓰는거 시멘틱하지 않다. 웹 표준 xㅌ
getElementsByClass