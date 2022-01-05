---
title: "Dream Coding-JavaScript 08강"
date: 2021-05-28
category: javascript
tags:
  - DreamCoding
toc: true
toc_sticky: true
toc_label: “8. 배열 제대로 알고 쓰자. 자바스크립트 배열 개념과 APIs 총정리”
---


## Dream Coding-JavaScript 08강 - 8. 배열 제대로 알고 쓰자. 자바스크립트 배열 개념과 APIs 총정리
<link rel="stylesheet" type="text/css" href="/assets/CSS/markdown.css">

<br>
{% include video id="yOdAVDuHUKQ" provider="youtube" %}
<br>

## Array

### 1. Declaration 배열 선언 방법

1. new를 이용해서 오브젝트를 만드는 것처럼 new Array로 만들기
```javascript 
const arr1 = new Array(); //  
```

2. 더 흔한 방법 [ ] 이용하기
```javascript 
const arr2 = [1, 2];
```
배열이 인덱스를 기준으로 데이터가 저장이 되기 때문에
인덱스를 활용해서 어떻게 데이터를 검색하고 삭제하는지 정확하게 알아야한다.

### 2. Index position 인덱스를 통해서 어떻게 배열에 접근할 수 있는지

```javascript
const fruits = ['🍎', '🍌']
console.log(fruits); 
console.log(fruits.length); //2
console.log(fruits[0]) //🍎   배열은 숫자 인덱스에 해당하는 value들을 받아올 수 있다.
console.log(fruits[2]) //undefined
console.log(fruits[fruits.length -1]) //배열의 마지막 값을 부를 때
```
배열의 마지막 값을 부를 때 `배열이름.length -1` 

### 3. Looping 배열 모두 출력하기


1. 
```javascript
for (let i = 0; i < fruits.length; i++; ) {
    console.log(fruitsp[i]);
}
```

2. 
```javascript
for(let fruit of fruits) {
    console.log(fruit);
}
```

3. 더 간단한 방법 forEach 사용하기
```javascript
fruits.forEach(value: fruits, index: 1, array: fruits[]) => void, thisArg?: any : void;
```
콜백함수를 받아온다. __api를 모르겠다면 ctrl을 눌러서 api가 선언되어진 곳으로 가서
어떻게 사용할 수 있는지 설명을 꼭 보자.__

<details>

  <summary>forEach설명 (click!)</summary>
  <div markdown="1">

>   forEach(callbackfn: (value: T, index: number, array: T[]) => void, thisArg?: any): void;

> * Performs the specified action for each element in an array.
* @param callbackfn  A function that accepts up to three arguments. forEach calls the callbackfn function one time for each element in the array.
* @param thisArg  An object to which the this keyword can refer in the callbackfn function. If thisArg is omitted, undefined is used as the this value.
* 배열의 각 요소에 대해 지정된 작업을 수행합니다.
* @param callbackfn 최대 3 개의 인수를받는 함수입니다. forEach는 배열의 각 요소에 대해 callbackfn 함수를 한 번 호출합니다.
* @param thisArg this 키워드가 callbackfn 함수에서 참조 할 수있는 객체입니다. thisArg가 생략되면 undefined가이 값으로 사용됩니다.

  </div>

</details>  
<br>

```javascript
fruits.forEach(function() {
    console.log('he');
}); // he가 2번 출력된다. fruits안에 2개가 들어있어서

fruits.forEach(function(fruit, index, array) { //이름이 없는  anonymous 함수는 arrow함수를 쓸 수 있다.
    console.log(fruit, index, array); //보통 array는 쓰지 않는다.
//🍎 0 (2) ["🍎", "🍌"]
//🍌 1 (2) ["🍎", "🍌"] 

fruits.forEach((fruit) => console.log(fruit)); //arrow함수 사용하여 간소화 시키기 ! 
//🍎
//🍌
}); 
```

### 4. Addition, deletion, copy 배열을 추가, 삭제, 복사 

1. 끝에서 부터

- 배열의 끝에 아이템을 추가하고싶다. 
> `push`


```javascript
fruits.push('🍓', '🍑');
console.log(fruits);
//(4) ["🍎", "🍌", "🍓", "🍑"]
```

- 배열의 끝에서 부터 아이템을 지우고 싶다.
> `pop`

```javascript
fruits.pop();
console.log(fruits);
// (3) ["🍎", "🍌", "🍓"]
fruits.pop();
console.log(fruits);
// (2) ["🍎", "🍌"]
```

2. 앞에서 부터

- 배열의 앞에 아이템을 추가하고싶다.
> `unshift`

```javascript
fruits.unshift('🍓','🍋');
console.log(fruits);
//(4) ["🍓", "🍋", "🍎", "🍌"]
```

- 배열의 앞에서 부터 데이터를 지우고 싶다.
> `shift`

```javascript
fruits.shift();
fruits.shift();
console.log(fruits);
//(3) ["🍎", "🍌"]
```


#### 4-1. <span style= "color:red">shift, unshift은 pop, push보다 느리다</span>

이유  
: 뒤에 있는 데이터를 빼거나 추가하는 것은 뒤에 할당되어 있는 공간만 빼거나 추가하면 되기 때문에
앞의 데이터를 건드리지 않아도 된다. 하지만 앞에서 데이터를 건드릴려면 그 뒤의 데이터를 다 건드려야 하기 때문에 
배열의 길이가 길면 길수록 데이터를 많이 쓴다. 

#### 4-2. 배열의 중간에 삭제 또는 추가

```javascript
fruits.push('🍓',🍑','🍋')
console.log(fruits);

fruits.splice(1, 
//splice(start: number, deleteCount?: number): string[]
//The number of elements to remove.
//Removes elements from an array and, if necessary, inserts new elements in their place, returning the //deleted elements.
//@returns — An array containing the elements that were deleted.
// splice를 치고 입력하면 이런 설명이 나온다. 
```
- (start: number, deleteCount?: number) 인덱스 몇 번 부터 지울 것인지 번호를 입력하고, deleteCount: 몇 개를 지울 것인가. 만약 start:number만 입력한다면 그 숫자 뒤는 모두 지워진다.) 
- 저 설명 중 `?` 표시는 해도 되고 안해도 된다는 말이다. 

```javascript
fruits.splice(1, 1);
console.log(fruits); 
//(4) ["🍎", "🍓", "🍑", "🍋"]
fruits.splice(1, 1, '🍏', '🍉');
//(5) ["🍎", "🍏", "🍉", "🍑", "🍋"]
```
splice를 이용해 지울 수도 있고 저렇게 추가도 할 수 있다. 

### 5. 2가지의 배열을 묶어서 만들 수도 있다. : concat

```javascript
const fruits2 = ['🍈', '🍒']
const newFruits = fruits.concat(fruits2); 
console.log(newFruits);
//(7) ["🍎", "🍏", "🍉", "🍑", "🍋", "🍈", "🍒"]
```

<details>

  <summary>concat설명 (click!)</summary>
  <div markdown= "1">
>   * Adds all the elements of an array into a string, separated by the specified separator string.  
* @param separator A string used to separate one element of the array from the next in the resulting string. If omitted, the array elements are separated with a comma.

> * 배열의 모든 요소를 지정된 구분자 문자열로 구분하여 문자열에 추가합니다.  
* @param separator 배열의 한 요소를 결과 문자열에서 다음 요소와 구분하는 데 사용되는 문자열. 생략하면 배열 요소가 쉼표로 구분됩니다.
  </div>

</details>

### 6. Searching 검색  : find the index

- 사과가 몇 번째 인덱스에 있는 건지 알고싶다면?  
    : `indexOf` api 사용

```javascript
console.log(fruits);
//(5) ["🍎", "🍏", "🍉", "🍑", "🍋"]
console.log(fruits.indexOf('🍎')); 
// 0 (0번째에 있다고 나온다. )
console.log(fruits.indexOf("🥑"));
// -1 : 없는 것을 찾으면 -1이 출력
```

#### 6-2. includes : 배열에 아이템이 있는지 없는지 true, false로 
```javascript
console.log(fruits.includes("🍉"));
// true
console.log(fruits.includes("🥑"));
// false
```

#### 6-3. lastIndexOf

```javascript
fruits.push('🍎'); //사과 하나를 끝에 넣어주고 
console.log(fruits); //(6) ["🍎", "🍏", "🍉", "🍑", "🍋", "🍎"] 이렇게 사과가 맨 앞과 뒤 2개가 있다.
console.log(fruits.indexOf('🍎')); // 0 
console.log(fruits.lastIndexOf('🍎')); // 5 : 맨 마지막에 나온 사과의 인덱스가 출력이 된다. 
```

### 숙제 
배열이 선언된 곳 lib.es5.d.ts 파일로 가서 array api들에 대해 한번씩 읽어보기