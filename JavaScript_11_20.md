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
( 제어구조 중 for in에 대해서만 다룹니다.)  
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

for (var i in ar) // 개수, 증감이점 키를 넣어줌
  document.write(ar[i]+"<br />");
```
javascript의 for in은 다른 언어의 for each와 다르게 key를 넘겨줌.
즉, for in을 사용하면 자동으로 
```
```
### 04강 - 코드 작성과 Live Server 설치하기
### 05강 - 데이터 객체와 래퍼클래스
---
JavaScript에서 모든 데이터는 객체로 되어있다. JavaScript에서 데이터는 모두 래퍼클래스에 담기기때문이다.
데이터를 담는 래퍼클래스는 Number(정수,실수), String(문자,문자열). Boolean(부울)이 있다. 자바스크립트에서 문자와 문자열 구분하지않는다.

```javascript
var x = 3; // var x = new Number(3); 와 같은 뜻
```
x는 따로 공간을 할당받지 않으며 단지 '참조'만 한다.

```javascript
var x;
alear(x == undefined);
```
undefined는 문자열이 아닌 하나의 값이므로 "undefined"로 두고 비교하지 않도록 주의하자. 
