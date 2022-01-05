---
title: "JavaScript 완전 Basic by Nomad Coders"
date: 2021-10-07
category: javascript
tags:
  - NomadCoders

toc: true
toc_sticky: true
toc_label: “Basic JavaScript”
---

## Variable 변수 
값을 저장하거나 유지하는 역할
1. __const__ 변수이름 = 값 ;  
	const : constant 상수: 변하지않는 값 
	절대 바뀔 수 없다.

2. __let__   
	변수지만 값이 바뀔 수 있다. 
	let 변수이름 = 값: 
	변수이름 = 다른값; 으로 바꿀 수 있다. 
	const는 불가능

3. __var__ (variable)   
	초기에는 변수를 설정하는 게 var 밖에 없었다. 
	var는 어떠한 규칙도 가지지 않고 설정한 후에 계속 바꿀 수 있다. 
	이제 거의 사용하지 않음


> 
js에서는 공백을 쓰고싶으면 공백 다음을 대문자로 쓴다.  
ex ) veryLong  
파이썬에서는  
ex ) very_long  


## Boolens
컴퓨터에 0, 1이 있듯이 true와 false가 있다.  

1. trus  

2. false  

3. null : nothing 아무 것도 없다.  
	false랑은 다르다.  
	false는 false라는 값이 있는 것  

4. undefined  


## Array
__<span style = "color:red"> use [ ]  </span>__  
`const week = ["mon", "tue", "wed", "thu", "fri", "sat", "sun"]; `

배열 중 ?번째 것을 출력하기
`console.log(week[?]);`

배열에 항목 추가하기
`week.push("항목");`


## Objects  
__<span style = "color:red"> use { } </span>__  
```javascript
const player = {
	name: "hyunjung",
	points: 10,
	fat: true,
};
```

<span style = "color:red"> { } 을 사용하고 
name, points, fat은 property라고 한다. 
</span>


object에는 = 를 사용하지 않는다. : 를 사용함  
- object는 업데이트가 가능하다.  
	const 는 바꿀 수 없지만 안에 있는 것은 바꿀 수 있다.   
	const 자체는 값이 있기 때문에 __true__ 라는 속성을 가진다.   
	그 true를 false로 바꾸려하면 오류가 생기지만 
	object안의 값을 바꾸는 것은 const 자체를 바꾸는 것이 아니기 때문에 가능하다.  

	`player.points = player.points + 15; `  

- object는 값(property) 추가가 가능하다.  
  `player.lastname = "pasta";` 	➞ 	가능

  `console.log(player);`  
  `console.log(player.name); = console.log(player["name"]);`  
  ➞ 이 말인 즉슨 console도 player와 같은 object라는 것   
    그 object인 console 안에 log가 있다. 라는 의미


## Function

: 계속 반복해서 사용할 수 있는 조각  
어떤 코드를 캡슐화해서, 실행을 여러 번 할 수 있게 해준다.   

__<span style = "color:red"> use ()  </span>__  

-string ➞ ""  
-array, list ➞ [ ]   
-function ➞ __( )__

__<span style = "background-color:skyblue"> function 만들기 </span>__
```javascript
function sayHello(){
  console.log("Hello!");
} 
```  
실행하려면 ➞ `sayHello(); `

1. argument란?   
  function을 실행하는 동안 어떤 정보를 function에게 보낼 수 있는 방법 
  `alert("hello");`  
  ➞ "hello"가 __argument__ 가 됨  



__<span style = "background-color:skyblue"> function에서 정보를 받을 수 있는 방법  </span>__

```javascript
function sayHello(nameOfPerson){
  console.log(nameOfPerson);
}
sayHello("a");
sayHello("b");
sayHello("c");

결과 
a
b
c
```


  - ( )가로 안에 nameOfPerson을 씀으로써 정보를 받게된다. 
  - sayHello( )안의 값들이 정보를 함수에 보내면 그 값들이 nameOfPerson이 되어 정보를 받게되는 것이다.   

__<span style = "background-color:skyblue"> 여러 개의 정보값 사용하기</span>__ 


```javascript
function sayHello(nameOfPerson, age){
  console.log("Hello my name is " + nameOfPerson + " and I'm " + age);
}
sayHello("a", 10);
sayHello("b", 23);
sayHello("c", 33);

결과
Hello my name is a and I'm 10
Hello my name is b and I'm 23
Hello my name is c and I'm 33
```

__<span style = "background-color:skyblue">object 내에서 함수 사용하기</span>__

```javascript
const player = {
  name: "nico",
  sayHello: function(otherPersonsName){
    console.log("hello! " + otherPersonsName);
  },
}
console.log(player.name);
player.sayHello("hyun");

결과 
nico
hello! hyun

```

__<span style = "background-color:skyblue"> return </span>__

```javascript
const age = 96;
function calculateKrAge(ageOfForeigner) {
  return ageOfForeigner + 2;
}

const krAge = calculateKrAge(age);
console.log(krAge);

결과
98
```
- return을 하고 나면 function은 끝이 나게된다. return 후에 console.log나 다른 것을 붙여도 함수계산은 이미 끝났기때문에 아무런 영향이 없게된다.
  
- console.log와 return의 차이점
  1. console.log 
    : console로 출력하는 기능만 가지고 있다. 그 값을 가지고 있진 않다.
  2. return 
    : 그 값 자체를 가지게 됨  



## conditionals 조건문

```javascript
const age = parseInt(prompt("How old are you?"));

if (isNaN(age) || age <0) {
  console.log("Please write a number");
} else if(age < 18) {
  console.log("You are too young.");
} else if(age >= 18 && age <= 50) {
  console.log("You can drink.");
} else if(age > 50 && age <= 80) {
    console.log("You should exercise.");
}
```

* type을 변경하는 방법

  - __parseInt__ : string to number 
    - “123”같은 string만 숫자로 바꿀 수 있다.
    - “aaa”는 처리하지 못해서 NaN으로 뜬다.

  - __isNaN__ : return a Boolean value
    - not a number : true
    - number : false 
    - boolean으로 반환하게 되면 조건문에 쓰기 유용하다.  
<br>

* 연산자 기호
  - and = &&
  - or = `||`
  - a === b 
    : a is b 
    : = 와 다르다 
  - a !== b
    : a is not b


