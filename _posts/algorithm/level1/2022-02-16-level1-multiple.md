---
title: "프로그래머스 코딩테스트(JavaScript) Lv.1 - 최대공약수와 최소공배수"
date: 2022-02-16 23:35:54+0900
category: coding-test
tags:
  - level1
  - coding-test
header:
  teaser: "/assets/post_img/22-02-16-02.png"
---
<br>

## 🔹 최대공약수와 최소공배수
```js
function solution(n, m) {
    var answer = [];
    return answer;
}
```

## 🔹 문제 설명
두 수를 입력받아 두 수의 최대공약수와 최소공배수를 반환하는 함수, solution을 완성해 보세요. 배열의 맨 앞에 최대공약수, 그다음 최소공배수를 넣어 반환하면 됩니다. 예를 들어 두 수 3, 12의 최대공약수는 3, 최소공배수는 12이므로 solution(3, 12)는 [3, 12]를 반환해야 합니다.

## 🔹 제한 조건
- 두 수는 1이상 1000000이하의 자연수입니다.

## 🔹 예시
<table class="table" style="width:200px">
        <thead><tr>
<th>n</th>
<th>m</th>
<th>return</th>
</tr>
</thead>
        <tbody><tr>
<td>3</td>
<td>12</td>
<td>[3, 12]</td>
</tr>
<tr>
<td>2</td>
<td>5</td>
<td>[1, 10]</td>
</tr>
</tbody>
      </table>

## 🔹 입출력 예 #1
위의 설명과 같습니다.

## 🔹 입출력 예 #2
자연수 2와 5의 최대공약수는 1, 최소공배수는 10이므로 [1, 10]을 리턴해야 합니다.

## 🔹 내가 푼 방법
- 최대공약수만 구하면 되는데 자꾸 테스트케이스 하나가 실패로 떠서 제일 힘들었던 문제. 
- 결국엔 끝까지 하지 못했다. 
- 최소공배수 공식 = n * m / 최대공약수 
- 최대공약수는 큰 값을 작은값으로 나누고 나머지가 0이면 작은 값이 최대공약수
- 나머지가 있다면 나머지로 계속 나눠주기 
- `n과 m의 최대공약수는 (n>m일 때) n을 m으로 나눈 나머지를 r이라 한다면 m과 r의 최대공약수와 같다. `

## 🔹 방법 1
```js
function solution(a, b) {
  let r
  var multiple = a*b;
  while (b != 0) {
    r = a % b
    a = b
    b = r
  }
  var m = multiple / a;
    return ([a, m])
}
```

