---
title: "Dream Coding-JavaScript 02강"
date: 2021-05-15
category: javascript
tags:
  - DreamCoding
toc: true
toc_sticky: true
toc_label: “2. 콘솔에 출력, script async 와 defer의 차이점”
# header:
#   video:
#     id: XsxDH4HcOWA
#     provider: youtube
---


## Dream Coding-JavaScript 02강 - 2. 콘솔에 출력, script async 와 defer의 차이점


<link rel="stylesheet" type="text/css" href="/assets/CSS/markdown.css">


<br>

{% include video id="tJieVCgGzhs" provider="youtube" %}


1. node.js 설치
2. cmd에 console.log('Hello World!');  입력 후 폴더에 main.js로 저장
3. cmd 경로를 프로젝트 폴더로 바꿔주고  
(cmd 경로 바꾸기 1. d: 2. cd + 바꿀 경로)
node main.js 입력하면 Hello World 출력된다.

4. 크롬 열어서 console창 열기 console 창 단축키 : __ctrl + shift + i__

  > console API : 웹 api의 하나  
  브라우저가 제공하는 브라우저가 이해하는 함수  
  Application Programming Interface

<br>

---

<br>

## 자바스크립트의 공식사이트는?
  - <a href="ecma-international.org">ecma-international.org</a>
  : 좀 어렵게 되어있다.

  - <a href="developer.mozilla.org">developer.mozilla.org</a> 제일 많이 보는 사이트
  : <a href="www.w3schools.com">www.w3schools.com</a> 이 사이트 보다 위에 mdn 사이트가 더 설명이 잘 되어있다.


<br>

---

## html에서 자바스크립트를 어떻게 포함하는게 좋을까?
### 1. head에 바로 script를 포함하는 경우
<a href="/assets/post_img/21-05-15-1-1.JPG"><img src="/assets/post_img/21-05-15-1-1.JPG"></a>
1. parsing html
2. 순차적으로 parsing되는데 js 차례가 됐을 때 js가 fetching되고 executing 되는 동안 html은 멈춰있고
3. js가 executing 되고나서야 그 다음 html이 parsing된다.  
  - js가 사이즈가 크다면 오래걸릴 수 있다

---

### 2. body 끝부분에 script 추가하기
<a href="/assets/post_img/21-05-15-1-2.JPG"><img src="/assets/post_img/21-05-15-1-2.JPG"></a>
1. html 준비가 된 다음에
2. js fetching, executing
   - js가 준비되기 전에도 html을 볼 수 있다.
   - 단점 : 만약 js에 의존적인 웹사이트라면 의미있는 콘텐츠를 미리 보기 힘들다.

단점 : html을 빨리 본다는 장점이 있지만 사용자가 의미있는 콘텐츠를 보기위해서는 자바스크립트가 필요하다면 정상적인 페이지를 보기위해서 많이 기다려야할 수 있다.

---

### 3. head안에 script를 이용하되 async(에이씽크)라는 속성값 쓰기
<a href="/assets/post_img/21-05-15-1-3.JPG"><img src="/assets/post_img/21-05-15-1-3.JPG"></a>
asyn는 boolean타입의 속성값이기 때문에 선언하는 것 만으로 true로 설정.  
  - html이 parsing 되기 전에 자바스크립트가 출력되기 때문에  
  html이 정의되어 있지 않을 수 있어서 위험할 수 있다.

---

### 3-1. async 상황에서 script가 여러 개일 경우
<a href="/assets/post_img/21-05-15-1-5.JPG"><img src="/assets/post_img/21-05-15-1-5.JPG"></a>
- 준비된 js먼저 출력을 하기 때문에 순서에 의존적인 거라면 문제가 될 수 있다.

---

### 4. 3과 똑같이 head안에 넣고 asyc대신 defer 속성값 쓰기
<a href="/assets/post_img/21-05-15-1-4.JPG"><img src="/assets/post_img/21-05-15-1-4.JPG"></a>
- __가장 좋은 옵션__  
- html이 parsing하는 동안 js를 fetching

---

### 4-1. async 상황에서 script가 여러 개일 경우
<a href="/assets/post_img/21-05-15-1-6.JPG"><img src="/assets/post_img/21-05-15-1-6.JPG"></a>
- parsing 하는 동안 필요한 js를 다 받아놓은 다음에 순서대로 js를 출력하기 때문에 원하는대로 출력할 수 있다.



---

## 모르는 단어 찾아보기

#### parsing  
<p id="d"> : 컴퓨터에서 컴파일러 또는 번역기가 원시 부호를 기계어로 번역하는 과정의 한 단계로, 각 문장의 문법적인 구성 또는 구문을 분석하는 과정. 즉 원시 프로그램에서 나타난 토큰(token)의 열을 받아들여 이를 그 언어의 문법에 맞게 구문 분석 트리(parse tree)로 구성해 내는 일이다. 파싱은 크게 하향식 파싱과 상향식 파싱으로 나눌 수 있다.
[네이버 지식백과] 파싱 [parsing, 文章-分析] (IT용어사전, 한국정보통신기술협회)
</p>

#### executing    
<p id="d"> : 실행하는 것 </p>

#### prototype 프로토 타입  
<p id="d"> : 본격적인 상품화에 앞서 성능을 검증ㆍ개선하기 위해 핵심 기능만 넣어 제작한 기본 모델</p>

#### ecmascript   
<p id="d"> : 1996년 미국 넷스케이프 커뮤니케이션즈사(Netscape Communications)는 자사의 웹 브라우저 넷스케이프를 지원하는 자바스크립트를 개발, 공개하였다. 이에 마이크로소프트사(Microsoft)는 익스플로러(Explorer)용 스크립트 언어인 제이스크립트(JScript)를 발표하였고, 이로 인해 상호호환성이 떨어지자 자바스크립트의 표준화가 추진되었다.<br>
1996년 11월부터 ECMA(European Computer Manufacturers Association) 인터내셔널의 기술위원회 39(TC39)에서 표준화가 추진되었고, 1998년 10월 ECMAScript(ECMA-262)라는 이름으로 표준 기술이 공개되었다. ECMAscript는 한마디로 표준 자바스크립트라고 할 수 있다.
[네이버 지식백과] 에크마스크립트 [ECMAScript] (IT용어사전, 한국정보통신기술협회)
</p>

#### debugging 디버깅
<p id="d"> : 오류 수정. 컴퓨터 프로그램의 잘못을 찾아내고 고치는 작업. 일단 작성된 프로그램들이 정확한가(즉 잘못 작성된 부분이 없는가)를 조사하는 과정. </p>

<br>
<br>

### -  바닐라 자바스크립트
<p id="d"> : 순수 자바스크립트' 라이브러리나 프레임워크 x <br>
정적 x 동적 o, 동적인 면만 갖고 있어 중간 중간 에러를 예측하기 힘들다.
</p>


### -  타입 스크립트
<p id="d"> : MS에서 만든 자바스크립트의 상위 언어. 자바스크립트를 보완한 언어(?), 정적 타입을 추가하여 결과 에러체크 등 편의성이 제공됨. <br> 마지막엔 자바스크립트 파일로 컴파일되어 실행된다.
</p>

<br>

### 바닐라 자바스크립트 이용하기 전에 'use strict 정의해주기'
 바닐라 자바스크립트를 이용하기 전에 제일 윗부분에 'use strict';을 정의해주자
__타입 스크립트__ 를 쓸 때는 안써도 되지만 순수 __바닐라 js__ 를 쓸 때는 꼭 쓰는 게 좋다.

`'use strict';` 스트릭모드를 선언
- 자바스크립트 엔진이 더 효율적으로 분석할 수 있다.
- 실행할 때 조금 더 나은 성능을 기대할 수 있다.
> 자바스크립트 : 유연한 언어 = dangerous한 언어
