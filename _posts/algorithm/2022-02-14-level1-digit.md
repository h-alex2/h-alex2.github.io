---
title: "프로그래머스 코딩테스트(JavaScript) Lv.1 - 자릿수 더하기"
date: 2022-02-14 19:26:21+0900
category: coding-test
tags:
  - level1
  - coding-test
header:
  teaser: "/assets/post_img/22-02-13-07.png"
---
<br>

## 🔹 짝수와 홀수
```js
function solution(n)
{
    var answer = 0;

    // [실행] 버튼을 누르면 출력 값을 볼 수 있습니다.
    console.log('Hello Javascript')

    return answer;
}
```

## 🔹 문제 설명
자연수 N이 주어지면, N의 각 자릿수의 합을 구해서 return 하는 solution 함수를 만들어 주세요.
예를들어 N = 123이면 1 + 2 + 3 = 6을 return 하면 됩니다.

## 🔹 제한 조건
- N의 범위 : 100,000,000 이하의 자연수

## 🔹 예시

<table class="table">
        <thead><tr>
<th>N</th>
<th>answer</th>
</tr>
</thead>
        <tbody><tr>
<td>123</td>
<td>6</td>
</tr>
<tr>
<td>987</td>
<td>24</td>
</tr>
</tbody>
      </table>

## 🔹 입출력 예 #1
문제의 예시와 같습니다.

## 🔹 입출력 예 #2
9 + 8 + 7 = 24이므로 24를 return 하면 됩니다.


## 🔹 내가 푼 방법
```js
function solution(n) {   
    var nn = (n+"").split("")
    var answer = 0;
    for (let i=0; i<nn.length; i++){
        answer = answer + Number(nn[i]);
    }
    return answer;
}
```
- 처음엔 `var answer = (n+"").split("").reduce((a,b) => +a + +b)`로 풀었으나 코드 실행에서 마지막 테스트에서 실패했다. 
  - reduece((a, b) => +a + +b, 0) 으로 하니 통과됐다.
  
## 🔹 방법 2
- `parseInt()` : 문자열 인자를 parsing 하여 특정 진수의 정수를 반환함
- 구문 : parseInt(string), parseInt(string, radix)
- radix : string의 진수를 나타내는 2부터 36까지의 정수 
  - 기본 값이 10이 아님. 주의 
  - <https://developer.mozilla.org/ko/docs/Web/JavaScript/Reference/Global_Objects/parseInt#%EC%84%A4%EB%AA%85>



