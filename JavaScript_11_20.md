### 11강 - JSON파서를 이용한 파싱
---
```javascript
var data = {"id": "32191061", "name":"댜사우"};  
```
형태로 Object를 초기화했었는데 사실은  
```javascript
var data = {id: "32000000", name:"기바"};
```
와 같이 key값을 '' or ""로 감싸지않아도 됨

그러나 JSON 파서는 굉장히 민감하기 때문에 key값을 '' or ""로 감싸줘야함  
```javascript
var data = JSON.parse('{"id": "32000000", "name":"기바"}');
console.log(data.id);
``` 
보통 JavaScript에서는 전자의 경우로 데이터르르 관리하는 경우가 많아 파싱을 하는 과정이 너무 불편하다는 생각을 하게 됨.
따라서 JSON 문자열로 바꾸어주는 stringfy를 사용하게 됨
```javascript  
var data = {"id": "32000000", "name":"기바"};
var json = JSON.stringify(data);
alert(json); //문자열로 바뀐 것을 확인
```  

### 12강 - 자바스크립트 연산자
---  
```javascript  
var x = 3;
var y = 3; 
document.write(x==y);
document.write('<br>');   
document.write(x===y);
```  
(두 연산자 결과 모두 true를 반환합니다.)
== 연산자는 두 변수가 가지고 있는 값이 일치하는지를 확인하며
=== 연산자는 두 변수가 참조하는 객체가 일치하는지를 확인합니다.
서로 다른객체를 선언하고 싶다면 var y = new Number(3);를 이용합니다.

```javascript  
document.write(33+"32");// 3332
document.write(33-"32");// 1
```  
+연산에서는 정수와 문자열을 더하면 문자열로 변환후 문자열들이 합쳐지지만
-연산에서는 문자가 실수가 되어 -연산이 이뤄짐   
   
### 13강 - 자바스크립트 제어구조
---  
(제어구조 중 for in에 대해서만 다룹니다.)  
```javascript  
var ar = ["hello", "hi", "greeting"];
var ob = {id:1, title:'hello', writeId:"newlec"};

for(var i =0; i<ar.length; i++)
  document.write(ar[i]+"<br />");
```  
for in이 어떻게 동작하는지를 알아보기위해서 위의 for문을 for in으로 바꾸고 보자  
```javascript
var ar = ["hello", "hi", "greeting"];
var ob = {id:1, title:'hello', writeId:"newlec"};

for (var i in ar)
  document.write(ar[i]+"<br />");
```  
javascript의 for in은 다른 언어의 for each와 다르게 key를 넘겨줌.

### 14강 - 함수 객체와 표현식
---  
자바 스크립트는 함수를 정의하지않고 만든다(객체)
함수를 인자로 전달하기 쉽다는 장점이 있다

함수를 만드는 방법
1.
```javascript
var add= new Function("x,y","return x+y;") 
```  
2.
```javascript
var add = function(x,y){
return x+y;
};
```  
3.
```javascript
function add(x,y){
   return x+y;
}
document.write(add(3,4));
```  
         
### 15강 - 함수의 가변 인자 arguments 콜렉션
---
사실 javascirpt에서 매개변수는 의미가 없다. 자바스크립트는 데이터가 모두 객체이기때문에 매개변수도 참조하는 이름일 뿐이다.
매개변수로 넘겨지는 것들은 모두 가변으로 받을 수 있는 컬렉션을 가지고 있다. (function 객체 내부에서 사용할 수 있는 arguments라는 컬렉션 이용하여 넘겨진 값들을 사용할 수 있음)

```javascript
function add(x,y){ 
             //alert(arguments.length);
             //alert(arguments[5]);
             alert(typeof arguments[5]);
             return x+y;
         }
         document.write(add(6,10,5,3,4,"hello"));
```  
  
### 16강 - 변수의 가시영역과 global 객체 그리고 전역변수
```javascript  
var a =1;
alert(a);
```  
위의 코드를 실행하면 알림창에 1이 나오는걸 알고있다. 만약 두 코드의 순서를 바꾸면 어떻게 될까?
에러가 아닌 undefined가 뜬다. 즉, 참조변수 a는 생성되었지만 값은 할당되지 않았음을 뜻한다.
이는 순서와 상관없이 지역내의 코드가 실행되기 전에 지역내에서 선언된 모든 변수들이 메모리에 올라간다는 것을 알 수 있다.

변수 선언없이 사용할 수 있다?  
```javascript  
b=1;
alert(b);// 자바스크립트의 객체는 속성이 막 붙읈 수 있다? 전역객체에 붙음
```  
변수를 선언했을때와 마찬가지로 알림창에 1이 나온다. 그럼 같은 의미를 가질까?
그렇지않다. 이전에 javascript의 객체는 속성을 이후에 막 붙일 수 있다고 배웠는데
이와 마찬가지로 var를 사용하지않으면 window라는 전역객체에 속성으로서 b가 붙게 된다.   
  
  
```javascript
var c =1;
var c =2;
alert(a);
```  
같은 참조변수를 두 번 선언해도 에레가 발생하지않는다.

```javascript  
{
    var d = 1;
} 
alert(d);
```  
코드를 실행시키면 알림창에 1이 나오게되는데 이를 통해 javascript에서는 중괄호가 변수 영역을 나누지 않는다는 것을 알 수 있다.
참고로 javascript에서 유일하게 지역으로 사용되는 괄호는 function이다.

```javascript
function f1(){
    var a =1;
}
f1();
alert(a);
```  
함수가 호출된 후 alert(a);를 실행할때 이미 참조변수 a는 사라졌으니 에러가 발생하게 된다.
그렇다면 var를 뺀다면 어떻게 될까?

```javascript
function f1(){
    a =1;
}
f1();
alert(a);
```  
전역객체에 속성으로서 a가 생성되므로 함수가 종류된다고해서 a가 사라지지않는다. 따라서 알림창에 1이 뜬다.
f1(); 와 alert(a);의 위치를 바꾼다면 어떻게 될까? 함수가 호출되기 전이니 전역객체에 속성 a가 생성되지 않았을 것이다.
따라서 에러가 발생한다.

### 17강 - 클로저(Closure)
---  
javascript에서는 함수도 객체로 표현한다고 배웠다. 따라서 함수의 반환 객체로 또 다른 함수를 둘 수 있다.
다음 코드를 살펴보자.
```javascript  
   function f1(){
       var a = 1;

       return function f2(){
           return a;
       }
   }

   var f = f1();
   var a = f();
   alert(a);
```  
f는 함수 f1의 반환 객체를 받는다. 함수 f1의 반환 객체는 함수 f2이므로 f는 함수객체를 참조하는 참조변수가 된다.
그런데 뭔가 이상하다. 함수 f1을 호출하면 지역변수 a=1이 되고 함수 f2를 반환하게 되는데 우리가 배운바에 따르면 이때 지역변수 a는 사라지게된다.
그 후 f2함수를 호출할때 a를 반환해야하는데 이미 a는 사라졌으므로 에러가 발생해야한다. 하지만 위의 코드를 실행해보면 f1함수에서 설정한 값 그대로
1이 출력된다. 어떻게 된 일일까?

javascript는 함수 안에서 함수를 정의할 경우에 자기 위에 있는 함수의 변수를 사용할 수 있도록 설계되었다. 따라서 f1이 호출이 끝났더라도 자기가 가지고 있는
자원이 언제 사용될지 모르므로 계속 가지고 있어야한다.

이런 상황에서 자기가 가지고 있는 자원을 닫을 수 있게 해주는 키워드를 closure라고 한다. 이 예시에서는 funciton f2(){ return a;}가 closure이다.


### 18강 - window 플랫폼을 이용한 대화 parseInt, alert, prompt, confirm
---  
javascript로 브라우져를 제어할 수 있음. 브라우져의 껍데기를 제어할 수 있는 객체를 window라고 한다.
window.location 는 주소가 나타나는 부분을
Window.history는 뒤로가기 부분을
window.document는 그 내부를 제어할 수 있다.  
  
윈도우 객체가 가지고 있는 함수 중 사용자와 상호작용 할 수 있는 대화상자를 띄우는 함수가 3가지가 있다.(alert, prompt, confirm)  
```javascript
var x = prompt("x의 값을 입력하세요", 0); //window.prompt
var y = prompt("y의 값을 입력하세요", 0);
alert(x+y);
```  
위의 코드를 실행하면 예상과는 다른 결과가 나온다. x에 3을 y에 4를 입력하면 7이 아닌 34가 나오는데 이는 입력받은 내용들을 무조건 문자열로 받기 때문이다.
parseInt라는 함수는 문자열을 정수로 바꿔준다. 이 함수를 이용하여 원하는 결과를 얻을 수 있다. (문자열을 실수로 바꾸고 싶다면 parseFloat사용, 숫자가 아닌 값을 넣으면 NaN반환)  

```javascript
var x = parseInt(prompt("x의 값을 입력하세요", 0)); //window.prompt
var y = parseInt(prompt("y의 값을 입력하세요", 0));

alert(x+y);
```  
만약 12abc와 같이 숫자 뒤에 문자열이 붙은 값을 parseInt의 인자로 넣어주면 어떻게 될까?
그래도 parseInt는 12를 리턴한다. 이는 평소 우리가 숫자뒤에 단위를 붙인 데이터를 많이 사용하기 때문에
이러한 데이터를 그대로 사용해도 되게끔 편리성을 위해 지원하는 기능이다.

```javascript
var x = prompt("x의 값을 입력하세요", 0); //window.prompt
var y = prompt("y의 값을 입력하세요", 0);

x= parseInt(x); //숫자 안넣으면 NaN parseint("12abc") -> return 12
y= parseInt(y);

alert(x+y);
```  

confirm함수는 사용자가 확인/취소만을 선택할 수 있으며 확인을 누르면 true가 반환된다.
```javascript
var answer = confirm("삭제하시겠습니까?");
if(answer)
   alert("삭제됨");
```          

### 19강 - 이벤트 기반의 프로그래밍
---
javascript를 작성할 수 있는 code block이 script 영역만 있는 것이 아니다. html에는 body안에 들어갈 수 있는 태그들이 존재하는데 그 태그 안쪽에
on으로 시작하는 속성이 있다. 그 속성의 값에도 작성이 가능하다.
```html
<body>
   <input type="button" value="클릭" onclick="alert('안녕하세요');">        
 </body>
```  
script영역에 작성하면 페이지가 읽혀질 때 실행이되지만 onXX 속성값으로 작성하면 해당 이벤트가 발생할 때 실행된다는 차이점이 있다.
하지만 onXX의 속성값이 길고 복잡해지면 가독성이 떨어진다는 단점이 있다.

```html
<input type="button" value="클릭" onclick="var x,y; x= prompt('x값을 입력하세요'); y=prompt('y값을 입력하세요'); alert(x+y);" />
```

따라서 이런 경우에는 다음과 같이 script block을 같이 사용하여 코드를 작성한다.

```html
<script>
   function printResult()
   {
        var x,y;
        x= parseInt(prompt("x값을 입력하세요",0));
        y= parseInt(prompt("y값을 입력하세요",0));
        alert(x+y);
   } 
</script>

<body>
   <input type="button" value="클릭" onclick="printResult()" />;
</body>
```  
페이지를 로드하는 경우에 script block에서 함수를 호출하지않으니 함수가 실행되지않을 것이며, 이벤트 발생시에 함수가 호출되어 실행될 것이다.  

### 20강 - 문서의 엘리먼트 객체 이용하기
---  
html 태그들이 화면에 보여질때 바로 보여지는게 아니라 메모리상에 javascript가 이용할 수 있게끔 객체로 올려놓는다.
태그라는 개념이 메모리에 올라가게되면 엘리멘트 객체라한다. 이 엘리먼트 객체를 이용하는 시간을 가져보자.

```html
<script>
   function printResult()
   {
        var x,y;
        x= parseInt(prompt("x값을 입력하세요",0));
        y= parseInt(prompt("y값을 입력하세요",0));
        btnPrint.value=x+y;
   } 
</script>

<body>
   <input type="button" value="클릭" onclick="printResult()" id='btnPrint'/>
</body>
```  
id를 이용해서 그 객체를 이용할 수 있는데 위 코드를 실행하면 id가 btnPrint인 엘리먼트 객체의 value속성이 x+y의 값으로 바뀌게 된다.
태그를 감싸고 있는 안쪽 텍스트를 제어하고 싶으면 innerText를 사용한다.

여기서 하나의 생각이 떠오른다. onclick또한 속성인데 이를 id를 이용해서 제어할 수는 없을까? 이것이 가능하다면 html 태그쪽에서는 script를 되도록 사용하지 않을 수 있으니
코드의 유지보수에 도움이 될 것이다.

```html
<script>
   function printResult()
   {
        var x,y;
        x= parseInt(prompt("x값을 입력하세요",0));
        y= parseInt(prompt("y값을 입력하세요",0));
        btnPrint.value=x+y;
   } 
   btnPrint.onclick= printResult;
</script>

<body>
   <input type="button" value="클릭" id='btnPrint'/>
</body>
```  
그런데 주목해야할 부분이 있다. printResult 뒤에 소괄호가 없다. script 내에서 함수를 대입할때는 함수가 참조하고 있는 함수객체를 대입해야하는데 괄호를 쓰면 함수를 호출하게 되는 것이다. 
그래서 그 결과를 대입하게 된다. 하지만 여기서는 함수의 결과값을 대입하는 것이 아니기 때문에 ()를 사용하면 안된다.

위의 코드를 실행해보면....? 에러가 난다. btnPrint is not defined라는 문구가 뜨는데 이는 script block은 페이지가 로드되면 바로 실행된다는 점을 생각해보면 그 이유를 알 수 있다.
```html
<script>
   function printResult()
   {
        var x,y;
        x= parseInt(prompt("x값을 입력하세요",0));
        y= parseInt(prompt("y값을 입력하세요",0));
        btnPrint.value=x+y;
   } 
   btnPrint.onclick= printResult;
</script>
```  
script block내에 printResult() 내부 코드는 실행되지않지만 btnPrint.onclick= printResult; 코드는 실행이 된다.
btnPrint는 <input type ="button" value ="출력" id = "btnPrint"/>가 실행될때 정의되는데 이 코드가 실행되기 전에
btnPrint를 사용하게되고 이는 메모리상에 존재하지 않으니 에러가 발생하는 것이다.

이를 해결하는 방법은 없을까?
