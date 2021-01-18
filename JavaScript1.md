var x;

alear(x == undefined);


JavaScript에서 모든 데이터는 객체로 되어있다.


Array 객체는 stack형식으로 사용하거나 list형식으로 사용할 수 있다.

Var nums = new Array()

의 생성자의 인수로 5를 넣어주면 그 크기만큼 할당

하지만 인수를 2개이상 넣어주면 그 인수들을 배열의 요소로 선언

splice() 메소드를 이용한 데이터 관리

Var nums = new Array(5,10,21,"hello");

Num.splice(1);
1부터 다지워라
num.splice(1,2);

1부터 2개만 지워라

num.splice(1,3,"hello");
1부터 3개만 지우고 hello대입

num.splice(1,0,"hoho");
1의 자리에 hoho 대입

JavaScript는 객체를 만들고 정의를 해(동적인 객체 정의)

Var exam = new Object();
Exam.kor = 30; // Expand Object

alert(exam.kor);
 
exam["kor"]=30;

alert(exam["kor"]);
변수에 담겨진 문자열을 이용하여 객체 속성을 꺼낸때, 대입할때
Object()는 hash형

간단한 데이터 하나를 변수에 담으려고해도 객체를 만들어야하는데
너무 복잡해

이를 쉽게 표기할 수 있는 표기법
 JSOn

현재 json은 자바스크립트를 벗어나서 모든 언어에서 데이터를 포장할 때 사용할 수 잇는 포멧으로 사용됨.



자바스크립트에서 문자와 문자열 구분하지않음

var ar= new Array();  -> var ar=[];
var exam = {"kor":30, "eng":70, "math":80};
 
var ob= new Object(); -> var ob =. };
var ar = [3,4,5,6,exam.[7,8,9]]


공공데이터들을 json형식으로 다운 받고 사용할 수 있는데, 이는 문자열로 되어있다. 
문자열로 데이터를 어떻게 객체로 만들 수 있을까
