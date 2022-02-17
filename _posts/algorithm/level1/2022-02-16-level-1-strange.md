---
title: "프로그래머스 코딩테스트(JavaScript) Lv.1 - 이상한 문자 만들기"
date: 2022-02-16 01:25:17+0900
category: coding-test
tags:
  - level1
  - coding-test
header:
  teaser: "/assets/post_img/22-02-15-02.png"
---
<br>

## 🔹 이상한 문자 만들기
```js
function solution(s) {
    var answer = '';
    return answer;
}
```

## 🔹 문제 설명
문자열 s는 한 개 이상의 단어로 구성되어 있습니다. 각 단어는 하나 이상의 공백문자로 구분되어 있습니다. 각 단어의 짝수번째 알파벳은 대문자로, 홀수번째 알파벳은 소문자로 바꾼 문자열을 리턴하는 함수, solution을 완성하세요.

## 🔹 제한 조건
- 문자열 전체의 짝/홀수 인덱스가 아니라, 단어(공백을 기준)별로 짝/홀수 인덱스를 판단해야합니다.
- 첫 번째 글자는 0번째 인덱스로 보아 짝수번째 알파벳으로 처리해야 합니다.

## 🔹 예시
<table class="table" style="width:200px">
        <thead><tr>
<th>s</th>
<th>return</th>
</tr>
</thead>
        <tbody><tr>
<td>"try hello world"</td>
<td>"TrY HeLlO WoRlD"</td>
</tr>
</tbody>
      </table>

## 🔹 입출력 예 설명
"try hello world"는 세 단어 "try", "hello", "world"로 구성되어 있습니다. 각 단어의 짝수번째 문자를 대문자로, 홀수번째 문자를 소문자로 바꾸면 "TrY", "HeLlO", "WoRlD"입니다. 따라서 "TrY HeLlO WoRlD" 를 리턴합니다.



## 🔹 내가 푼 방법

```js
function solution(s) {
    var word = s.split("");
    for(let i=0; i<s.length; i++){
        i%2 ? word[i] = word[i].toLowerCase() : word[i] = word[i].toUpperCase();
    }
    for(let i=0; i<s.length; i++){
        if(word[i-1] ===" " && word[i] !== " "){
            console.log(i+"는?");
            var j = i;
            var k = [];
            while(j<s.length){
                k.push(j);
                if(k[0]%2===0){
                    j%2===0 ? word[j] = word[j].toUpperCase() :
                    word[j] = word[j].toLowerCase();
                } else{
                    j%2!==0 ? word[j] = word[j].toUpperCase() :
                    word[j] = word[j].toLowerCase();
                }
                j++;
            }
        }
        else {
            continue;
        }
    }
    word = word.join("");
    return word
}
```
- 너무 힘들었던 문제
- 처음에 쉽게 풀리길래 쉽네 했는데 조건을 잘못봤다.
- 너무 길게 푼 것 같다. 


## 🔹 방법 2
- 이런 천재같은 방법이 있다니
- `split(' ')` 으로 띄어쓰기를 기준으로 분리시킨 후
- `map`을 이용해서 단어별로 배열들을 만든다.(분리되어있는 알파벳)
- split으로 알파벳을 분리시킨 후 `map`의 key값을 이용해서 짝수번째 알파벳을 대문자로 바꿔주기

```js
function solution(s) {
    return 
    s.split(' ').map(i => i.split('').map((j, key) => key % 2 ===0 ? j.toUpperCase() : j.toLowerCase()).join('')).join(' ')
}
```

## 🔹 방법 3

- `charAt` : 특정 인덱스에 위치하는 문자열 유니코드를 반환합니다. 
- `s.charAt(i)`가 `" "`라면 num을 다시 0으로 해주고 다음 문자를 바꿀 수 있게끔 해주는 것
```js
function toWeirdCase(s){
  var result = "";
    var num = 0;

  console.log(s.length);

  for(var i = 0; i < s.length; i++){
   if(s.charAt(i) == " "){
    num = 0;
    result += " ";
    continue;
   }
    else if(num % 2 == 0){
      result += (s.charAt(i)).toUpperCase();
      num++;
    }
    else{
      result += (s.charAt(i)).toLowerCase();
      num++; 
    }
  }
```