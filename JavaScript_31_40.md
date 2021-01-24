## 30강 - 엘리먼트 노드의 속성변경 예제 - 사진변경
---  
노드의 속성을 변경하는 예제를 풀어보자  
```html
<section id = "section5">
   <h1>Ex5 : 엘리먼트 노드의 속성 & CSS 속성 변경 </h1>
   <div>
         <input class ="src-input" />
         <input class ="change-button" type="button" value="변경하기" />
   </div>
   <div>
      <img class = "img" src="images/img1.jpg" style="border:1px solid red;" />
   </div>
</section>
```  

```javascript  
<section id = "section5">
window.addEventListener("load",function(){
    var section = document.querySelector("#section5");
    var changeButton = section.querySelector(".change-button");
    var img = section.querySelector(".img");

    changeButton.onclick= function() {
        img.src="./images/"+srcInput.value;

    };

});
```  
option을 고르는 형태로 사용자의 input값을 받아보자  
```html
<section id = "section5">
   <h1>Ex5 : 엘리먼트 노드의 속성 & CSS 속성 변경 </h1>
   <div>
      <select class = "img-select">
         <option value="img1.jpg">img1</option>
         <option value="img2.jpg">img2</option>
         <option value="img3.jpg">img3</option>
      </select>
         <input class ="src-input" />
         <input class ="change-button" type="button" value="변경하기" />
   </div>
   <div>
      <img class = "img" src="images/img1.jpg" style="border:1px solid red;" />
   </div>
</section>
```  

```javascript  
<section id = "section5">
window.addEventListener("load",function(){
    var section = document.querySelector("#section5");
    var changeButton = section.querySelector(".change-button");
    var imgSelect = section.querySelector(".img-select"); 
    var img = section.querySelector(".img");

    changeButton.onclick= function() {
        img.src="./images/"+imgSelect.value;
    };

});
```  

datalist를 추가  
```html  
<section id = "section5">
   <h1>Ex5 : 엘리먼트 노드의 속성 & CSS 속성 변경 </h1>
      <div>
         <input class ="src-input" list="img-list"/>
            <datalist id ="img-list">
                <option value="img1.jpg">img1</option>
                <option value="img2.jpg">img2</option>
                <option value="img3.jpg">img3</option>
            </datalist> 
            <select class = "img-select">
                <option value="img1.jpg">img1</option>
                <option value="img2.jpg">img2</option>
                <option value="img3.jpg">img3</option>
            </select>
            <input type="color" class="color-input" />
            <input class ="change-button" type="button" value="변경하기" />
         </div>
         <div>
            <img class = "img" src="images/img1.jpg" style="border:1px solid red;" />
         </div>
</section>
```  

```javascript  
window.addEventListener("load",function(){
    var section = document.querySelector("#section5");
    var srcInput = section.querySelector(".src-input");
    var imgSelect = section.querySelector(".img-select");
    var changeButton = section.querySelector(".change-button");
    var img = section.querySelector(".img");
    var colorInput = section.querySelector(".color-input");

    changeButton.onclick= function() {
        img.src="./images/"+srcInput.value;
    };

});
```   
### 31강 - CSS 스타일 속성변경
---  
30강의 예제에서 이미지의 테두리를 제어하는 코드를 추가해보자

```html  
<section id = "section5">
   <h1> Ex5: 엘리먼트 노드의 속성 $ CSS 속성 변경 </h1>
   <div>
      <input class ="src-input" list="img-list" />
      <datalist id = "img-list">
         <option value="img1.jpg">img1</option>
         <option value="img2.jpg">img2</option>
         <option value="img3.jpg">img3</option>
      </datalist>
      <select class = "img-select">
         <option value="img1.jpg">img1</option>
         <option value="img2.jpg">img2</option>
         <option value="img3.jpg">img3</option>
      </select>
      <input type ="color" class="color-input" />
      <input class = "change-button" type = "button" value ="변경하기" />
   </div>
   <div>
      <img class = "img" src = "images/img1.jpg" style = "border: 1px solid red;" />
   </div>
</section>
```   

```javascript  
window.addEventListener("load",function(){
    var section = document.querySelector("#section5");
    var srcInput = section.querySelector(".src-input");
    var imgSelect = section.querySelector(".img-select");
    var changeButton = section.querySelector(".change-button");
    var img = section.querySelector(".img");
    var colorInput = section.querySelector(".color-input");

    changeButton.onclick= function() {
        img.src="./images/"+srcInput.value;
        // img.src= "./images/" + imgSelect.value;
        //img.style.border-color;
        img.style.borderColor = colorInput.value; //img.style["border-color"]= colorInput.value;
    };

});
```  
style속성의 border-color프로퍼티의 값을 사용자가 설정한 값으로 바꾸려한다. 이를 위해서 img.style.border-color로 코드를 작성하면 syntax에러가 발생한다. 이를 해결하기 위한 2가지 방법이 있다.

#### 1) img.style["border-color"]= colorInput.value;
#### 2) img.style.borderColor = colorInput.value

##### 참고로 class속성은 img.class와 같이 사용할 수 없음. img["class"] or img.className으로 사용  

## 32강 - 텍스트 노드를 동적으로 추가/삭제
---  
새로운 텍스트노드를 만들고 이를 추가하는 코드와 원래 있었던 노드를 삭제하는 코드를 만들어보자(document.createTextNode(), appendChild, removeChild 사용)  

```html  
<section id = "section6">
    <h1>Ex6 : 노드 조작: 메뉴추가(createTextNode, Element) </h1>
    <div>
        <input class="title-input" name = "title" />
        <input type="button" class = "add-button" value="추가" />
        <input type="button" class = "del-button" value="삭제"/>
    </div>
    <div class = "menu-list">
    
    </div>
</section>  
```  

```javascript
window.addEventListener("load",function(){
    var section = document.querySelector("#section6");
    
    var titleInput = section.querySelector(".title-input");
    var menuListDiv = section.querySelector(".menu-list");
    var addButton = section.querySelector(".add-button");
    var delButton = section.querySelector(".del-button");

    addButton.onclick= function() {
        var title = titleInput.value;
        var txtNode = document.createTextNode(title);
        menuListDiv.appendChild(txtNode);
    };

    delButton.onclick= function() {
        var txtNode = menuListDiv.childNodes[0];
        menuListDiv.removeChild(txtNode); 
        
    };
});  
``` 
하지만 위 코드에는 문제점이 있다. 노드를 추가하고 삭제를 하면 바로 menuListDiv의 첫번째 텍스트노드가 삭제되지 않는다. 이는 '공백'때문이다.
하지만 이 문제를 해결할 필요는 없다. 보통 노드를 추가할때 텍스트 노드만을 만들어서 추가하기보다는 텍스트노드를 만들고 태그들을 같이 포함시켜 넣어주기 때문이다.


