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
이틀 동안.. 구글링 네이버.. 찾으며 한 숙제😂🤣😂🤣😂🤣😂🤣😂🤣


```javascript
'use strict';

// Q1. make a string out of an array 문자열 만들기
{
    const fruits = ['apple', 'banana', 'orange'];
    console.log("Q1");
    console.log(fruits.toString());

  }
  
  // Q2. make an array out of a string 배열 만들기
  {
    const fruits = '🍎, 🥝, 🍌, 🍒';
    const fruits3 = fruits.split(',')
    console.log("Q2");
    console.log(fruits3);
  }

  
  // Q3. make this array look like this: [5, 4, 3, 2, 1]
  {
    const array = [1, 2, 3, 4, 5];
    console.log("Q3");
    console.log(array.reverse());
  }
  
  // Q4. make new array without the first two elements 맨 앞에 두 개 빼고 새로운 배열 만들기
  {
    const array = [1, 2, 3, 4, 5];
    // array.shift();
    // array.shift();
    // console.log(array);
    const array2 = array.slice(2);
    console.log("Q4");
    console.log(array2);
  }
  


  class Student {
    constructor(name, age, enrolled, score) {
      this.name = name;
      this.age = age;
      this.enrolled = enrolled;
      this.score = score;
    }
  }
  //속성, 메소드 정의

  const students = [
    new Student('A', 29, true, 45),
    new Student('B', 28, false, 80),
    new Student('C', 30, true, 90),
    new Student('D', 40, false, 66),
    new Student('E', 18, true, 88),
  ];
  
  //객체, 인스턴스

  // Q5. find a student with the score 90 : 90점의 학생 찾기
  { const score90 = students
    .filter(Student => Student.score > 89)
    .map(Student => Student.name);
    console.log("Q5");
    console.log(score90);
  }

  // Q6. make an array of enrolled students
  { const enrolledtrue = students
    .filter(Student => Student.enrolled === true)
    .map(Student => Student.name);
    console.log("Q6");
    console.log(enrolledtrue);
  }
  
  // Q7. make an array containing only the students' scores
  // result should be: [45, 80, 90, 66, 88]
    const scorelist = students.map(Student => Student.score);
    console.log("Q7");
    console.log(scorelist);
  
  // Q8. check if there is a student with the score lower than 50
  { const lower50 = students
    .filter(Student => Student.score < 50)
    .map(Student => Student.name);
    console.log("Q8");
    console.log(lower50);
  }
  
  // Q9. compute students' average score
  {const scoresum = scorelist.reduce(function add(sum, currValue) { 
    return sum + currValue;
  }, 0);
  const average = scoresum / scorelist.length;
  console.log("Q9");
  console.log(average);}

  // Q10. make a string containing all the scores
  // result should be: '45, 80, 90, 66, 88'
    console.log("Q10");
    console.log(scorelist.toString());

  
  // Bonus! do Q10 sorted in ascending order
  // result should be: '45, 66, 80, 88, 90'
  { function compare ( a , b ) {   return a - b;   } 
    scorelist.sort( compare );
    const scorelist2 = scorelist.toString();
    console.log("Q11");
    console.log(scorelist2);
  }

```