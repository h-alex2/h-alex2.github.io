---
title: "프로그래머스 코딩테스트(JavaScript) Lv.1 - 완주하지 못한 선수"
date: 2022-02-18 23:10:32+0900
category: coding-test
tags:
  - level1
  - coding-test
header:
  teaser: "/assets/post_img/22-02-18-06.png"
---
<br>

## 🔹 완주하지 못한 선수
```js
function solution(participant, completion) {
    var answer = completion.pop(participant.filter(it => completion.includes(it)))
    return answer;
}
```

## 🔹 문제 설명
수많은 마라톤 선수들이 마라톤에 참여하였습니다. 단 한 명의 선수를 제외하고는 모든 선수가 마라톤을 완주하였습니다.

마라톤에 참여한 선수들의 이름이 담긴 배열 participant와 완주한 선수들의 이름이 담긴 배열 completion이 주어질 때, 완주하지 못한 선수의 이름을 return 하도록 solution 함수를 작성해주세요.

## 🔹 제한 조건
- 마라톤 경기에 참여한 선수의 수는 1명 이상 100,000명 이하입니다.
- completion의 길이는 participant의 길이보다 1 작습니다.
- 참가자의 이름은 1개 이상 20개 이하의 알파벳 소문자로 이루어져 있습니다.
- 참가자 중에는 동명이인이 있을 수 있습니다.

## 🔹 예시
<table class="table" style="width:500px">
        <thead><tr>
<th>participant</th>
<th>completion</th>
<th>return</th>
</tr>
</thead>
        <tbody><tr>
<td>["leo", "kiki", "eden"]</td>
<td>["eden", "kiki"]</td>
<td>"leo"</td>
</tr>
<tr>
<td>["marina", "josipa", "nikola", "vinko", "filipa"]</td>
<td>["josipa", "filipa", "marina", "nikola"]</td>
<td>"vinko"</td>
</tr>
<tr>
<td>["mislav", "stanko", "mislav", "ana"]</td>
<td>["stanko", "ana", "mislav"]</td>
<td>"mislav"</td>
</tr>
</tbody>
      </table>

## 🔹 입출력 예 #1
"leo"는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

## 🔹 입출력 예 #2
"vinko"는 참여자 명단에는 있지만, 완주자 명단에는 없기 때문에 완주하지 못했습니다.

## 🔹 입출력 예 #3
"mislav"는 참여자 명단에는 두 명이 있지만, 완주자 명단에는 한 명밖에 없기 때문에 한명은 완주하지 못했습니다.


## 🔹 다른 분 방법
- 내가 쓴 코드는 for문이 두번이나 들어가서 효율성 테스트에 통과하지 못했다. 
- return 쓰면 for문 종료

```js
function solution(participant, completion) {
    participant = participant.sort();
    completion = completion.sort();
    
    for(let i=0; i<participant.length; i++){
        if(participant[i] !== completion[i]){
            return participant[i];
        }
    } 
}
```