---
title: "프로그래머스 코딩테스트(JavaScript) Lv.1 - 자연수 뒤집어 배열로 만들기"
date: 2022-02-15 00:33:07+0900
category: coding-test
tags:
  - level1
  - coding-test
header:
  teaser: "/assets/post_img/22-02-13-08.png"
---
<br>

## 🔹 자연수 뒤집어 배열로 만들기
```js
function solution(n) {
    var answer = [];
    return answer;
}
```

## 🔹 문제 설명
자연수 n을 뒤집어 각 자리 숫자를 원소로 가지는 배열 형태로 리턴해주세요. 예를들어 n이 12345이면 [5,4,3,2,1]을 리턴합니다.

## 🔹 제한 조건
- n은 10,000,000,000이하인 자연수입니다.

## 🔹 예시
<table class="table" style="width:200px">
        <thead><tr>
<th>n</th>
<th>return</th>
</tr>
</thead>
        <tbody><tr>
<td>12345</td>
<td>[5,4,3,2,1]</td>
</tr>
</tbody>
      </table>

## 🔹 내가 푼 방법
```js
function solution(n) {
    var arrayN = (n+"").split("").map(num => Number(num));
    var answer = [];

    for(let i=arrayN.length-1; i>= 0; i--){
        answer.push(arrayN[i]);
    }
    return answer
}
```

## 🔹 방법 2
- `reverse` 사용하기
  - 배열의 순서를 반전합니다. 
  - Number() 말고 parseInt() 도 가능
  - Numbr() : 숫자 출력 
  - parseInt() : 정수만 뽑아서 출력
```js
function solution(n) {
    var arrayN = (n+"").split("").map(num => Number(num));
    var answer = arrayN.reverse();
    return answer;
}
```
