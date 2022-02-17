---
title: "프로그래머스 코딩테스트(JavaScript) Lv.1 - 평균 구하기"
date: 2022-02-13 14:25:18+0900
category: coding-test
tags:
  - level1
  - coding-test
header:
  teaser: "/assets/post_img/22-02-13-02.png"
---
<br>

## 🔹 평균 구하기
```js
function solution(arr) {
    var answer = 0;
    return answer;
}
```

## 🔹 문제 설명
정수를 담고 있는 배열 arr의 평균값을 return하는 함수, solution을 완성해보세요.

## 🔹 제한 조건
- arr은 길이 1 이상, 100 이하인 배열입니다.
- arr의 원소는 -10,000 이상 10,000 이하인 정수입니다.

## 🔹 예시

arr [1, 2, 3, 4] 
return 2.5 
<br>
arr [5, 5]
return 5

## 🔹 방법 1 
```js
function solution(arr) {
    var answer = 0;
    for(let i=0; i<arr.length; i++){
        answer = answer + arr[i];
    }
     return (answer/arr.length);
}
```

## 🔹 방법 2
- reduce 이용하기
> reduce() 메서드는 배열의 각 요소에 대해 주어진 reducer 함수를 실행하고 하나의 결과값을 반환한다.    
> 배열.reduce((누적값, 현재값, 인덱스, 요소) => {return 결과}, 초깃값);
> <https://www.zerocho.com/category/JavaScript/post/5acafb05f24445001b8d796d>

```js
function solution(arr) {
    return arr.reduce((a,b) => a + b) / arr.length;
}
```
## 혼잣말
reduce.. 기억하자 reduce, repeat, \n