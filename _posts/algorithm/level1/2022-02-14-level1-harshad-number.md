---
title: "프로그래머스 코딩테스트(JavaScript) Lv.1 - 하샤드 수"
date: 2022-02-14 17:52:35+0900
category: coding-test
tags:
  - level1
  - coding-test
header:
  teaser: "/assets/post_img/22-02-13-06.png"
---
<br>

## 🔹 핸드폰 번호 가리기
```js
function solution(phone_number) {
    var answer = '';
    return answer;
}
```

## 🔹 문제 설명
양의 정수 x가 하샤드 수이려면 x의 자릿수의 합으로 x가 나누어져야 합니다. 예를 들어 18의 자릿수 합은 1+8=9이고, 18은 9로 나누어 떨어지므로 18은 하샤드 수입니다. 자연수 x를 입력받아 x가 하샤드 수인지 아닌지 검사하는 함수, solution을 완성해주세요.

## 🔹 제한 조건
- x는 1 이상, 10000 이하인 정수입니다.

## 🔹 예시

<table class="table" style="width:200px">
        <thead><tr>
<th>arr</th>
<th style="text-align: center">return</th>
</tr>
</thead>
        <tbody><tr>
<td>10</td>
<td style="text-align: center">true</td>
</tr>
<tr>
<td>12</td>
<td style="text-align: center">true</td>
</tr>
<tr>
<td>11</td>
<td style="text-align: center">false</td>
</tr>
<tr>
<td>13</td>
<td style="text-align: center">false</td>
</tr>
</tbody>
      </table>

## 🔹 내가 푼 방법
```js
function solution(x) {
    var stringX = String(x);
    var sum = 0;
    for(let i=0; i<stringX.length; i++ ){
        sum += Number(stringX[i]);
    }
    return x%sum===0 ? true : false;
}
```
- 이 문제는 좀 쉽게 푼 것 같다. 자릿수만 더하고 나머지만 구하면 되는거라.. 

## 🔹 방법 2
- `toString()` : String과 같은듯. 
  - `a.toString() = String(a)`
- `eval` 이 뭐지? 
  - 절대 사용하지 말 것..? 이라고? 
  - 문자열로부터 eval()을 실행하는 건 엄청나게 위험하다고 하네 해킹의 위험이 크다고..

- `x+""` = `"x"` 
- split("") 하면 `"12" -> "1","2"`
- `map(Number)` 하여 숫자로 바꿔주기

```js
function solution(x) {
    var a = 0;
    var s = (x+"").split("").map(Number);

    for(let i of s){
        a += i;
    }

    return x%a == 0 ? true : false;
}
```

## 🔹 방법 3
- reduce에서 왜 +a, +b 를 쓰는건지 궁금했는데 알아냈다. 문자열에 +를 붙이니까 숫자가 되는구나
- `(n+"").split("")` 으로 숫자를 "1","2" 이런식으로 분리해주고
- reduce를 이용해 1 + 2 각 자릿수를 더해준다.
- 더해준 값을 n에 나눈 나머지값이 0 or 1값이 나온다. 
- 0이면 true, 1이면 false 값이 나오기 때문에 `!`를 사용해 불린값을 뒤바꿔준다. 

```js
function Harshad(n){
  return !(n%(n+'').split('').reduce((a, b) => +a + +b);
}
```


