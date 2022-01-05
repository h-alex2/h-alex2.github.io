---
title: "Dream Coding-JavaScript 07강"
date: 2021-05-25
category: javascript
tags:
  - DreamCoding
toc: true
toc_sticky: true
toc_label: “7. 오브젝트 넌 뭐니?”
---

## Dream Coding-JavaScript 07강 - 7. 오브젝트 넌 뭐니?
<link rel="stylesheet" type="text/css" href="/assets/CSS/markdown.css">

<br>
{% include video id="1Lbr29tzAA8" provider="youtube" %}
<br>

### Object
<https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/Object>

__object는 {key : value} 의 집합체이다.__  
    : key : 우리가 접근할 수 있는 변수 property key는 항상 string 타입
      value : property가 가지고 있는 값  

### 1. Literals and properties

```javascript
const obj1 = {}; // 'object literal' syntax
const obj2 = new Object(); // 'object constructor' syntax
```
javascript에서는 class가 없어도 {} 괄호를 이용해서 object를 생성할 수 있다

```javascript
function print(person) {
    console.log(person.name);
    console.log(person.age);
}

const ellie = { name: 'ellie', age: 4};
print(ellie); // ellie, 4 
```


자바스크립트는 다이나믹 랭귀지 즉 동적인 언어라서 추후에 추가를 할 수도 있다.
동적으로 코딩하면 유지보수하기 힘들다. 
삭제도 가능하다.
```javascript
ellie.hasJob = true;

delete ellie.hasJob;
```

### 2. Computed properties 계산된 properties  
```javascript
console.log(ellie.name);
console.log(ellie['name']); //둘 다 같은 값. 
```
['name']안에 name은 꼭 string 타입 이어야한다. 
```javascript
ellie['hasJob'] = true; 라고 할당하게 되면 위 ellie.hasJob = true; 와 같다.
```
- 코딩하는 그 순간 그 키에 해당하는 값을 받아오고 싶을 때 . 을 쓴다.   
- 우리가 정확하게 어떤 키가 필요한지 모를 때. runtype에서 결정될 때 [' ']을 쓴다. 
기본적으로 코딩할 때는 . dot을 쓰는 게 맞다.   
실시간으로 우리가 원하는 키의 값을 가져오고 싶다면 computed properties를 쓰면 된다. 

```javascript
function printValue(obj, key) {
    console.log(obj.key);
}
printValue(ellie, 'name');
// -> undefined 
// 바로 저 console.log(obj.key) 에 obj에 key라는 properties가 없기 때문에 
// 이 때는 computed properties를 써야한다.
function printValue(obj, key) {
    console.log(obj[key]);
}
printValue(ellie, 'name'); //정상적으로 출력됨
```
: 나중에 동적으로 키의 값을 받아와야 할 때 유용하게 쓰일 수 있다. 

### 3. Property value shorthand  
```javascript
const person1 = {name: 'bob', age: 2};
const person2 = {name: 'steve', age: 3};
const person3 = {name: 'dave', age: 4};
// person4를 추가하고 싶다면 또 입력해야 할 것이다. 번거로움

function makePerson(name, age) { //이름을 추가하는 함수를 만들자.
    return {
        name = name,
        age = age, // 자바스크립트는 age와 value값이 같다면 age를 생략하고 age, 만 적어도 된다. 
    };
}

const person4 = makePerson('ellie', 30); // {name: "ellie", age: 30} 으로 나온다. 
```



### 4. Constructor
function makePerson을 보면 지난 시간에 살펴본 class같은 것 즉 template같은 것  
이전에 자바스크립트에 class가 없을 때는 저런식으로 많이 작성했다.  
이렇게 다른 계산을 하지 않고 object를 생성하는 함수들은 __대문자__ 로 시작하도록 만들고  
return을 쓰지 않는다 

```javascript
function Person(name, age) {
    this.name = name; //class constructor에서 했던 것처럼
    this.age = age; // 생략된 건 this = {}; 새로운 오브젝트를 만들어서 값을 넣고 결국엔 return해주는 것 
}

//호출을 할 때도 
const person4 = new Person('ellie, 30);
```

### 5. in operator : 해당하는 오브젝트안에 키가 있는지 없는지 확인하는 것 

```javascript
console.log('name' in ellie); //ellie 안에 name이 있나 없나 - 값은 true로 나온다.
```


### 6. for..in vs for..of  유용

for (key in obj) 
```javascript 
console.clear(); //이전 것들이 다 지워짐 

for (key in ellie) {
    console.log(key);
}
// ellie가 가진 모든 key가 출력된다. 
```

for (value of iterable)
```javascript 
const array = [1, 2, 4, 5];
//이 데이터의 모든 값들을 찍으려면
for(let i = 0; i < array.length ; i++) {
    console.log(array[i];
} //이렇게 하면 번거롭다. 

for(value of array) {
    console.log(value);
}// for of 를 이용하면 위와 같이 동일하게 나오는 걸 확인할 수 있다. 
```
### 7. Fun cloning
 
```javascript 
const user = { name: 'ellie', age: '20'};
const user2 = user;
// 여기 obj를 만들어놓고 user2가 user를 가리키게 해놨다. 
// 메모리에는 user2에도 user와 같은 동일한 레퍼런스가 들어있고 오브젝트를 가리키고 있다.
user2.name = 'coder';
console.log(user); // user 이름이 coder로 변경이 됨
```
value값을 다른 것에 넣는 예전 old 방법은 

```javascript 
const user3 = {}; //빈 괄호에 배정하고 
for (key in user) { //for in을 이용해서 user안에 있는 key들을 빙글 돌리면서 key를 user3에 넣는 것 
    user3[key] = user[key];
}
console.log(user3);
```
다른 방법으로는 __Object.assign__ 을 쓰는 것 
```javascript 
Object.assign 
// object: js에기본탑재되어있는 언어 중 하나 

const user4 = {}; //타겟을 정의한 다음
Object.assign(user4, user); // user의 value를 user4에 넣겠다. 
//또는
const user4 = Object.assign({}, user); 

```
새로운 함수나 api 를 쓸 때는
어떤 파라미터를 전달해서 어떤 값이 리턴되는지 꼭 확인하기

```javascript 
Object.assign 예 2 

const fruit1 = { color: 'red' };
const fruit2 = {color: 'blue', size: 'big'};
const mixed = Object.assign({}, fruit1, fruit2); //이렇게 한다면??
console.log(mixed.color); //blue로 나옴
console.log(mixed.size); //big으로 나옴
//즉 값을 뒤에 것으로 덮어씌우기 때문이다. 
```
