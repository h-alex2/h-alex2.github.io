---
title: "Higher Order Function 고차 함수, CallBack 콜백함수"
date: 2022-01-05
category: javascript
tags:
  - HigherOrderFunction
  - udemy
  - 고차함수
---


## Higher Order Function 고차함수
- 하나 이상의 함수를 argument(인수)로 받거나, 함수를 결과로 반환하는 함수

```javascript 
document.addEventListener("keydown", respondToKey(event));
addEventListener는 입력으로 respondToKey 함수를 취한다. 

function respondToKey(event) {
  console.log("Key downed.");
} //무언가가 끝날 때 까지 기다리기 때문에 콜백함수
```
event
- e
- evt
- event 

## callback function (call-after function) 콜백함수
- 다른 함수의 인자로써 이용되는 함수
- 어떤 이벤트에 의해 호출되어지는 함수


## setTimeout() 지정한 시간 후에 코드를 실행 