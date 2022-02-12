---
title: "React로 TO-DO 만들기"
date: 2022-02-05
category: toyproject
tags:
  - react
header:
  teaser: "/assets/post_img/22-02-05-01.JPG"
toc: true 
toc_sticky: true
---

> udemy The Complete 2022 Web Development Bootcamp 강의와
> [MDN-React](https://developer.mozilla.org/en-US/docs/Learn/Tools_and_testing/Client-side_JavaScript_frameworks/React_components) 에서 학습한 걸 바탕으로 만들어보았습니다


## 1. App.jsx - 기본틀 만들기
```
h1 - todo 타이틀
<form부분>
form - todo 입력 input과 버튼

<todo부분>
h2 - todo "몇 개 남았습니다"
div - 입력된 input이 기록되는 곳 
```

![code](/assets/post_img/22-02-05-02.png)
Form, Todo로 컴포넌트를 분리해준다. 


<br>

__index.js__ 의 const DATA 배열에 TODO를 담을 것이다.    
앞으로 넣을 TODO에도 name, id의 형태로 넣을 것이고 밑 DATA 배열안에 들어있는 것들은 저 값들을 App으로 가져가 화면에 표시할 수 있도록 밑작업을 하기 위한 연습값들. 
App 옆에 `tasks={DATA}` 추가

```js
import React from 'react';
import ReactDOM from 'react-dom';
import App from './App';
import './index.css'

const DATA = [
  {name: "cooking",
  id: "todo-1"},
  {name: "coding",
    id: "todo-2"}
]; 


ReactDOM.render(<App tasks={DATA} />,document.querySelector("#root"));
```
## 2. index.js의 DATA를 App.jsx에 가져오기   
컴포넌트 Todo.jsx의 input에 DATA 배열의 name이 들어가야한다.    
props로 값을 넣어주면 되지만 DATA 배열의 값이 하나가 아니기 때문에 `map()` 을 이용해서 반복문을 사용해야한다. 

![code](/assets/post_img/22-02-05-03.png)

## 3. Form - input값을 todo에 추가하기 

Form 컴포넌트에서 새로운 input값을 App으로 들고와야한다.   
1. Form.jsx에서 input 값을 저장하기 위해 useState를 만든다.
  - `const [name, setName] = useState("");`
2. onChange로 input의 값을 저장하고 onSubmit으로 클릭하면 값을 저장해서 App.jsx로 보내게된다.
3. App.jsx에서는 props.tasks를 useState로 설정하고 addTask함수를 이용해 Form의 name값을 받아 setTasks에 넣어준다. 

> nanoid : id의 값을 랜덤값으로 지정할 수 있는 플러그인 
`npm install --save nanoid` 로 설치한 후 `import { nanoid } from 'nanoid'`해서 불러온 후 nanoid() 로 사용할 수 있다.

![code](/assets/post_img/22-02-05-04.png)

## 4. delete 기능 추가하기 

Todo.jsx - delete button에 onClick을 추가하여 클릭한 todo의 id를 App.jsx로 보내기
```js
<Todo.jsx>
<button onClick={() => props.deleteTodo(props.id)}>delete</button>
```

App.jsx - deleteTodo로 클릭한 id를 받고 `filter()`를 이용해서 제거하기   
```js
  <App.jsx>
  function deleteTodo(id) {
    const deleteItem = tasks.filter(task => task.id !== id);
    setTasks(deleteItem);
  }
  const tasklist = tasks.map(task => (
  <Todo 
    name={task.name}
    id={task.id}
    key={task.id}
    deleteTodo={deleteTodo} //추가
    />
  ))
```

## 5. edit 기능 추가하기
edit기능을 추가하기 위해서는 두 개의 view가 필요하다.   
1. edit을 누르지 않은 기본 view
2. edit view 

![code](/assets/post_img/22-02-05-05.png)

## 6. 몇 개의 todo가 남았는지 표시하기

```js
app.js
  const taskss = `${tasks.length <= 1 ? "task" : "tasks"}`;
  const todoLength = tasks.length;
```
App.js return 위에 추가해주기

```js
<h2>{todoLength} {taskss}</h2>
```

## 6. GitHub pages로 빌드하기
1. package.json에 `"homepage": "http://<github아이디?.github.io/<repository 이름>"` 추가하기
2. `npm run build` 
3. 빌드된 build 폴더를 github에 업로드 해야한다. .gitignore 아래와 같이 수정 
```
# production
# /build
```
4. GitHub에 업로드하기
```
git commit -m 'Add build folder'
git push origin main
``` 
5. build 폴더만 gh-pages 브랜치에 업로드 
```
git subtree push --prefix build/ origin gh-pages
```

>[GitHub Pages에 배포](https://dev-yakuza.posstree.com/ko/react/github-pages/) 사이트를 참고하였습니다. 

### 힘들었던 점
처음 만들었던 todolist에서는 key값을 nanoid로 줬는데 todo가 추가될 때 마다 
key값이 계속 바껴서 전체 렌더링이 됐다. 아직도 왜 그런지 잘 모르겠다.   
이제 map, filter가 좀 적응된 것 같다. 아직 useRef는 많이 안써봐서 더 써보도록 해야겠다. 