### 21강 - 코드 초기화와 엘리먼트 객체 선택하기  

20강에서 btnPrint가 정의되기 이전에 script block에서 이를 사용하여(btnPrint.onclick = printResult;) 에러가 발생한 상황을 접했다.
이를 해결하기 위한 방법으로 가장 쉬운 방법은 script block을 btnPrint가 선언된 이후로 옮기는 방법이 있지만 
코드가 굉장이 납잡해진다는 단점을 가진다. 그렇다면 다른 방법으로는 무엇이 있을까?


이벤트 중에 해당 객체가 다 load되었을때 발생하는 이벤트가 있다. window 객체는 script block에 있는 코드가 실행되기 전에 가장 먼저 생성되는 객체임(다만 문서가 완료되지 않은 상태)으로 이를 이용하여 winodw객체가 모두 load된 후에 btnPrint.onclick = printResult;를 실행하게 하면 된다.

```html
<script>
function printResult()
{
    var x,y;
    x= parseInt(prompt("x값을 입력하세요",0)); 
    y= parseInt(prompt("y값을 입력하세요",0));

    btnPrint.value=x+y;

} 
function init(){
    btnPrint.onclick = printResult;
}
window.onload = init;
</script>

</head>
 <body>
         <input type="button" value="클릭" onclick="printResult()" id = "btnPrint"/>    
 </body>
```  
위와 같이 코드를 작성하면 window객체가 로드가 되면 init함수가 호출된다. init 함수내부의 코드를 실행할때는 이미 btnPrint가 정의되어 있으므로 에러가 발생하지않는다.  
  
위의 코드에서 문제가 하나 있다. html 명명규칙에 따르면 id의 속성값은 "btnPrint"가 아니라 "btn-print"로 작성해야한다.
하지만 이 명명규칙에 따르면 javascript에서는 오류가 발생한다. 그럼 html에서 명명규칙을 어기며 btnPrint를 사용해야할까? 그렇지않다.
다음 코드를 사용하면 된다.  
```html
<script>
function printResult()
{
    var btnPrint = document.getElementById("btn-print");
    var x,y;
    x= parseInt(prompt("x값을 입력하세요",0)); 
    y= parseInt(prompt("y값을 입력하세요",0));

    btnPrint.value=x+y;

} 
function init(){
    var btnPrint = document.getElementById("btn-print");
    btnPrint.onclick = printResult;
}
window.onload = init;
</script>

</head>
 <body>
         <input type="button" value="클릭" onclick="printResult()" id = "btn-print"/>    
 </body>
```  
그런데 수정된 코드에서도 var btnPrint = document.getElementById("btn-print"); 코드가 중복되는 비효율적인 부분이 보인다.
이를 전역변수로 선언하면  
```html
<script>
var btnPrint = null;
function printResult()
{
    var x,y;
    x= parseInt(prompt("x값을 입력하세요",0)); 
    y= parseInt(prompt("y값을 입력하세요",0));

    btnPrint.value=x+y;

} 
function init(){
    var btnPrint = document.getElementById("btn-print");
    btnPrint.onclick = printResult;
}
window.onload = init;
</script>

</head>
 <body>
         <input type="button" value="클릭" onclick="printResult()" id = "btn-print"/>    
 </body>
``` 
위 코드와 같이 코드를 간략하게 나타낼 수 있다. 하지만 script 내에서 전역변수를 사용하는 것은 바람직한 방법이 아니다. 충돌이 날 가능성이 높아지기 때문이다. 그렇다면 어떤 방법으로 위의 코드를 간략하게 만들 수 있을까?
