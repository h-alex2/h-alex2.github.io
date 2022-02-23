---
title: "프로그래머스 코딩테스트(JavaScript) Lv.1 - 두 개 뽑아서 더하기"
date: 2022-02-18 23:10:17+0900
category: coding-test
tags:
  - level1
  - coding-test
header:
  teaser: "/assets/post_img/22-02-18-01.png"
---
<br>

## 🔹 두 개 뽑아서 더하기
```js
function solution(numbers) {
    var answer = [];
    return answer;
}
```

## 🔹 문제 설명
정수 배열 numbers가 주어집니다. numbers에서 서로 다른 인덱스에 있는 두 개의 수를 뽑아 더해서 만들 수 있는 모든 수를 배열에 오름차순으로 담아 return 하도록 solution 함수를 완성해주세요.

## 🔹 제한 조건
- numbers의 길이는 2 이상 100 이하입니다.
  - numbers의 모든 수는 0 이상 100 이하입니다.

## 🔹 예시
<table class="table" style="width:200px">
        <thead><tr>
<th>numbers</th>
<th>result</th>
</tr>
</thead>
        <tbody><tr>
<td><code>[2,1,3,4,1]</code></td>
<td><code>[2,3,4,5,6,7]</code></td>
</tr>
<tr>
<td><code>[5,0,2,7]</code></td>
<td><code>[2,5,7,9,12]</code></td>
</tr>
</tbody>
      </table>

## 🔹 입출력 예 #1
- 2 = 1 + 1 입니다. (1이 numbers에 두 개 있습니다.)
- 3 = 2 + 1 입니다.
- 4 = 1 + 3 입니다.
- 5 = 1 + 4 = 2 + 3 입니다.
- 6 = 2 + 4 입니다.
- 7 = 3 + 4 입니다.
- 따라서 [2,3,4,5,6,7] 을 return 해야 합니다.

## 🔹 입출력 예 #2

- 2 = 0 + 2 입니다.
- 5 = 5 + 0 입니다.
- 7 = 0 + 7 = 5 + 2 입니다.
- 9 = 2 + 7 입니다.
- 12 = 5 + 7 입니다.
- 따라서 [2,5,7,9,12] 를 return 해야 합니다.

## 🔹 내가 푼 방법
- `set` 이 뭘까
  - ES6에서 등장한 중복을 제거한 값들의 집합
  - 자료형에 관계 없이 원시 값과 객체 참조 모두 유일한 값을 저장할 수 있다. 
  - 즉 어떤 값은 그 Set 콜렉션 내에서 유일하다. 

```js
function solution(numbers) {
    var answer = [];
    for(let i=0; i<numbers.length; i++){
        for(let j=numbers.length-1; j>0; j--){
            if(i!==j){
                // console.log("i:"+numbers[i] + " j:"+numbers[j])
                answer.push(numbers[i] + numbers[j]);
            }
        }
    } 
    answer = [...new Set(answer.sort((a,b) => a-b))];
    return answer
}
```