---
title: "프로그래머스 코딩테스트(JavaScript) Lv.1 - 핸드폰 번호 가리기"
date: 2022-02-13 19:11:02+0900
category: coding-test
tags:
  - level1
  - coding-test
header:
  teaser: "/assets/post_img/22-02-13-05.png"
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
프로그래머스 모바일은 개인정보 보호를 위해 고지서를 보낼 때 고객들의 전화번호의 일부를 가립니다.
전화번호가 문자열 phone_number로 주어졌을 때, 전화번호의 뒷 4자리를 제외한 나머지 숫자를 전부 *으로 가린 문자열을 리턴하는 함수, solution을 완성해주세요.

## 🔹 제한 조건
- s는 길이 4 이상, 20이하인 문자열입니다.

## 🔹 예시

<table class="table" style="width: 300px">
        <thead><tr>
<th>phone_number</th>
<th>return</th>
</tr>
</thead>
        <tbody><tr>
<td>"01033334444"</td>
<td>"*******4444"</td>
</tr>
<tr>
<td>"027778888"</td>
<td>"*****8888"</td>
</tr>
</tbody>
      </table>

## 🔹 내가 푼 방법
```js
function solution(phone_number) {
    var answer = '';
    for(let i=0; i<phone_number.length-4; i++){
        answer = answer + "*"
    }
    for (k=answer.length; k<phone_number.length; k++){
        answer = answer + phone_number[k];
    }
    return answer;
}
```
- 푸는 내내 이것보다 더 좋은 방법이 있을 것 같은데 하면서 풀었다. 
- repeat 또 기억해!! 

## 🔹 방법 2
- `"*".repeat(반복할횟수)` repeat 사용하면 반복할 수 있다. 기억해!! 
- `slice` 사용 
  - `slice(4) `5번째 자리 수 부터 끝까지
  - `slice(0,4)` 1번째 자리부터 4번째 까지 
  - `slice(0,1)` 1번째 자리
  - `slice(-1)` 맨 마지막 자리

```js
function hide_numbers(s){
  var result = "*".repeat(s.length - 4) + s.slice(-4);
  //함수를 완성해주세요

  return result;
}
```

## 🔹 방법 3
- `Array` 사용 
- `fill` 사용
- `join` 사용
  - `join` : 배열의 모든 요소를 연결해 하나의 문자열로 만듦
  - `const elements = ['fire','air','water']`
  - `elements.join(); = fire,air,water`
  - `elements.join(''); = fireairwater`  

```js
function solution(phone_number) {
    var answer = Array(phone_number.length - 4).fill("*").join('');
    var number = phone_number.slice(-4);
    return answer+number
}
```


