---
title: "Dream Coding-JavaScript 06강"
date: 2021-05-25
category: javascript
tags:
  - DreamCoding
toc: true
toc_sticky: true
toc_label: “6. 클래스와 오브젝트의 차이점(class vs object), 객체지향 언어 클래스 정리”
---

## Dream Coding-JavaScript 06강 - 6. 클래스와 오브젝트의 차이점(class vs object), 객체지향 언어 클래스 정리
<link rel="stylesheet" type="text/css" href="/assets/CSS/markdown.css">


<br>
{% include video id="_DLhUBWsRtw" provider="youtube" %}
<br>

<details>
<summary>객체지향언어란?</summary>
<div markdown="1">
<p id="d">
Object Oriented  
객체 지향  
<br><br>

컴퓨터 프로그래밍을 하기 위한 언어에는 많은 종류가 있다. 이러한 언어들은 크게 2가지로 나누어지는데, 객체 지향 언어와 절차 지향 언어이다. 객체 지향이란 실제 세계를 모델링하여 소프트웨어를 개발하는 방법으로서, 객체 지향 프로그래밍에서는 데이터와 절차를 하나의 덩어리로 묶어서 생각한다. 이는 마치 컴퓨터 부품을 하나씩 사다가 컴퓨터를 조립하는 것과 같은 방법이다.
<br><br>
객체(object)란 보고 만질 수 있는 것, 지성적으로 이해할 수 있는 것, 생각이나 행동이 추구하는 바를 말한다. 또는 문제영역에서 잘 정의된 역할을 갖고 있는 각각에 대해서 구별할 수 있는 품목(item), 단위(unit), 개체(entity)라 정의하기도 하며 단순히, 정의된 경계를 갖고 구별되는 어떤 것이라 말할 수도 있다.
<br><br>
다시 말해서 객체는 학생, 교실, 책 같은 생각할 수 있는 모든 사물이나 공부, 수학 같은 개념상으로 존재하는 것 등 모든 것이 될 수 있다. 좀 더 구체적으로, 문제영역에 속한 사물 중에 관리의 필요성이 있거나 중요한 개념이라면 더 좋은 객체가 될 수 있다. 시스템의 관점에서 본다면 어떤 상태(state)를 나타내는 데이터의 구조와 동작을 수행하는 연산(operation)으로 이루어진 프로그램의 한 요소이다. 여기서의 연산을 객체 지향에선 메소드(method)라고 한다. 이렇게 객체의 상태는 데이터에 의해 결정되고 동작은 메소드에 의해 결정된다.
<br><br>
객체 지향의 3대 특성으로는 (1) 캡슐화(encapsulation) : 관련 데이터와 알고리즘(코드)이 하나의 묶음으로 정리된 것으로서 개발자가 만들었으며, 관련된 코드와 데이터가 묶여있고 오류가 없어 사용이 편리하다. 데이터를 감추고 외부 세계와의 상호작용은 메소드(Method)를 통하는 방법인데, 라이브러리로 만들어 업그레이드하면 쉽게 바꿀 수 있다. ‘메소드’는 메시지에 따라 실행시킬 프로시저로서 객체 지향 언어에서 사용되는 것으로서, 객체 지향 언어에서는 메시지를 보내 메소드를 수행시킴으로써 통신(communication)을 수행한다.
<br><br>
(2) 상속(inheritance) : 상속은 이미 작성된 클래스를 이어 받아서 새로운 클래스를 생성하는 기법으로 기존 코드를 재활용해서 사용하는 것을 의미한다. 객체기술의 가장 핵심이 되는 개념으로 프로그램을 쉽게 확장할 수 있도록 해주는 강력한 수단이 된다. (3) 다형성(polymorphism) : 다형성이란 하나의 이름(방법)으로 많은 상황에 대처하는 기법이다. 개념적으로 동일한 작업을 하는 함수들에 똑같은 이름을 부여할 수 있으므로 코드가 간단해지는 효과가 있다.
[네이버 지식백과] Object Oriented - 객체 지향 (지형 공간정보체계 용어사전, 2016. 1. 3., 이강원, 손호웅)
</p>

</div>
</details>

class
- fields 데이터만 들어있는 경우 : 데이터 클래스
- methods

- template : 틀만 정의
- declare once : 한 번만 선언 
- no data in : class 자체에는 data가 없다.
- ES6에 소개됨
 
class에 data를 넣어서 만드는 것 : object

object 
- instance of class : class안에 instance
- created many times
- data in 

---

## JavaScript classes
- introduced in ES6
- syntactical sugar over prototype-based inheritance : 기본에 있던걸 바탕으로 문법이 추가된 것 

### 1. Class declarations : class 선언하기

```javascript
class Person {
    // constructor 생성자
    constructor(name, age) {
        // fields
        this.name = name;
        this.age = age;
    }

    //methods
    speak() {
        console.log(`${this.name}: hello!`);
    }
}
const ellie = new Person('ellie', 20);
//새로운 오브젝트를 만들 땐 new
console.log(ellie.name); //ellie
console.log(ellie.age);  //20
ellie.speak(); //ellie: hello!
```

### 2. Getter and setters
- 외부에서 데이터값을 바꾸는 것을 막기위해 쓴다. 객체의 무결성을 유지하기 위해
- getter : 값을 가져온다.
- setter : 값을 셋팅한다. 

```javascript
class User {firstName, lastName, age) {
    this.firstName = firstName;
    this.lastName = lastName;
    this.age = age;
}
    get age() {
        return this.age;
    } 

    set age(value) {
        this.age = value; // -> 이렇게 해주면 call stack이 뜬다. 왜냐면 set age(value)의 value가 age이므로 age(age) this.age = age; 로 되어 계속 호출을 반복하기 때문이다. 
    }
//-----------------------------
    get age() {
        return this._age;
    } 

    set age(value) {
        if (value < 0) {
            throw Error('age can not be negative'); // 1. 만약 나이가 마이너스 값이라면 경고를 주도록
        }
        this._age = value;  // age이름을 바꿔주어야 한다. _age로 바꾸었다. 
    //--------------------------    
    set age(value) {
        }
        this._age = value < 0 ? 0 : value;  // 2. value가 마이너스라면 지정된 value값을 쓰겠다. 
}


const user1 = new User('Steve', 'Job', -1); //나이 age가 마이너스로 잘못들어갔는데 위의 get, set로 인해
console.log(user1.age); //결과가 0으로 나오게 된다.
// 위 age는 _age로 바꿔줬지만 .age로 호출할 수 있다. 내부적으로 get과 set을 이용하기 때문
```

### 3. Fields (public, private)
    : 최근에 추가. 많이 쓰고 있지는.. 

```javascript
class Experiment { 
    publicField = 2;
    #privateField = 0; // # 해쉬를 붙이면 클래스 내부에서는 접근이 가능하지만 외부에서는 값을 읽을 수도 변경할 수도 없다. 
}
const experiment = new Experiment(); 
console.log(experiment.publicField); //2
console.log(experiment.pivateField); //undefined로 나옴 
```

### 4. Static properties and methods 

: 최근에 추가
: class안에 있는 fields와 methods는 새로운 오브젝트를 만들 때마다 그대로 복제되어서 값만 우리가 지정한 값으로 변경이 되어서 만들어진다.
    간혹 이런 오브젝트에 상관없이 class가 가지고 있는 고유한 값과 이런 데이터에 상관없이 동일하게 반복적으로 사용되어지는 method가 있을 수 있다. 
    그런 것들을 이런 static이라는 키워들을 이용해서 붙이면 object에 상관없이 class 자체에 연결되어 있다. 

```javascript
class Article {
    static publisher = 'Dream Coding';
    constructor (articleNumber) {
        this.articleNumber = articleNumber;
    }

    static printPublisher() {
        console.log(Article.publisher);
    }
}

const article1 = new Article(1);
const article2 = new Article(2);
console.log(article1.publisher);  
// undefined로 나옴 : 위에 static으로 할당했는데 왜 안나올까? 
// 이유 : static은 오브젝트마다 할당이 되는 것이 아니라 class 자체 즉 article이라는 class 자체에 붙어있기 때문이다. 
console.log(Article.publisher); // Dream coding : 클래스를 붙이니까 나오게됨. 
Article.printPublisher(); // Dream coding 출력됨

// 어떨 때 쓰면 좋을까? 
// : 오브젝트, 들어오는 데이터에 상관없이 공통적으로 class에 쓸 수 있는 거라면 static과 static method를 이용해서 작성하는 것이 메모리의 사용을 줄여줄 수 있다.
```

### 5. Inheritance 상속과 다양성

```javascript
class Shape {
    constructor (width, height, color) {
        this.width = width;
        this.height = height;
        this.color = color; 
    }

    draw() {
        console.log(`drawing $P{this.color} color of`);
    }

    getArea() {
        return width * this.height;
    }
}
 
class Rectangle extends Shape {}// rectangle이라는 class를 만들고 싶다면 "extends"라는 키워드를 이용해서 shape을 연장한다.
// 이렇게만 정의해도 shape에서 정의했던 width, height, color 세개의 fields와 method가 자동적으로 rectangle에 포함이 된다.  
const renctangle = new Rectangle(20, 20, 'blue');
rectangle.draw(); // drawing blue color of 호출됨

class Triangle extends Shape {}
const triangle = new Triangle(20, 20, 'red');
triangle.draw(); // drawing red color of 호출됨 
```
즉 같은 도형일 때 __extends__ 를 이용해서 도형에 각각 따로 일일이 작성하지 않아도 동일한 것들을 재사용할 수 있다.  


삼각형의 getArea면적의 경우 (width * height) / 2 즉 2를 나눠주어야 한다.
하지만 저기 위에 getArea에는 곱하는 것만 있다 이럴 때는


```javascript
class Triangle extends Shape {}  // 우리가 필요한 함수만 바로 재 정리해서 쓸 수 있다. : overwriting
    getArea() {
        return (width * this.height) / 2;
    } // 이 부분이 이 값을 추가해준다. 
    draw() {
        super.draw();
        console.log('삼각'); // 이렇게 추가하게 되면 위에서 정립한 drawing color of라는 건 안나오게 된다. 저 위에것도 함께 나오게하고 싶다면
                            // 저렇게 super.draw();를 적어주면 된다. : 부모의 메소드를 호출하는 것
    }
const triangle = new Triangle(20, 20, 'red');
```


### 6. Class checking: instanceOf

```javascript
console.log(rectangle instanceof Rectangle); // 왼쪽 rectangle 오브젝트가 오른쪽 Rectangle class의 instance인지 아닌지 즉 저 오브젝트가 저 클래스를 이용해서 만들어진 아이인지? 확인하는 것
console.log(triangle instanceof Rectangle);
console.log(rectangle instanceof Triangle);
console.log(rectangle instanceof Shape);
console.log(rectangle instanceof Object); //우리가 자바스크립트에서 만든 모든 오브젝트들은 오브젝트를 상속한 것 
```

MDN Javascript Reference 페이지  
<https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference>