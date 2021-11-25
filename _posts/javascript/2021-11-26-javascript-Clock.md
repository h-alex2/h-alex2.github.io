---
title: "JS로 시계만들기"
date: 2021-11-26
category: javascript
tags:
  - NomadCoders
# toc: true
# toc_sticky: true
# toc_label: “Clock”
---

배운 것
- `setInterval(, )` 
  - 함수를 원하는 간격마다 실행시킨다.
  1. 두 개의 인자를 받는다.
  2. 첫 번째 : 실행하고자 하는 함수
  3. 두 번째: 호출되는 함수 간격을 몇 ms(millisec)로 할 지
- `setTimeout(, )` 
  - 함수를 원하는 시간 뒤에 실행시킨다. 
  1. 두 개의 인자를 받는다.
  2. 첫 번째 : 실행하고자 하는 function 
  3. 두 번쨰 : 얼마나 기다릴지 ms 단위로 
- `new Data()`
  - 날짜 데이터를 받아올 수 있다.
- `padStart(, )`  
  - string의 자릿수가 한자리라면 앞에 string을 더 넣어서 원하는 길이를 맞출 수 있다. 
  1. string에서만 쓸 수 있다.
  2. 예) padStart(2, "0"); : string이 한자리라면 앞에 "0"을 넣어서 두자리로 만들고 만약 string이 두자리라면 변경사항 없음
- `padEnd(, )`
  - padStart가 앞에 추가라면 padEnd는 뒤에 추가하는 것
- `getHours()` `getMinutes()` `getSeconds()`
  - 시간 값을 가져올 수 있다.   
  ```clock.innerText=(`${date.getHours()}:${date.getMinutes()}:${date.getSeconds()}`);```

