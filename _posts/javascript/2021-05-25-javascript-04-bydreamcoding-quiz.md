---
title: "Dream Coding-JavaScript 05강 퀴즈"
date: 2021-05-25
category: javascript
tags:
  - DreamCoding
  - Quiz
---

드림코딩 5강 퀴즈  
function calculate라는 함수를 만들어서 입력받은 command에 따라서 연산하기 
function calculate(command, a, b) 
command: add, substract, divide, multiply, remainder




```javascript
function calculation(a, b, c) {
    if (a == add) {
        console.log(b + c);
    }
    else if (a == substract) {
        console.log(b - c);
    }
    else if (a == divide) {
        console.log(b / c);
    }
    else if (a == multiply) {
        console.log(b * c);
    }
    else if (a == remainder) {
        console.log(b % c);
    }
}
const add = (b, c) => b + c;
const substract = (b, c) => b - c;
const divide = (b, c) => b / c;
const multiply = (b, c) => b *+* c;
const remainder = (b, c) => b % c;
```



ellie's answer 

```javascript
function calculation(command, a, b) {
    switch (command) {
        case 'add':
            return a + b;
        case 'substrat':
            return a - b;
        case 'divide':
            return a / b;
        case 'multiply':
            return a *+* b;
        case 'remainder':
            return a % b;
        dafault:
            throw Error('unknown command');
    }
}
```


정해진 데이터를 처리하는 경우에는 __switch__ 를 이용해서 만드는 게 더 좋다.


switch 를 내가 잘 익히질 못했나보다.. 잘 생각이 나질 않았다.
이런 기능이 있을 것 같은데.. 라고만 생각했네ㅎㅎ
