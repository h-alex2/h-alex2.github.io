---
title: "프로그래머스 코딩테스트(JavaScript) Lv.1 - 제일 작은 수 제거하기"
date: 2022-02-15 00:48:14+0900
category: coding-test
tags:
  - level1
  - coding-test
header:
  teaser: "/assets/post_img/22-02-13-09.png"
---
<br>

## 🔹 제일 작은 수 제거하기
```js
function solution(arr) {
    var answer = [];
    return answer;
}
```

## 🔹 문제 설명
정수를 저장한 배열, arr 에서 가장 작은 수를 제거한 배열을 리턴하는 함수, solution을 완성해주세요. 단, 리턴하려는 배열이 빈 배열인 경우엔 배열에 -1을 채워 리턴하세요. 예를들어 arr이 [4,3,2,1]인 경우는 [4,3,2]를 리턴 하고, [10]면 [-1]을 리턴 합니다.

## 🔹 제한 조건
- arr은 길이 1 이상인 배열입니다.
- 인덱스 i, j에 대해 i ≠ j이면 arr[i] ≠ arr[j] 입니다.

## 🔹 예시
<table class="table" style="width:200px">
        <thead><tr>
<th>arr</th>
<th>return</th>
</tr>
</thead>
        <tbody><tr>
<td>[4,3,2,1]</td>
<td>[4,3,2]</td>
</tr>
<tr>
<td>[10]</td>
<td>[-1]</td>
</tr>
</tbody>
      </table>

## 🔹 내가 푼 방법
```js
function solution(arr) {
    var minimum = [];
    for(let i=0; i<arr.length; i++){
        minimum.push(arr[i]);
    }
    minimum = minimum.sort((a,b) => a-b).sort((a,b)=> a-b)[0];
    var answer = arr.length-1 ? arr.filter((element) => element !== minimum) : [-1];
    return answer
}
```

## 🔹 방법 2
- `Math.min()` 사용하기
  - 주어진 숫자들 중 가장 작은 값을 반환합니다. 
- `indexOf()` 사용하기
- `splice()` 사용하기

```js
function solution(arr) {
    arr.splice(arr.indexOf(Math.min(...arr)), 1);
    var answer = arr.length ? arr : [-1]
    return answer;
}
```
