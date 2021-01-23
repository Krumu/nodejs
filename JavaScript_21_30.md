### 21강 - 코드 초기화와 엘리먼트 객체 선택하기  
---  
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



### 22강 - 스크립트 코드의 지역화
---  
이벤트를 처리하기 위한 함수는 명명할 필요가 없으며 그 함수가 한 번만 사용된다면 더더욱 함수의 이름이 필요가 없다. 익명함수로 전 시간에 공부한 코드를 수정해보면
```html
<script>
window.onload = function init(){
    var btnPrint = document.getElementById("btn-print");
    btnPrint.onclick = function(){
        var x,y;
        x= parseInt(prompt("x값을 입력하세요",0)); 
        y= parseInt(prompt("y값을 입력하세요",0));

        btnPrint.value=x+y;
    };
};
</script>
</head>
 <body>
         <input type="button" value="클릭" onclick="printResult()" id = "btn-print"/>    
 </body>
```  
### 23강 - 코드분리와 이벤트 바인딩 방법 두 가지
---   
#### 1) 코드분리
코드 작성시 html 문서안에 script를 작성할 수 있는데 이는 분업화해서 프로그램을 만드는 경우 문제가 될 수 있음.
```html
<script src="파일이름"></script>
```  
#### 2) 이벤트 바인딩 방법

```html
window.onload = function(){alert("test1");}
window.onload = function(){alert("test2");}
```  
윈도우 객체가 로드되었을때 위의 두 함수를 모두 호출하고 싶어서 위와 같이 코드를 작성하면 원하는 결과를 얻을 수 없다. 앞에서 대입한 내용을 뒤에서 대체하기 때문에 뒤의 함수만 호출이 됨. 이를 해결하려면 이벤트를 처리해주는 함수들이 누적이 되도록 해주면 된다.

```html
winodw.addEventListener("load",function(){
    alert("test1");
});
winodw.addEventListener("load",function(){
    alert("test2");
});
```  

### 24강 - 첫 예제 간단한 계산기 프로그램 만들기  
### 25강 - 노드 선택 방법 개선하기  
---  
```html  
<section>
   <h1></h1>
   <ul>
      <li id="num1">번호1</li>
      <li id="num2">번호2</li>
      <li id="num3">번호3</li>
   </ul>
<section>
```  
엘리먼트를 사용할때 마다 각 태그에 id속성을 만들어야하나? 그러기엔 너무 번거롭다.

```html  
<section id = "sec1">
   <h1></h1>
   <ul>
      <li>번호1</li>
      <li>번호2</li>
      <li>번호3</li>
   </ul>
<section>
```  
위와 같이 작성한 후에
```javascript
var lis = sec1.getElementsTagName("li");
li[0].textContent = "Hello"; // li[0].innerText="Hello";
```  
로 작성하면 모든 엘리먼트에 id를 부여할 수고를 덜 수 있다. 그런데 이런 경우에도 문제가 발생할 수 있다.
새로운 li 태그를 넣거나 태그의 순서를 변경하면 javascript에서의 인덱스도 변경해주어야 하며, 코드 작성이후에 인덱스가 의미하는 태그가 무엇이였는지를 확인해야하는 상황이 발생한다. 또한 그룹마다 동일한 의미의 li 들이 있어도 id는 두 개이상이 될 수 없으니 효율적으로 사용 할 수 없다. 이 때 class를 사용하면 된다.(단, getElementsByClass를 하면 배열을 가지고 오므로 요소가 1개일 경우도 [0]와 같이 인덱스를 붙여서 사용할 것)  


### 26강 - Selectors API    
---  
selctors API를 사용하면 편리하게 노드선택을 할 수 있다.(querySelector(), querySelectorAll())
```javascript
var txtX = section3.querySelector("[css selector]");
```
css selector의 표현방법이 풍부하고 정밀하기때문에 이를 이용하여 검색하거나 select하는것은 정말 편리함.

### 27강 - Node와 Element Node 그리고 childNodes, children
---   
계보를 이용해서 노드를 선택할 수도 있다.  
```html
<section id = "section4">
   <h1>Ex4 : childNodes를 이용한 노드 선택 </h1>
      <div class = "box">
          <input />
          <input />
      </div>
</section>

```

```javascript
window.addEventListener("load",function(){
    var section4 = document.querySelector("#section4");
    var box = section4.querySelector(".box");

    var input1 = box.children[0]; //childNodes[0];
    var input2 = box.children[1]; //childNodes[1];

    input1.value = "hello";
    input2.value = "okay";
});
```


텍스트, 주석도 노드임 childNodes[0];으로 코드를 작성하면 공백도 노드로 포함되어 원하는 결과를 얻지 못한다.
따라서 태그형태만 자식으로 치부하는 children[0]; 코드를 사용해야한다.  

### 28강 - Node의 종류와 개체 형식
---  

객체들이 존재하려면 그 객체의 형식이라는 개체가 존재 해야한다. 객체 형식에는 어떠한 것들이 있는지 알아보자. 

* **Document**  ```html 문서 객체의 중심을 담당하고 있는 부분```  
* **DocumentType** ```그 녀석을 객체화할때 객체 형식```
* **Elemment**  ``` <textarea><p> ```  
* **Attr** ```<textarea <b>rows</b> = "30" **cols**="40">```
* **Entity** ```&**lt**;뉴렉처**&**gt**;** &**nbsp**;```
* **EntityReference** ```**&**lt**;**뉴렉처**&**gt**;** **&**nbsp**;**```
* **Text** ```<p>**뉴렉처**</p>```
* **comment** ```<!-- 주석 -->```
* **CDTASection** ```Entity를 쓰다보면 그 기호를 쓰는 것에 대한 불편함도 있음. <![CDATA[<,>,]]> 특수기호 마음껏 써도 됨``` 
* **Notation** ```<font color = **"#ffff00"** size = **"10px"**> 속성의 값으로 설정하는 것 중에서 어떤 표현형식을 사용할수 있게 해주는 표기법에 대한 내용을 담고 있음``` 

위의 타입들은 공통분모를 가지고있음. 그 공통분모를 기능적으로 하나로 추상화하여 node라 함.
