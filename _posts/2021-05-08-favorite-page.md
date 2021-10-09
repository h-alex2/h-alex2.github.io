---
title: "자주 쓰는 것들 모음"
date: 2021-05-08
category: favoritepage
tags:
  - Github
  - Jekyll
  - ruby
  - bookmark
---


<br>


- 지킬 서버로 블로그 연결하기 
  bundle exec jekyll serve <br>
  <https://ogaeng.com/jekyll-blog-install/>



- Atom에서 toc 자동으로 만들기  
  command palette ctrl + shift + p 들어가서   
  "Markdown Toc Auto: Insert Toc"  


- html 이모지  
  <https://getemoji.com/>

- html color
  <https://htmlcolorcodes.com/>



## Markdown 문법


- 접기, 펼치기

``` html
<details>
  <summary>제목</summary>
  <div markdown="1">//내용 안에 markdown을 인식하기 위함
    내용 적기
</details>
```

---


<summary>스케쥴러</summary>
<details>
  <div markdown="1">
  </div>
  <head>
    <link rel="stylesheet" type="text/css" href="/assets/css/weeklyplan_table.css">
  </head>
  <body>


  <div>
    <table>
      <thead class="head">
        <td></td>
        <td></td>
        <td></td>
        <td>1st 2nd 3rd</td>
      </thead>
      <thead class="date">
      <!--SUN ~ THU-->
        <tr>
          <td>SUN</td>
          <td>MON</td>
          <td>TUE</td>
          <td>WED</td>
        </tr>
      </thead>
      <tbody id="todo-list">
        <tr class= "day">
          <td>03</td>
          <td>04</td>
          <td>05</td>
          <td>06</td>
        </tr>
        <tr class="text">
        <!--본문-->
          <td> <!--일요일-->
            <li></li>
          </td>
          <td> <!--월요일-->
            <li></li>
          </td>
          <td> <!--화요일-->
            <li></li>
          </td>
          <td> <!--수요일-->
            <li></li>
          </td>
        </tr>
      </tbody>
      <thead class="date2">
        <tr>
          <td>THU</td>
          <td>FRI</td>
          <td>SAT</td>
          <td>MEMO</td>
        </tr>
      </thead>
      <tbody id="todo-list">
        <tr class= "day">
          <td>07</td>
          <td>08</td>
          <td>09</td>
          <td>📝</td>
        </tr>
        <tr class="text">
        <!--본문-->
          <td> <!--목요일-->
            <li></li>
          </td>
          <td> <!--금요일-->
            <li></li>
          </td>
          <td> <!--토요일-->
            <li></li>
          </td>
          <td> <!--메모장-->
            <li></li>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
</details>