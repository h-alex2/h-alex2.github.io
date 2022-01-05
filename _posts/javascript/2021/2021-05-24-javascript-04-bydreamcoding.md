---
title: "Dream Coding-JavaScript 05강"
date: 2021-05-24
category: javascript
tags:
  - DreamCoding
toc: true
toc_sticky: true
toc_label: “5. Arrow Function은 무엇인가? 함수의 선언과 표현”
---

## Dream Coding-JavaScript 05강 - 5. Arrow Function은 무엇인가? 함수의 선언과 표현

<br>
{% include video id="e_lU39U-5bQ" provider="youtube" %}
<br>

## Function declaration
어떤 언어이든 대체적으로 함수 (function은) input (parameter)을 받아서 잘 처리한 다음에 output을 return 한다  
함수는 input, output이 중요하기때문에 함수의 이름을 잘 설정하는 게 중요하다.
- fundamental building block in the program 프로그램을 구성하는 기본적인 빌딩 블록
- subprogram can be used multiple times 서브프로그램이라고도 불리고 여러번 재사용이 가능
- performs a task or calculates a value 한가지의 태스크나 어떤 값을 계산하기위해 쓰여진다.  

### 1. 자바스크립트에서 Function을 정의하는 방법
1. function이라는 키워드를 이용하고 함수 이름을 지정 후 (파라미터1, 파라미터2) 파라미터를 넣어준 후 
2. 한가지의 함수는 하나의 일만 하도록 만들어야한다.
3. 함수는 무언가를 행동하는 것이기 때문에 동사형태로 이름을 지정하기

자바스크립트에서 Function은 __Object__ 이다. 

```javascript
function printHello() {
  console.log('Hello');
}
printHello();
// -> console에 Hello가 출력됨
```

```javascript
function log(message) {
  console.log(message) ;
}
log('Hello@');
// javascript는 타입이 없기 때문에 저 message가 숫자, 스트링 둘 중 뭘로 전달되어야하는지 모른다.
// 그래서 
log('1234); 
// 숫자도 출력되고 문자도 출력된다.
```
<a href="https://www.typescriptlang.org/play?#code/PTAEHUFMBsGMHsC2lQBd5oBYoCoE8AHSAZVgCcBLA1UABWgEM8BzM+AVwDsATAGiwoBnUENANQAd0gAjQRVSQAUCEmYKsTKGYUAbpGF4OY0BoadYKdJMoL+gzAzIoz3UNEiPOofEVKVqAHSKymAAmkYI7NCuqGqcANag8ABmIjQUXrFOKBJMggBcISGgoAC0oACCoASMFmgY7p7ehCTkVOle4jUMdRLYTqCc8LEZzCZmoNJODPHFZZXVtZYYkAAeRJTInDQS8po+rf40gnjbDKv8LqD2jpbYoACqAEoAMsK7sUmxkGSCc+VVQQuaTwVb1UBrDYULY7PagbgUZLJH6QbYmJAECjuMigZEMVDsJzCFLNXxtajBBCcQQ0MwAUVWDEQNUgADVHBQGNJ3KAALygABEAAkYNAMOB4GRogLFFTBPB3AExcwABT0xnM9zsyhc9wASmCKhwDQ8ZC8iElzhB7Bo3zcZmY7AYzEg-Fg0HUiS58D0Ii8AoZTJZggFSRxAvADlQAHJhAA5SASAVBFQAeW+ZF2gldWkgx1QjgUrmkeFATgtOlGWH0KAQiBhwiudokkuiIgMHBx3RYbC43CCJSAA" target="_blank">TypeScript사이트 (누르면 이동합니다.)</a>로 가서 Playground에 가면 type스크립트로 작성한 걸 javascript로 바꿔주는데  
type 스크립트는 항상 파라미터나 리턴 타입에 타입을 명시하도록 되어있다. 


### 2. Parameters
1. premitive parameters: 메모리에 value가 그대로 저장되어있기 때문에 value가 전달이 된다.
2. object parameters: 메모리에 레퍼런스가 저장되어지므로 reference가 전달되어진다.

```javascript
function changeName(obj) {
  obj.name = 'coder';
} // obj이름을 다 'coder'로 바꿈 
const ellie = { name: 'ellie'} ;
changeName(ellie);
console.log(ellie); //결과 name: "coder"
```

### 3. Default parameters (added in ES6)
```javascript
function showMessage(message, from) {
  console.log(`${message} by ${from}`);
}
showMessage('Hi!'); //를 출력해보면 Hi! by undefined로 나온다. from을 정의해주지 않았기 때문에
```
ES6 이전에는 from을 정의하기 위해서
```javascript
function showMessage(message, from) {
  if (from === undefined) {
    from = 'unknown'; // 이런식으로 넣어줬다.
  }
  console.log(`${message} by ${from}`);
}
showMessage('Hi!');
```
하지만 이제는 그럴 필요 없이
```javascript
function showMessage(message, from = 'unknown') { //parameter 옆에 바로 적어주면 된다.
  console.log(`${message} by ${from}`);
}
showMessage('Hi!');
```

### 4. Rest parameters (added in ES6)
```javascript
function printAll(...args) { // ' ... ' 을 rest 파라미터라고 부른다. 배열이다.
  for (let i = 0; i < args.length; i++) {
    console.log(args[i]);
  }
}
printAll('dream','coding','ellie'); //인자를 지금 3세개를 전달했다. 즉 저 args는 3개의 인자를 담고 있는 배열이다. 
```
#### for of를 이용해서 더 간단하게 출력할 수 있다.
```javascript
function printAll(...args) {
  for (const arg of args) {
    console.log(arg);
  }
}
```
### 5. Local scope 스코프 {} 
밖에서는 안이 보이지 않고 안에서만 밖을 볼 수 있다. 
```javascript
let globalMessage = 'global'; // global variable
function printMessage() {
  let message = 'hello';
  console.log(message); // local variable 지역 변수
  console.log(globalMessage);
}
```
{} 스코프 안에서 처리된 것들은 안에서만 할 수 있다. 
중첩된 함수에서 자식함수는 부모함수의 정의된 값에 접근이 가능하지만 
안을 벗어나면 자식함수에는 접근할 수 없다.

### 6. Return a value
```javascript
function sum(a,b) {
  return a + b; // return 타입이 없는 함수들은 return undefined; 가 생략이 되어있는 것. 
}
const result = sum(1, 2); //3
console.log(`sum: ${sum(1, 2)}`);
```

### 7. Early return, early exit 빨리 리턴해 빨리 엑싯해
안좋은 코드
```javascript
function upgradeUser(user) {
  if (user.point > 10) {
    // long upgrade logic.. user.point가 10 이상일때 무언가 업그레이드 시키는 로직이 있다 치자
  }
}
```
좋은 코드
```javascript
function upgradeUser(user) {
  if (user.point <= 10) {
    return; // 조건이 맞지 않을 때를 빨리 return해서 함수를 종료하고 
  }
    // long upgrade logic.. : 조건이 맞을 때만 logic을 실행하는 게 더 좋다.
}
```

## Fuction expression
- 함수는 다른 변수와 마찬가지로 변수에 할당이 되고 function에 파라미터로 전달이 되며 리턴값으로도 리턴이 된다. 

```javascript
const print = function () { //함수를 선언함과 동시에 변수에 할당 , 이렇게 함수에 이름이 없는 것을 anonymous function이라고 한다. 
  console.log('print');     //이름이 있는 것 : named function이라고 한다.
};
print(); //print 출력
const printAgain = print; 
printAgain(); //print 출력
```

### 1. function declaration과 function expression의 가장 큰 차이점 
- function expression은 할당된 다음부터 호출이 가능하다.
- function declaration은 호이스트가 된다. 즉 함수를 선언하기 전에 호출 가능

### 2. Callback function using function expression
```javascript
function randomQuiz(answer, printYes, printNo) { //printYes, printNo : callback 함수
  if (answer === 'love you') {
    printYes();
  } else {
    printNo();
  }
}

const printYes = function () { //이름이 없는 anonymous function이 쓰여짐
  console.log('yes!');
};
const printNo = function print() { //named fuction 쓰여짐. 
  console.log('no!');
  )
}
randomQuiz('wrong', printYes, printNo);  
randomQuiz('love you', printYes, printNo);
```
#### anonymous function 
#### named fuction
#### Arrow function 
- 항상 anonymous 함수이다.

```javascript
const simplePrint = function () {
  console.log('simplePrint!');
};
const simplePrint = () => console.log('simplePrint!');
// arrow 함수는 저렇게 화살표로 간단하게 함수를 만들 수 있다. 
const add = (a, b) => a + b; 
// 이걸 function express로 바꾸려면
const add = function (a, b) {
  return a + b;   
};
// 조금 더 복잡해지는 경우 블록을 쓸 수도 있다.
const add = (a, b) => {
  // do something more 
  return a * b; // 이 경우에는 꼭 return을 적어줘야한다. 
};
```

#### IIFE
  : Immediately Invoked Function Expression

```javascript
(function hello() {
  console.log('IIFE');
})();
// 저렇게 가로로 묶어주고 ();를 해주면 바로 호출된다. 
// 잘 쓰이지는 않음
```


퀴즈  
function calculate(command, a, b)  
command: add, substract, divide, multiply, remainder  
function calculate라는 함수를 만들어서 입력받은 command에 따라서 a,b의 값을 더하거나 빼거나 나누거나..