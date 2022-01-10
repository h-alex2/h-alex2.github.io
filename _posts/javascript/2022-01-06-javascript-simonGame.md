---
title: "Simon Game 만들기"
date: 2022-01-10
category: javascript
tags:
  - jQuery
---
<br>
<div markdown="1">

1. jQuery, javascript 추가
2. 패턴 추가하기
  - js에 nextSequence() 새 함수 만들기 
  - nextSequence() - 0~3 사이 난수 생성 변수 만들기 randomNumber
  - buttonColours 배열을 만들고 "red", "blue", "green", "yellow" 값 넣기
  - nextSequence()- randomChosenColour 배열을 만들고 randomNumber을 사용해서 buttonColours배열에서 임의의 색상을 추가하기 
  - 상단에 gamePattern 빈 배열 만들기
 <br><br>

3. 애니메이션 추가하기
  - animate() 함수를 추가 jQuery로 nextSequence()의 randomChosenColour 값 id 찾아서 .pressed 클래스 추가하기 addclass
  - 100ms초 뒤에 추가한 클래스 삭제 removeclass 
  ```javascript 
  function animate(ChosenColour) {
  $("#" + ChosenColour).addClass("pressed");
  setTimeout(function() {
    $("#" + ChosenColour).removeClass("pressed");
  }, 100);
  }
  ```
  - nextSequence()에 animate(randomChosenColour) 추가 
  <br><br>
4. 사운드 추가하기
  - audio() 추가
  ```javascript 
  function audio(ChosenColour) {
  var audio = new Audio("sounds/" + ChosenColour + ".mp3");
  audio.play();
  }
  ```
  - nextSequence()에 audio(randomChosenColour) 추가 
  <br><br>
5. 클릭 이벤트 넣기
  - this 사용해서 클릭한 id값 가져오기
  ```javascript 
  $(".btn").click(function() {
  const userChosenColour = this.id;
  animate(pickColour);
  sound(pickColour);
  })
  ```
  - userClickedPattern 빈 배열 만들기
  - userClickedPattern에 userChosenColour 값 담기
  <br><br>
6. 키보드 버튼 하나 누르면 게임 시작하기
  - Press A Key to Start -> Level 표시하기
  - 변수 level = 0 추가하기
  - 변수 started = false 추가하기 : 버튼 한번만 인식하게
  ```javascript
  $(document).keydown(function() {
  if (!started) {
    $("#level-title").text("Level" + level);
    nextSequence();
    started = true;
  }
  });
  ```
<br>

7. 클릭한 값과 랜덤값 비교하기
  - checkAnswer 함수만들기  
  ```javascript
    function checkAnswer(currentLevel) {
        if (gamePattern[currentLevel] === userClickedPattern[currentLevel]) {
          console.log("success");
          if (userClickedPattern.length === gamePattern.length){
            setTimeout(function () {
              nextSequence();
            }, 1000);
          }
        } else {
          sound("wrong");
          $("#level-title").text("Game Over, Press Any Key to Restart");

          $("body").addClass("game-over");
          setTimeout(function() {
            $("body").removeClass("game-over");
          }, 100);
        }
      }
  ```


---
## CODE




```html
<body>
  <h1 id="level-title">Press A Key to Start</h1>
  <div class="container">
    <div lass="row">

      <div type="button" id="green" class="btn green">
      </div>
      <div type="button" id="red" class="btn red">
      </div>
    </div>

    <div class="row">
      <div type="button" id="yellow" class="btn yellow">
      </div>
      <div type="button" id="blue" class="btn blue">
      </div>
    </div>
  </div>

  <script src="https://ajax.googleapis.com/ajax/libs/jquery/3.3.1/jquery.min.js"></script>
  <script src="index.js" charset="utf-8"></script>
```

```css
body {
  text-align: center;
  background-color: #011F3F;
}

#level-title {
  font-family: 'Press Start 2P', cursive;
  font-size: 3rem;
  margin:  5%;
  color: #FEF2BF;
}

.container {
  display: block;
  width: 50%;
  margin: auto;

}

.btn {
  margin: 25px;
  display: inline-block;
  height: 200px;
  width: 200px;
  border: 10px solid black;
  border-radius: 20%;
}

.game-over {
  background-color: red;
  opacity: 0.8;
}

.red {
  background-color: red;
}

.green {
  background-color: green;
}

.blue {
  background-color: blue;
}

.yellow {
  background-color: yellow;
}

.pressed {
  box-shadow: 0 0 20px white;
  background-color: white;
}
```


```javascript
let gamePattern = [];
let userClickedPattern = [];
const buttonColours = ["red", "blue", "green", "yellow"];

let started = false;
let level = 0;



$(document).keydown(function() {
  if (!started) {
    $("#level-title").text("Level " + level);
    nextSequence();
    started = true;
  }
})

function checkAnswer(currentLevel) {

    if (gamePattern[currentLevel] === userClickedPattern[currentLevel]) {

      console.log("success");

      if (userClickedPattern.length === gamePattern.length){
        setTimeout(function () {
          nextSequence();
        }, 1000);
      }

    } else {
      sound("wrong");
      $("#level-title").text("Game Over, Press Any Key to Restart");

      $("body").addClass("game-over");
      setTimeout(function() {
        $("body").removeClass("game-over");
      }, 100);
      level = 0;
      started = false;
      gamePattern = [];

    }

}

$(".btn").click(function() {
  const userChosenColour = this.id;
  userClickedPattern.push(userChosenColour);
  animate(userChosenColour);
  sound(userChosenColour);
  checkAnswer(userClickedPattern.length - 1);
})


function nextSequence() {
  userClickedPattern = [];
  level++;
  $("#level-title").text("Level " + level);

  const randomNumber = Math.floor(Math.random()*4);
  const randomChosenColour = buttonColours[randomNumber];
  gamePattern.push(randomChosenColour);
  animate(randomChosenColour);
  sound(randomChosenColour);
}


function animate(ChosenColour) {
  $("#" + ChosenColour).addClass("pressed");
  setTimeout(function() {
    $("#" + ChosenColour).removeClass("pressed");
  }, 100);
}

function sound(ChosenColour) {
  var sound = new Audio("sounds/" + ChosenColour + ".mp3");
  sound.play();
}
```