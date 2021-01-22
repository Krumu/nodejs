### 01강 - 학습가이드
### 02강 - 자바스크립트의 탄생과 플랫폼
### 03강 - 실습환경 준비하기
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
  
  
  
### 06강 - 배열(Array) 생성과 사용하기  
---  
#### Array 객체는 stack형식으로 사용하거나 list형식으로 사용할 수 있다.

1. stack 형식

```javascript
var nums = new Array();
nums.push(2);
nums.push(3);
nums.push(5);

var data =nums.pop();
alert(data); // 5
```

2. list 형식

```javascript
var nums = new Array();
nums[0]= 2;
nums[1]= 3;
nums[2]= 5;
// num[4]=4; nums[3]은 undefined
alert(nums[2]); // 5
```
  
  
  
### 07강 - 배열(Array) 초기화와 조작하기  
---
#### 1. 배열 초기화
생성자에 하나의 인수를 넣어주면 그 만큼 공간을 할당한다. 하지만 인수를 2개이상 넣어주면 그 인수들을 배열의 요소로 선언한다.

```javascript
var nums = new Array(3,2) // var nums = [3,2];가 됨 
```
#### 2. 배열 조작
splice() 메소드를 이용한 데이터 관리
```javascript
var nums = new Array(5,10,21,"hello","haha");
nums.splice(4); //4부터 끝까지 다지워라
num.splice(3,1); //3부터 1개만 지워라
num.splice(1,0,"hoho"); //1의 자리에 hoho 대입
```
  
  
  
### 08강 - Object 객체  
---  
JavaScript는 객체를 만들고 정의를 한다.(동적인 객체)

```javascript
var exam = new Object();
exam.kor = 30; // Expand Object

alert(exam.kor); // exam["kor"]=30;와 같음
```
exam.kor와 exam["kor"]는 같은데 왜 두개의 표현이 존재할까? 

변수에 답겨진 문자열을 이용하여 객체 속성을 꺼내거나 대입할때 exam["kor"]형식을 사용

```javascript
var str = 'kor';
alert(exam[str]);
```
Object()는 hash형임  
  
  
  
### 09강 - JSON   
---  
간단한 데이터 하나를 변수에 담으려고해도 객체를 만들어야함. 너무 복잡함.
이를 쉽게 표기할 수 있는 표기법이 바로 JSON

```javascript
var ar= new Array();  // var ar=[];
var exam = new Object(); // var ha={};
```

```javascript
var ar = [3,4,5,6,exam.[7,8,9]];
var exam = {"kor":30, "eng":70, "math":80};
```

현재 json은 자바스크립트를 벗어나서 모든 언어에서 데이터를 포장할 때 사용할 수 잇는 포멧으로 사용됨.
  
  
  
### 10강 - eval 함수와 JSON파싱하기  
---  
공공데이터들을 json형식으로 다운 받고 사용할 수 있는데 이들은 문자열로 되어있다. 문자열 데이터를 어떻게 객체로 만들 수 있을까?

#### eval 함수이용
```javascript
data = 'var x = 5;';
eval(data);
alert(x); // 5
```

#### JSON파싱(다음시간에 공부함)
