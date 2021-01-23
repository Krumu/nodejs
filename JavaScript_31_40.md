### 30강 - 엘리먼트 노드의 속성변경 예제 - 사진변경
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
### 30강 - 엘리먼트 노드의 속성변경 예제 - 사진변경
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
