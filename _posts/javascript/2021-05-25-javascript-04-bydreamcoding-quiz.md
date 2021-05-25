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

