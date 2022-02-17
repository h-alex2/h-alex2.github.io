---
title: "프로그래머스 코딩테스트(JavaScript) Lv.1 - 정수 내림차순으로 배치하기"
date: 2022-02-16 11:25:17+0900
category: coding-test
tags:
  - level1
  - coding-test
header:
  teaser: "/assets/post_img/22-02-16-01.png"
---
<br>

## 🔹 정수 내림차순으로 배치하기
```js
function solution(n) {
    var answer = 0;
    return answer;
}
```

## 🔹 문제 설명
함수 solution은 정수 n을 매개변수로 입력받습니다. n의 각 자릿수를 큰것부터 작은 순으로 정렬한 새로운 정수를 리턴해주세요. 예를들어 n이 118372면 873211을 리턴하면 됩니다.

## 🔹 제한 조건
- n은 1이상 8000000000 이하인 자연수입니다.

## 🔹 예시
<table class="table" style="width:200px">
        <thead><tr>
<th>n</th>
<th style="text-align: center">return</th>
</tr>
</thead>
        <tbody><tr>
<td>118372</td>
<td style="text-align: center">873211</td>
</tr>
</tbody>
      </table>


## 🔹 내가 푼 방법

```js
function solution(n) {
    var num = (n+"").split("");
    var answer = num.sort((a, b) => b-a).join("")
    return Number(answer);
}
```
- `sort((a,b) => a-b)` : 오름차순
- `sort((a,b) => b-a)` : 내림차순 
- `Number(answer)` 말고 `answer*1` 해줘도 숫자로 바꿀 수 있다
- `parseInt(answer)` 


## 🔹 방법 2
- `reverse` 이용 
- `number + string = string` 
- `number * string = number`

```js
function solution(n) {
  const newN = n + "";
  const newArr = newN
    .split("")
    .sort()
    .reverse()
    .join("");

  return +newArr;
}
```
