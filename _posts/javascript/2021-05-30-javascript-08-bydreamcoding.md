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
  console.log(fruits.toString()); //apple,banana,orange


  }

// Ellie's 답
{
  const fruits = ['apple', 'banana', 'orange'];
  const result = fruits.join(); //() 가로 안에 뭘 넣던지 저 배열 사이에 들어가는 문자가 된다. 
  console.log(result);
}

  
  // Q2. make an array out of a string 배열 만들기
  {
    const fruits = '🍎, 🥝, 🍌, 🍒';
    const fruits3 = fruits.split(',') //["🍎", " 🥝", " 🍌", " 🍒"]
    //const fruits3 = fruits.split(',', 2); ["🍎", " 🥝"] limit을 정해줄 수 있다.  
    //split은 꼭 ',' 구분자를 전달해 주어야 한다.
    console.log("Q2");
    console.log(fruits3);
  }

  
  // Q3. make this array look like this: [5, 4, 3, 2, 1]
  {
    const array = [1, 2, 3, 4, 5];
    console.log("Q3");
    console.log(array.reverse()); //[5, 4, 3, 2, 1]
    console.log(array); //를 확인해보면 array 배열 자체도 순서가 바뀜 

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
  // Ellie's 답
  {
    const array = [1, 2, 3, 4, 5];
    const result = array.splice(0, 2);
    console.log(result);
    (console.log(array);)
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

  // Ellie's 답
  {
    const result = students.find(function(student, index) {
      console.log(student, index);

    })
    // find : 첫번째 찾은 것을 리턴한다. 
  }
```find<S extends T>(predicate: (this: void, value: T, index: number, obj: T[]) => value is S, thisArg?: any): S | undefined;
find(predicate: (value: T, index: number, obj: T[]) => unknown, thisArg?: any): T | undefined;```
  Returns the value of the first element in the array where predicate is true, and undefined
  otherwise.
  `predicate` find calls predicate once for each element of the array, in ascending
  order, until it finds one where predicate returns true. If such an element is found, find
  immediately returns that element value. Otherwise, find returns undefined.
  `thisArg` If provided, it will be used as the this value for each invocation of
  predicate. If it is not provided, undefined is used instead.
  




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