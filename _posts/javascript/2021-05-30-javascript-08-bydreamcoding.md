---
title: "Dream Coding-JavaScript 09강"
date: 2021-05-30
category: javascript
tags:
  - DreamCoding
toc: true
toc_sticky: true
toc_label: “9. 유용한 10가지 배열 함수들. Array APIs 총정리”
---
## Dream Coding-JavaScript 09강 - 9. 유용한 10가지 배열 함수들. Array APIs 총정리
<link rel="stylesheet" type="text/css" href="/assets/CSS/markdown.css">

<br>
{% include video id="3CUjtKJ7PJg" provider="youtube" %}
<br>

---
## Quiz
```javascript
// Q1. make a string out of an array 문자열 만들기
{
  const fruits = ['apple', 'banana', 'orange'];
}

// Q2. make an array out of a string 배열 만들기
{
  const fruits = '🍎, 🥝, 🍌, 🍒';
}

// Q3. make this array look like this: [5, 4, 3, 2, 1]
{
  const array = [1, 2, 3, 4, 5];
}

// Q4. make new array without the first two elements 맨 앞에 두 개 빼고 새로운 배열 만들기
{
  const array = [1, 2, 3, 4, 5];
}




class Student {
  constructor(name, age, enrolled, score) {
    this.name = name;
    this.age = age;
    this.enrolled = enrolled;
    this.score = score;
  }
}
const students = [
  new Student('A', 29, true, 45),
  new Student('B', 28, false, 80),
  new Student('C', 30, true, 90),
  new Student('D', 40, false, 66),
  new Student('E', 18, true, 88),
];

// Q5. find a student with the score 90
{
}

// Q6. make an array of enrolled students
{
}

// Q7. make an array containing only the students' scores
// result should be: [45, 80, 90, 66, 88]
{
}

// Q8. check if there is a student with the score lower than 50
{
}

// Q9. compute students' average score
{
}

// Q10. make a string containing all the scores
// result should be: '45, 80, 90, 66, 88'
{
}

// Bonus! do Q10 sorted in ascending order
// result should be: '45, 66, 80, 88, 90'
{
}
```