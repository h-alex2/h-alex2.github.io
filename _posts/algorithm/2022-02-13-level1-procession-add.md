---
title: "프로그래머스 코딩테스트(JavaScript) Lv.1 - 행렬의 덧셈"
date: 2022-02-13 17:01:26+0900
category: coding-test
tags:
  - level1
  - coding-test
header:
  teaser: "/assets/post_img/22-02-13-04.png"
---
<br>

## 🔹 행렬의 덧셈
```js
function solution(arr1, arr2) {
    var answer = [[]];
    return answer;
}
```

## 🔹 문제 설명
행렬의 덧셈은 행과 열의 크기가 같은 두 행렬의 같은 행, 같은 열의 값을 서로 더한 결과가 됩니다. 2개의 행렬 arr1과 arr2를 입력받아, 행렬 덧셈의 결과를 반환하는 함수, solution을 완성해주세요.

## 🔹 제한 조건
- 행렬 arr1, arr2의 행과 열의 길이는 500을 넘지 않습니다.

## 🔹 예시

<table class="table" style="width : 400px;">
        <thead><tr>
<th>arr1</th>
<th>arr2</th>
<th>return</th>
</tr>
</thead>
        <tbody><tr>
<td>[[1,2],[2,3]]</td>
<td>[[3,4],[5,6]]</td>
<td>[[4,6],[7,9]]</td>
</tr>
<tr>
<td>[[1],[2]]</td>
<td>[[3],[4]]</td>
<td>[[4],[6]]</td>
</tr>
</tbody>
      </table>

## 🔹 방법 1 
- `map()이용하기` 

```js
function solution(arr1, arr2) {
    var answer = [[]];
    answer = arr1.map((a,i) => a.map((b,j) => b + arr2[i][j]));
    return answer;    
}
```
- arr1.map((a, i)) 로 arr1의 인덱스와 배열값을 가져오고 
- a.map으로 배열값 안의 값인 b와 인덱스 j를 가져온다. 


## 🔹 방법 2

```js
function solution(arr1, arr2) {
    var answer = [[]];
    for (var i=0; i<arr1.length; i++){
        answer[i] =[];
        for(var j=0; j<arr1[i].length; j++){
            answer[i].push(arr1[i][j] + arr2[i][j]);
        }
    }
    return answer;
}
```

## 혼잣말 
map을 좀 익혔다고 생각했는데 계속 새롭네.. ㅎㅎ   
이중배열일 때는 for문 두 번!! 기억해!! 