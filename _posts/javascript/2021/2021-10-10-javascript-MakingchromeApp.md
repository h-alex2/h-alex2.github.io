---
title: "JS로 크롬앱 만들기"
date: 2021-10-11
category: javascript
tags:
  - NomadCoders
published: false
toc: true
toc_sticky: true
toc_label: “HTML CSS JAVASCRIPT”
---
   
<br>
<link rel="stylesheet" type="text/css" href="/assets/CSS/markdown.css">
```javascript
const loginForm = document.getElementById("login-form");
const loginInput = loginForm.querySelector("input");
const loginButtom = loginForm.querySelector("button");

const loginInput = document.querySelector("#login-form, infut");
const loginButton = document.querySelector("#login-form, botton);
```
위 3줄과 밑 2줄은 같은 것 

- 항상 최고의 기능이 있는 툴을 사용하기
- 이미 가지고 있는 기능들을 사용하기

## input form 
이전에 js에서 로그인인풋의 글자 길이에 따라 alert를 보낸 것 등 이러한 기능은 HTML의 `input` 에서 할 수 있다.

- `<input>` : 입력 요소  
  <p id="d" markdown="1"> HTML `<input>` 요소는 웹 기반 양식에서 사용자의 데이터를 받을 수 있는 대화형 컨트롤을 생성합니다. 사용자 에이전트에 따라서 다양한 종류의 입력 데이터 유형과 컨트롤 위젯이 존재합니다. 입력 유형과 특성의 다양한 조합 가능성으로 인해, `<input>` 요소는 HTML에서 제일 강력하고 복잡한 요소 중 하나입니다.   
  <https://developer.mozilla.org/ko/docs/Web/HTML/Element/input>
  </p>

- input은 자체적으로 최대 글자수를 조절할 수 있다.
- input의 유효성 검사를 작동시키기 위해서는 input이 `form` 안에 있어야 한다. 

```html 
  <body>
    <form id="login-form">
      <input 
        required 
        maxlength="15" : 최대 글자 수 15로 15자를 넘으면 타이핑이 안된다.
        type="text" 
        placeholder="what is your name?">
      <button>Log In</button> or <input type="submit" value="Log In" /> : 둘은 같은 것
    </form>
```
브라우저로 들어가보면 input에 value를 누르고 login을 누르면 _새로고침_ 이 된다.   
➞ form이 submit되고 있는 것

form 안에서 엔터를 누르고 input이 더 존재하지 않는다면 자동으로 submit 되는 규칙  
or form 안에 있는 버튼을 눌렀을 때, 이 때도 form이 자동으로 submit된다  

<u>브라우저가 새로고침하지 않고 user 정보를 저장하도록 하고싶다면</u>


- 항상 user가 입력하는 값의 유효성 확인하기