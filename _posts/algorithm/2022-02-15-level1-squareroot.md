---
title: "프로그래머스 코딩테스트(JavaScript) Lv.1 - 정수 제곱근 판별"
date: 2022-02-15 17:31:01+0900
category: coding-test
tags:
  - level1
  - coding-test
header:
  teaser: "/assets/post_img/22-02-15-01.png"
---
<br>

## 🔹 정수 제곱근 판별
```js
function solution(n) {
    var answer = 0;
    return answer;
}
```

## 🔹 문제 설명
임의의 양의 정수 n에 대해, n이 어떤 양의 정수 x의 제곱인지 아닌지 판단하려 합니다.
n이 양의 정수 x의 제곱이라면 x+1의 제곱을 리턴하고, n이 양의 정수 x의 제곱이 아니라면 -1을 리턴하는 함수를 완성하세요.

## 🔹 제한 조건
- n은 1이상, 50000000000000 이하인 양의 정수입니다.

## 🔹 예시
<table class="table" style="width:200px">
        <thead><tr>
<th>n</th>
<th style="text-align: center">return</th>
</tr>
</thead>
        <tbody><tr>
<td>121</td>
<td style="text-align: center">144</td>
</tr>
<tr>
<td>3</td>
<td style="text-align: center">-1</td>
</tr>
</tbody>
      </table>

## 🔹 입출력 예#1
121은 양의 정수 11의 제곱이므로, (11+1)를 제곱한 144를 리턴합니다.

## 🔹 입출력 예#2
3은 양의 정수의 제곱이 아니므로, -1을 리턴합니다.


## 🔹 내가 푼 방법

```js
function solution(n) {
    return (Number.isInteger(n ** (1/2)) ? (n ** (1/2)+1) * (n ** (1/2)+1) : -1);
}
```
- 계속 제곱되기 전의 수를 구하는 공식이 뭘까 생각했는데.. 저렇게 구하면 되는 걸 바보같이 ㅠ 
- 하루종일 풀었다. 결국엔 검색으로 알아냈고 허무하군.. 
- `Number.isInteger` : 정수인가 묻는 것
- `n ** (1/2)`를 했을 때 제곱근이 아니라면 실수가 나온다. 


## 🔹 방법 2
- n을 while에다가 가져다 쓰면 되는구나.. 맞아 그렇지

```js
function nextSqaure(n){
  var result = 0;
  var x = 0;
  while (x*x < n){
    x++;
  }
  if (x*x == n){
    x++;
    result = x*x; 
  }else{
    result = 'no';
  }

  return result;
}
```
