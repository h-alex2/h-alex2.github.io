---
title: "프로그래머스 코딩테스트(JavaScript) Lv.1 - 콜라츠 추측"
date: 2022-02-15 01:40:51+0900
category: coding-test
tags:
  - level1
  - coding-test
header:
  teaser: "/assets/post_img/22-02-13-10.png"
---
<br>

## 🔹 콜라츠 추측
```js
function solution(num) {
    var answer = 0;
    return answer;
}
```

## 🔹 문제 설명
1937년 Collatz란 사람에 의해 제기된 이 추측은, 주어진 수가 1이 될때까지 다음 작업을 반복하면, 모든 수를 1로 만들 수 있다는 추측입니다. 작업은 다음과 같습니다.   
<br>
<1-1> 입력된 수가 짝수라면 2로 나눕니다.    
<1-2> 입력된 수가 홀수라면 3을 곱하고 1을 더합니다.   
<2> 결과로 나온 수에 같은 작업을 1이 될 때까지 반복합니다. 



<br>
예를 들어, 입력된 수가 6이라면 6→3→10→5→16→8→4→2→1 이 되어 총 8번 만에 1이 됩니다. 위 작업을 몇 번이나 반복해야하는지 반환하는 함수, solution을 완성해 주세요. 단, 작업을 500번을 반복해도 1이 되지 않는다면 –1을 반환해 주세요.

## 🔹 제한 조건
- 입력된 수, num은 1 이상 8000000 미만인 정수입니다.

## 🔹 예시
<table class="table" style="width:200px">
        <thead><tr>
<th>n</th>
<th>result</th>
</tr>
</thead>
        <tbody><tr>
<td>6</td>
<td>8</td>
</tr>
<tr>
<td>16</td>
<td>4</td>
</tr>
<tr>
<td>626331</td>
<td>-1</td>
</tr>
</tbody>
      </table>


## 🔹 예시 설명 
입출력 예 #1   
문제의 설명과 같습니다.   
<br>
입출력 예 #2   
16 -> 8 -> 4 -> 2 -> 1 이되어 총 4번만에 1이 됩니다.   
<br>

입출력 예 #3   
626331은 500번을 시도해도 1이 되지 못하므로 -1을 리턴해야합니다.    


## 🔹 내가 푼 방법
```js
function solution(num) {
    var number = num; 
    var repeat = 0; 
    while(repeat < 500){
        if(number === 1){
            break;
        }else{
            if(number%2===0){
                number /= 2;
                repeat += 1;
            } else {
                number = number * 3 + 1;
                repeat += 1;
            }
        }
    }
    return repeat===500 ? -1 : repeat;
}
```

## 🔹 방법 2

```js
function solution(num) {
    var count = 0;

    while (count < 500) {
        if (num === 1) {
            return count;
        }
        count ++;
        num = num % 2 === 0 ? num /2 : num *3 +1;
    }

    return -1;
}
```
## 🔹 방법 3

```js
function collatz(num,count = 0) {
    return num == 1 ? (count >= 500 ? -1 : count) : collatz(num % 2 == 0 ? num / 2 : num * 3 + 1,++count);
}
```