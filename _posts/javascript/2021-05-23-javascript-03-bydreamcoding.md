---
title: "Dream Coding-JavaScript 04강"
date: 2021-05-23
category: javascript
tags:
  - JavaScript
toc: true
toc_sticky: true
toc_label: “4. 코딩의 기본 operator, if, for loop 코드리뷰 팁 ”
---

<br>
{% include video id="YBjufjBaxHo" provider="youtube" %}
<br>



#### 1. String concatenation 문자열 병합
>'+' 기호를 이용해서 합해서 새로운 문자로 바꿀 수 있다  


```javascript
console.log('my' + 'cat'); 
console.log('1' + 2);
console.log(`string literals: 1 + 2 = ${1 + 2}`); //console : string literals: 1 + 2 = 3
```
` `  백틱을 이용해서 string literals를 만들 수 있다. 달러값을 이용하면 변수값을 계산해서 
스트링으로 포함하여 합해질 수 있다. 

```javascript
console.log(`string literals: 
''''
1+ 2 = ${1 + 2}`);
```
출력해보면 띄어쓰기는 물론 ''''까지 출력되는 걸 볼 수 있다.

`console.log('ellie's book');`  
    : 이렇게 만들게 되면 에러가 뜨고 특수기호가 인식이 되질 않는다. 이럴경우엔
`console.log('ellie\'s book'); `  
    : 백슬러시를 \ 를 이용해서 싱글코트 ' 를 넣어줘야 인식이 된다. 또는 ' 로 감싸져있는 걸 " 로 바꾼다.  
    : 새로 줄바꿈을 할 떄는 \n 을 넣어줘야한다.  
        `console.log('ellie\'s \nbook');`  
        `console.log("ellie's book");`  
        `// \t //` : tab키   
 

#### 2. Numeric operators 숫자 연산자

```javascript
console.log(1 + 1); //add
console.log(1 - 1); //substract
console.log(1 / 1); //divide
console.log(1 * 1); //multiply
console.log(5 % 2); //remainder
console.log(2 ** 3);//exponentiation제곱
```


#### 3. Increment and decrement operators 증감연산자 ++

```javascript
let counter = 2;
const preIncrement = ++counter; //변수 앞에 ++기호를 붙여주게되면 바로 preIncrement라고 하는 것이다.
// counter = counter + 1;
// preIncrement = counter; 이 두가지가 위와 같은 말
console.log(`preIncrement: ${preIncrement}, counter: ${counter}`);
// -> preIncrement: 3 , counter : 3으로 나오게 된다.


//반대로
const postIncrement = counter++; //변수 뒤에 ++기호를 붙이면
// postIncrement = counter;
// counter = counter + 1; 이것과 같은 말
// 1. counter가 3이니 ponIncrement에 3이 할당이 되고
// 2. 3+1이니 4로 업데이트가 되었을 것이다.
console.log(`postIncrement: ${preIncrement}, counter: ${counter}`)
// -> postIncrement : 3 counter : 4 
```

#### 4. Assignment operators 할당하는 오퍼레이터  

```javascript
let x = 3;
let y = 6;
x += y; // x = x + y;와 같은 말
x -= y; // x = x - y;
x *= y; // x = x * y;
x /= y; // x = x / y; 
```

#### 5. Comparison operators 비교하는 오퍼레이터  

```javascript
console.log(10 < 6);
console.log(10 <=6);
console.log(10 > 6);
console.log(10 >= 6);
``` 

#### 6. ⭐ Logical operators 논리 연산자 : || (or), && (and), ! (not) ⭐   

##### || 뜻 : or 하나라도 트루면 다 트루

```javascript
const value1 = true;
const value2 = 4 < 2;
console.log(`or: ${value1 || value2 || check()}`);
```
- 셋중에 하나라도 트루가 되면 트루로 계산이 됨
- 맨 처음이 트루라면 뒤를 계산하지 않고 맨 처음만 계산하고 멈춘다. 하나라도 트루면 트루니까
- expression이나 함수를 호출하게 되는 아이들은 제일 뒤에 배치하는 것이 효율적이다.
    : true가 되면 거기서 멈추니까 가벼운 아이들 먼저 배치


##### && 뜻 : and 모두가 다 트루여야 트루로 나온다.

```javascript
console.log(`and: ${value1 && value2 && check()}`);
```
- 셋중에 하나라도 false면 뒤는 계산 하지 않는다.  
- often used to compress long if-statement and는 간단하게 null 체크할때도 많이 쓰인다. 
- nullableObject && nullableObject.something 이 오브젝트가 널이면 false가 되기 때문에 뒤가 실행이 안된다. 
    : 즉 null오브젝트가 null이 아닐때만 뒤 something이라는 값을 받아오게 된다.    

##### ! 뜻 : not
```javascript
console.log(!value1); 
```
- 값을 바꿔주는 것 value1이 ture기 때문에 값이 false로 나온다.


#### 7. Equality    

##### == : loose equality 
- == 두개의 이퀄사인을 쓰게되면 loose equality라고 부른다. 타입을 변경해서 검사를 하기 때문 
- with type conversion 

```javascript
const stringFive = '5';
const numberFive = 5;
console.log(stringFive == numberFive); //true
console.log(stringFive != numberFive); //false true인데 !때문에 false로
```
> 문자열이긴 한데 안에 들어있는건 5니 똑같다고 보는 것   

##### === : strict equality
- 타입이 다르면 다르다고 하는 것, 타입 변경 없이 검사

```javascript
console.log(stringFive === numberFive); //false
console.log(stringFive !== numberFive); //true
```
> 왠만해선 strict equality를 이용해서 검사하는 게 더 좋다.
이퀄리티를 공부할 땐 오브젝트를 더 신경써서 공부하기


##### object equality by reference
  : object는 메모리에 탑재될 때 reference의 형태로 저장 : ovject equality by reference
```javascript
const ellie1 = {name: 'ellie'};
const ellie2 = {name: 'ellie'}; 
    // ellie1과 2에는 똑같은 데이터가 들어있는 오브젝트 이지만 실제로 메모리는 1, 2에는
        // 각각 다른 레퍼런스가 들어있고 그 다른 레퍼런스는 서로 다른 오브젝트를 가리키고 있다.

const ellie3 = ellie1; 
    // ellie3은 ellie1의 레퍼런스를 가지고 있게 된다.
    
console.log(ellie1 == ellie2); // false 각각 레퍼런스가 다르기 때문
console.log(ellie1 === ellie2); // false 
console.log(ellie1 === ellie3); // true
```



###### 퀴즈
```javascript
console.log(0 == false); //true
console.log(0 === false); //false
console.log('' == false); //true
console.log('' === false); //false
console.log(null == undefined); //true
console.log(null === undefined); //false
    // boolean 참과 거짓 참고 
        // false = 0, null, undefined, NaN, "
        // true = any other value"
```


#### 8. Conditional operators: if
```javascript
const name = 'ellie';
if (name === 'ellie') {
    console.log('Welcome, Ellie!');
}

const name2 = 'coder';
if (name2 === 'ellie') {
    console.log('Welcome, Ellie!');
} else if (name2 === 'coder') {
    console.log('Your are amazing coder');
}

const name3 = 'nobody';
if (name3 === 'ellie') {
    console.log('Welcome, Ellie!');
} else if (name3 === 'coder') {
    console.log('Your are amazing coder');
} else {
    console.log('unkwnon');
}
```

#### 9. Ternary operator: ? 값을 할당하거나 출력할 때 간단하게 쓰는 것
```javascript
// condition ? value1 : value2;
console.log(name === 'ellie' ? 'yes' : 'no');
    // 이것의 뜻은 name === ellie가 맞니 (?) 맞으면 yes 아니면(:) no
    // 간단할때만 쓰는 게 좋다.
```

#### 10. Switch statement   
- use for multiple if checks
- use for enum-like value check
- use for multiple type checks in TS
```javascript
const browser = 'IE';
switch (browser) {
    case 'IE':
        console.log('go away!');
        break;
         // browser의 값이 IE면 밑 console을 실행하게 되고 멈춘다.
    case 'Chrome':
    case 'Firefox': // 이렇게 묶어서도 됨
        console.log('I love you!');
        break;
    default:
        console.log('same all!');
        break;
}
```

#### 11. Loops
##### while loop
- while loop, while the condition is truthy, true일때 까지 loop
-  body code is exucuted. 
```javascript
let i = 3;
while (i > 0) {
    console.log(`while: ${i}`);
    i--;
}
```
##### do while loop
- "do while" do while loop, body code is executed first, then check the condition. 
- 먼저 블록을 실행한 다음에 조건이 맞는지 안맞는지 검사 
```javascript
do {
    console.log(`do while: ${i}`);
    i--;
} while (i > 0);
```

##### for loop
- for loop, for(begin; condition; step)
- for(1.시작하는 문장; 2.컨디션; 3.어떤스텝을 밟을건지) 저 시작하는 문장은 __맨 처음 "한번만 실행한다"__
```javascript
for (i = 3; i >0; i--) {
    console.log(`for: ${i}`);
}

for (let i = 3; i > 0; i = i - 2 ) { 
    // inline variable declaration 인라인 안에 let이라는 지역변수를 선언해서 작성하는 것
    console.log(`inline variable for: ${i}`);
}
```
##### for nested loops
```javascript
for (let i = 0; i < 10; i++) {
     for (let j = 0; j < 10; j++) {
         console.log(`i: ${i}, j+${j}`);  
    }
}
```
##### break, continue
- break : 완전히 끝내는 것 
- continue : 지금 것만 스킵하고 다음 스텝으로 넘어가는 것 


###### 퀴즈
- 숫자를 0부터 10까지 짝수인 아이들만 프린트를 컨티뉴를 이용하여 만들어보자


```javascript
for (let i = 0; i < 11; i++) {
    if (i % 2 !== 0) {
        continue;
    }
    console.log(`q1. ${i}`);
}
// 이것보다

for (let i = 0; i < 11; i++) {
    if (i % 2 === 0) {
        console.log(`q1. ${i}`);
    }
}
// 이렇게 하면 됨.
```

- 주어진 숫자의 범위인 0부터 10까지를 루핑하는 것을 작성하되  숫자 8을 만나면 break하게

```javascript
for (let i = 0; i < 11; i++) {
    if (i > 8) {
        break;
    }
    console.log(`${i}`);
}
```

루핑 레이블은 잘 안씀 