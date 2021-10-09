---
title: "HTML, CSS in JavaScript (Basic)"
date: 2021-10-08
category: javascript
tags:
  - NomadCoders

toc: true
toc_sticky: true
toc_label: “HTML CSS JAVASCRIPT”
---
   
<br>
    
javascript는 html을 가져올 수 있다. 이미 연결 되어 있다. 
: html 안에서 javascript를 연결하기 때문에 html을 자동적으로 읽어들인다. 
<br>

## document 객체 이용하기
- `document.title` : html에서 설정한 title 확인 
- `document.getElementById("string")` ID 로 element를 가져올 수 있다.
  - `const title = document.getElementById("string")`
  - `console.dir(string)` dir ➞ 사용할 수 있는 __element__ 들을 보여준다.   
  💡 이 안의 element들을 이용해서 javascript로 html안의 정보들을 사용할 수 있다. 무궁무진!

  - `title.innerText = "Got you";` 를 js에 입력해놓으면 인터넷페이지 - 검사 - elements에 들어가서 html <body> 부분에 "Got you"라고 적용되어 있는 걸 확인할 수 있다. ➞ HTML에 의해 변경된 게 아니라 JS에 의해 변경된 것.

  - `const hellos = document.getElementsByClassName("hello");`  
  ➞ array 형태로 class element 가져오기  

---

## document - querySelector , querySelectorAll
  - `querySelector` 
  : element를 CSS 방식으로 검색할 수 있다. 
  : 단 하나의 element를 return 해준다. 

  ```html 
    <body>
    <div class = "hello">
      <h1>Grab me!</h1>
    </div>
    <script src="app.js"></script>
  </body>
  ```
  `class = "hello"` 부분의 `<h1>` 태그 부분인 `Grab me!` 만 가져오고 싶다면   
  `const title = document.querySelector(".hello h1");` 를 통해서 가져올 수 있다. 
  - querySelector에서는 hello가 __class name__ 이라는 것과 그 안의 __h1__ 을 명시해줘야한다.
  - class name이 중복된다면 querySelector는 __첫번째__ 것만 가져온다. 
  - class가 아닌 __ID__ 를 가져오는 것도 가능하다  
  `const title = document.querySelector("#hello");`  
  `const title = document.getEelementById("hello");`  
  ➞ 이 두가지는 같은 것이다.


 - `querySelectorAll`
 : class가 중복돼도 모두 다 가져온다. 

    예시1

    ```html
      <body>
        <div class = "hello">
          <h1>Grab me!</h1>
        </div>
        <div class = "hello">
          <h1>Grab me!</h1>
        </div>
        <div class = "hello">
          <h1>Grab me!</h1>
        </div>
        <div class = "hello">
          <h1>Grab me!</h1>
        </div>
        <script src="app.js"></script>
      </body>
    ```

    `class = "hello"` 의 두번째 `<h1>` 을 가져오고 싶다면  
    ➞ `document.querySelector(".hello:nth-child(2) h1");`  
    첫번째 <h1> `".hello:first-child h1"` 
    마지막 <h1> `".hello:last-child h1"`

## EVENT - JavaScript Object : console.dir 
`console.dir(title);` console을 확인하면 on으로 시작하는 많은 단어들이 있다.  
➞ event 

- event를 listen하기(감지하기) : `addEventListener` 
```javascript
function handleTitleClick(){
  console.log("title was clicked");
}
title.addEventListener("click", handleTitleClick);
```
  - `addEventListener` 를 이용해서 title을 click하면 handleTitleClick함수를 실행시키게 해놓았다. 
  - "click" 부분이 바로 __event__ 이다. 
  - 함수를 실행하기 위해 () 를 사용할 필요 없다. javascript에게 실행하라고 시키기만 하면 된다. 
  - `title.onclick = handleTitleClick;` 으로도 쓸 수 있지만 일관성이 없어서 이렇게는 잘 쓰지않는듯 하다.

---
Web APIs   
➞ JavaScript관점의 HTML Heading Element란 의미  <br>  
[MDN HTMLHeadingElement 사이트(클릭)](https://developer.mozilla.org/en-US/docs/Web/API/HTMLHeadingElement)
에 들어가면 EVENT를 확인할 수 있다.  
➞ 인터넷 검색하여 찾거나 console.dir를 이용하여 찾는다. (on으로 시작하는 것들 사용할 때는 on을 빼고 사용)

---
## EVENT - Window
<https://developer.mozilla.org/en-US/docs/Web/API/Window>

```javascript
function handleWindowResize(){
  document.body.style.backgroundColor = "tomato";
}
window.addEventListener("resize", handleWindowResize);
```
: 브라우저 크기를 조절하면 배경색이 tomato색으로 바뀌게 된다. 
- window의 event는 기본적으로 제공되는 event

---
<br>
<span style = "color:red"> 정리 </span>
- console에서 document의 <u>body, head, title</u> 이런 것들은 중요하기 때문에 document.body 이런식으로 불러올 수 있는 것
- 나머지 element ((ex)body 안의 div) 들은 <span style = "color:red">querySelector, getElementById</span> 등으로 찾아와야 한다.
<br><br>

---
## className, classList, toggle

```javascript
function handleTitleClick(){
  if (h1.className === "clicked") {
    h1.className = "";
  } else {
    h1.className = "clicked";
  }
}
```
css에서 정의해놓은 
`clicked` 를 불러오기 위해서 저 위 js에 `clicked` 가 2번 쓰였다. 저걸 raw string이라고 함  
➞ 저렇게 쓰는 대신 `const clickedClass = "clicked" ` 라고 const를 만들어서 `clicked` 대신 `clickedClass`를 쓰는 게 더 낫다. __오타로 인한 오류를 줄여준다.__ const 오타로 인해 에러가 나도 고치기가 훨 수월함.


- `className`
➞ html에 존재하는 class까지 다 바꿔버릴 수 있다.
- `classList`
➞ html에 존재하는 건 놔두고 추가가 가능하다. 
- `toggle`   
➞ If force is not given, "toggles" token, removing it if it's present and adding it if it's not present. If force is true, adds token (same as add()). If force is false, removes token (same as remove()).
힘이 주어지지 않으면 토큰을 "전환"하여 토큰이 있으면 제거하고 없으면 추가합니다. force가 true이면 토큰을 추가합니다(add()와 동일). force가 false이면 토큰을 제거합니다(remove()와 동일).

```javascript
function handleTitleClick(){
  const clickedClass = "clicked"
  if (h1.classList.contains(clickedClass)){
    h1.classList.remove(clickedClass);
  } else {
    h1.classList.add(clickedClass);
  }
}
```
```javascript
function handleTitleClick(){
  h1.classList.toggle("clicked");
}

h1.addEventListener("click", handleTitleClick);
```
이 두 가지 코드는 같은 결과를 낸다. `toggle` 덕분에 
