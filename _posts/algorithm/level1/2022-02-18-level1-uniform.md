---
title: "프로그래머스 코딩테스트(JavaScript) Lv.1 - 체육복"
date: 2022-02-18 23:10:23+0900
category: coding-test
tags:
  - level1
  - coding-test
header:
  teaser: "/assets/post_img/22-02-18-04.png"
---
<br>

## 🔹 체육복
```js
function solution(n, lost, reserve) {
    var answer = 0;
    return answer;
}
```

## 🔹 문제 설명
점심시간에 도둑이 들어, 일부 학생이 체육복을 도난당했습니다. 다행히 여벌 체육복이 있는 학생이 이들에게 체육복을 빌려주려 합니다. 학생들의 번호는 체격 순으로 매겨져 있어, 바로 앞번호의 학생이나 바로 뒷번호의 학생에게만 체육복을 빌려줄 수 있습니다. 예를 들어, 4번 학생은 3번 학생이나 5번 학생에게만 체육복을 빌려줄 수 있습니다. 체육복이 없으면 수업을 들을 수 없기 때문에 체육복을 적절히 빌려 최대한 많은 학생이 체육수업을 들어야 합니다.

전체 학생의 수 n, 체육복을 도난당한 학생들의 번호가 담긴 배열 lost, 여벌의 체육복을 가져온 학생들의 번호가 담긴 배열 reserve가 매개변수로 주어질 때, 체육수업을 들을 수 있는 학생의 최댓값을 return 하도록 solution 함수를 작성해주세요.

## 🔹 제한 조건
- 전체 학생의 수는 2명 이상 30명 이하입니다.
- 체육복을 도난당한 학생의 수는 1명 이상 n명 이하이고 중복되는 번호는 없습니다.
- 여벌의 체육복을 가져온 학생의 수는 1명 이상 n명 이하이고 중복되는 번호는 없습니다.
- 여벌 체육복이 있는 학생만 다른 학생에게 체육복을 빌려줄 수 있습니다.
- 여벌 체육복을 가져온 학생이 체육복을 도난당했을 수 있습니다. 이때 이 학생은 체육복을 하나만 도난당했다고 가정하며, 남은 체육복이 하나이기에 다른 학생에게는 체육복을 빌려줄 수 없습니다.

## 🔹 예시
<table class="table" style="width:200px">
        <thead><tr>
<th>n</th>
<th>lost</th>
<th>reserve</th>
<th>return</th>
</tr>
</thead>
        <tbody><tr>
<td>5</td>
<td>[2, 4]</td>
<td>[1, 3, 5]</td>
<td>5</td>
</tr>
<tr>
<td>5</td>
<td>[2, 4]</td>
<td>[3]</td>
<td>4</td>
</tr>
<tr>
<td>3</td>
<td>[3]</td>
<td>[1]</td>
<td>2</td>
</tr>
</tbody>
      </table>

## 🔹 입출력 예 #1
1번 학생이 2번 학생에게 체육복을 빌려주고, 3번 학생이나 5번 학생이 4번 학생에게 체육복을 빌려주면 학생 5명이 체육수업을 들을 수 있습니다.

## 🔹 입출력 예 #2
3번 학생이 2번 학생이나 4번 학생에게 체육복을 빌려주면 학생 4명이 체육수업을 들을 수 있습니다.


## 🔹 다른 분 방법
- 인원 수 n 만큼 배열을 1로 채워주기
- 유니폼이 없으면 -1, 여벌 유니폼이 있으면 +1 


```js
function solution(n, lost, reserve) {
    let answer = 0;
    let hasUniform = new Array(n).fill(1);

    // 유니폼이 없는 학생은 -1 
    for (let i=0; i<lost.length; i++){
        hasUniform[lost[i]-1]--;
    }
    // 여벌 유니폼이 있는 학생은 +1 
    for (let i=0; i<reserve.length; i++){
        hasUniform[reserve[i]-1]++;
    }
    
    for (let i=0; i<hasUniform.length; i++ ){
        if(hasUniform[i] === 0){
            if(hasUniform[i-1] === 2){
                hasUniform[i]++;
                hasUniform[i-1]--;
            } else if(hasUniform[i+1] === 2){
                hasUniform[i]++;
                hasUniform[i+1]--;
            }
        }
    }
    for(let i=0; i<hasUniform.length; i++){
        if(hasUniform[i] >= 1) {
            answer++;
        } 
    }
    return answer;
}
```