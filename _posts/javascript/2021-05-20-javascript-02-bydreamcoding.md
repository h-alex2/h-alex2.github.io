---
title: "Dream Coding-JavaScript 03강"
date: 2021-05-22
category: javascript
tags:
  - JavaScript
toc: true
toc_sticky: true
toc_label: “3. 데이터타입, data types, let vs var, hoisting”
---

<br>
{% include video id="OCCpGh4ujb8" provider="youtube" %}
<br>

  

 Use scrict
 : ES5에 추가되었다. 
 use this for Valina Javascript. 바닐라 자바스크립트를 시작하기 전엔 꼭 

```javascript
'use strict';
```
### I. 변수

#### 1. let 
: ES6에 추가되었다.

```javascript
let globalName = 'global name';
let name = 'ellie';
console.log(name);
// console을 보면 ellie라는 값이 나온다.
name = 'hello';
console.log(name);
// hello 로 변경되어서 나온다.
```

#### 2. 블럭 설정하기
: { ,} 블럭을 설정하게되면 블럭 안에서만 가능하다.
   블럭을 쓰지 않고 파일 안에 바로 쓰는 것을 글로벌 스콥이라고 한다.
   글로벌한 변수들은 어플리케이션이 실행되는 순간부터 끝까지 메모리에 탑재되어있어서 최소한으로 쓰는 게 좋다.

```javascript
{
let name = 'ellie';
console.log(name);
name = 'hello';
console.log(name);
}
```

#### 3. var
: 자바스크립트에서(mutable 타입에서) 변수를 선언할 수 있는 키워드는 딱 하나 __let__ 그 전에는 var를 썼다.
  - var를 쓰면 안되는 이유 
    - var는 값을 선언하기도 전에 쓸 수가 있다.  
    - var hoisting 어디에서 선언했는지 상관없이 항상 제일 위로 선언을 끌어올려주는 것.
    - 블럭스콥이 없다. : 메모리를 많이 먹게 된다.


#### 4. Constants : const
  : 한 번 할당하면 값이 절대 바뀌지 않는 것
  - 변경이 가능한 것 : mutable
  - 변경이 가능하지 않은 것 : immutable
  <br>
  - immutable 데이터타입을 선호한다.
    <reason>
    1. Security : 보안상의 이유
    2. Thread safety : 쓰레드의 안정성. 다양한 쓰레드들이 동시에 변수에 접근해서 값을 변경할 수도 있기 때문에
    3. human mistakes를 줄여준다.
//왠만해선 const를 쓰는 게 좋다.

```javascript 
const daysInweek = 7;
const maxNumber = 5;
```

#### 5. 변수 선언 키워드 : let, const
정리
  : 자바스크립트에서 변수를 선언할 수 있는 키워드는 딱 두 가지.
  1. mutable type : let
  2. immutable type : const


### II. Variable types

### 1. primitive
  : 더 이상 작은 단위로 나눠질 수 없는 _single item_(한가지의 아이템을 말한다.)

  : number, string, boolean, null, undefiend, symbol

#### 1. number
  : c언어나 java같은 경우에 숫자를 쓰려면 많은 양의 숫자, 적은 숫자 이렇게 따로 타입을 정해줘야한다. (메모리 할당 문제 때문에)
  : 하지만 javascript에서는 number만 쓰면 된다. 

``` javascript
const count = 17; //integer 정수
const size = 17.1; // decimal number 소수점의 숫자
console.log(`value: ${count}, type: ${typeof count}`);
console.log(`value: ${size}, type: ${typeof size}`);
//이렇게 입력하게 되면 value : 정의한 것, type : number로 나오게 된다.
```

#### 1-2. number : infinity, -infinity, NAN
  : special numeric values

```javascript
const infinity = 1 / 0; //positive한 1이나 숫자를 0으로 나누면 infinity가 된다.
const negativeInfinity = -1 / 0;
const nAn = 'not a number' / 2;
console.log(infinity); //Infinity로 나옴
console.log(negativeInfinity); //-Infinity로 나옴
console.log(nAn); //NaN으로 나옴
```
<span style= "color:red"> 나중에 연산을 할 때 0인지 숫자인지 확인하지 않고 연산을 해버리게되면 숫자가 아닌 결과로 에러가 나올 수 있다.</span>


##### 2-1. bigInt (fairly new, don't use it yet)
  : 새롭게 추가된 기능이라 아직 쓰지는 X
```javascript
const bigInt = 1234567890123456789012345678901234567890n; 
// over (-2**53 ~ 2*53 ) -2의 53승부터 2의 53승까지만 표현 가능
// 숫자 끝에 'n'만 붙이면 bigint라고 간주되어짐
console.log(`value: ${bigInt}, type: ${typeof bigInt}`);
// 최근에 bigInt라는 기능이 추가됨. 추가된지 얼마 안돼서 안쓰는 게 나음
```

#### 2. string 
```javascript
const char = 'c';
const brendan = 'brendan';
const greeting = 'hello' + brendan;
```
: 기호를 이용해서 일반 string과 다른 변수를 붙일 수 있다.

```javascript
console.log(`value: ${greeting}, type: ${typeof greeting}`);
const helloBob = `hi ${brendan}!`;
```
template literals (string) or template string이라고 불리는 걸 많이 쓴다.  
즉 원하는 변수를 적고 옆에 *__달러 sign $과 { }기호__* 를 이용하면 변수의 값이 자동적으로 입력되게된다.

```javascript
console.log(`value: ${helloBob}, type: ${typeof helloBob}`);
```
: 한가지 글자든 여러 글자든 string으로 할당이 된다.
 ` ` 이 백틱을 이용해서 출력하게되면 +를 쓰지 않고 앞과 뒤만 묶어주면 출력이 가능하다.

기존의 + 기호를 이용해서 출력하려면
```javascript
 console.log('value: ' + helloBob + ' type ' + typeof helloBob); 
 : 번거롭다
```
#### 3. boolean : 참과 거짓
false : 0, null, undefined, NaN, '' <br>
true : any other value

```javascript
const canRead = true; //true라고 값을 할당시켜도 되고
const test = 3 < 1; //3보다 1이큰건 거짓이니까 false로 할당
```

#### 4. null
  : 아무것도 아닌 것
`let nothing = null;` 아무것도 아니라고 지정하는 것 

#### 5. undefined
  : let x; 아무것도 할당되지 않은 상태가 바로 undefined상태
    `let x=undefined;` 라고 해도 된다. 
    `console.log(`value: ${x}, type: ${typeof x}`);` = undefined로 나옴

#### 6. symbol, create unique identifiers for objects

```javascript
const symbol1 = Symbol('id');
const symbol2 = Symbol('id');  
: 동일한 id를 가지고 symbol을 만들었지만 저 symbol1, symbol2 는 다른 것이다
console.log(symbol1 === symbol2); //faulse로 나온다. 

같은 걸로 만들려면 for을 넣으면 된다.
const gSymbol1 = Symbol.for('id');
const gSymbol2 = Symbol.for('id');
console.log(gSymbol1 === gSymbol2); for을 넣었을 떄는 True로 나온다.
console.log(`value: ${symbol1}, type: ${typeof symbol1}`); 
symbol은 바로 출력하게 되면 에러가 뜬다.
항상 .description을 이용해서 스트링으로 변환하여 출력해야한다.
```
    
### 2. object
  : single 아이들을 여러개 묶어서 한 단위로 박스로 관리할 수 있게 해주는 box container  
  : function, first-class function

object, real-life object, data structure
object : 일상생활에서 보는 물건과 물체를 대표하는 박스 형태
```javascript
const ellie = {name:'ellie', age:20};
//ellie는 const로 정해져있어서 다른 오브젝트로 할당이 불가하지만 오브젝트 안에는 
//name과 age라는 값은 다른 값으로 할당이 가능하다. 
ellie.age = 21; // 변경이 가능하다.
```

### III. Dynamic typing: dynamically typed language
  - 선언할 떄 어떤 타입인지 선언하지 않고 프로그램에 동작할 때 할당된 값에 따라서 타입이 변경될 수 있다는 것을 의미
  - 빠르게 할 때 굉장히 유연하게 쓸 수 있는 언어지만 다수의 엔지니어들이 다이나믹 타이핑때문에 에러를 만든다.

__c, java : statically type language__
 : 변수를 선언할 때 어떤 타입인지 결정해서 타입을 같이 선언

```javascript
let text = 'hello'; //: 할당하게 되면 text는 자동적으로 string이라는 변수가 된다.
text = 1; //: text에 1이라고 넣어주면 type이 number로 변한다. 
text = '7'+5; //: 문자열 + 숫자는 string으로 type이 변환되면서 75가 나온다. 
text = '8'/'2'; //: 숫자를 나눌 수 있는 나누기를 연산자, 스트링안에는 숫자가 있으니 number로 나온다.
```

많은 엔지니어들이 text라는 변수 이름을 통해서 string이라고 생각하게된다. 
```javascript
let text = 'hello'
console.log(text.charAt(0)); 
//text의 제일 첫번째(0이 제일 첫번째)를 콘솔에 출력하게 되면 h가 나온다.
text = 7 + 5; //근데 중간에 이런 것 때문에 text가 number로 변하게 되면 
console.log(text.charA(0)); //error가 뜨게된다. 
//-> 이 이유때문에 typescript가 나오게 된 것. 
```
