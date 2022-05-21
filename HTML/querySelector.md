# querySelector()
>2022년05월22일

1. querySelector의 첫 번째 인자에 'div'를 넣으면 어떻게 될까?

html파일 내에서 가장 최상단 즉, 가장 먼저 나온 div element객체가 선택된다.

2. querySelector의 부모는 꼭 document 객체여야만 할까?'
document 하위의 어떤 객체든 자식 element를 가지고 있다면 querySelector의 부모가 될 수 있다. 
```
<body>
<div id="myDIV">
  <p>This is a p element in div.</p>
  <p>This is also a p element in div.</p>
</div>
<p>Click the button to change the text of the first p element in div.</p>
<button onclick="myFunction()">Try it</button>

<script>
function myFunction() {
  var x = document.getElementById("myDIV");
  x.querySelector("p").innerHTML = "Hello World!";
}
</script>
```
