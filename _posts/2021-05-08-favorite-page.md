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
      <thead class="day">
      <!--SUN ~ THU-->
        <tr style="text-align:right" >
          <td>SUN</td>
          <td class = "date">01</td>
          <td>MON</td>
          <td class = "date">02</td>
          <td>THU</td>
          <td class = "date">03</td>
          <td>WED</td>
          <td class = "date">04</td>
        </tr>
      </thead>
      <tbody id="todo-list">
        <tr class="text">
        <!--본문-->
          <td colspan = "2"> <!--일요일-->
            <li></li>
          </td>
          <td colspan = "2"> <!--월요일-->
            <li></li>
          </td>
          <td colspan = "2"> <!--화요일-->
            <li></li>
          </td>
          <td colspan = "2"> <!--수요일-->
            <li></li>
          </td>
        </tr>
      </tbody>
      <thead class="day">
        <tr style="text-align:right" >
          <td>THU</td>
          <td class = "date">05</td>
          <td>FRI</td>
          <td class = "date">06</td>
          <td>SAT</td>
          <td class = "date">07</td>
          <td></td>
          <td>MEMO</td>
        </tr>
      </thead>
      <tbody id="todo-list">
        <tr class="text">
        <!--본문-->
          <td colspan = "2"> <!--목요일-->
            <li></li>
          </td>
          <td colspan = "2"> <!--금요일-->
            <li></li>
          </td>
          <td colspan = "2"> <!--토요일-->
            <li></li>
          </td>
          <td colspan = "2"> <!--메모장-->
            <li></li>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
  <div>
    <table>
      <thead class="day">
      <!--SUN ~ THU-->
        <tr style="text-align:right" >
          <td>SUN</td>
          <td class = "date">01</td>
          <td>MON</td>
          <td class = "date">02</td>
          <td>THU</td>
          <td class = "date">03</td>
          <td>WED</td>
          <td class = "date">04</td>
        </tr>
      </thead>
      <tbody id="todo-list">
        <tr class="text">
        <!--본문-->
          <td colspan = "2"> <!--일요일-->
            <li></li>
          </td>
          <td colspan = "2"> <!--월요일-->
            <li></li>
          </td>
          <td colspan = "2"> <!--화요일-->
            <li></li>
          </td>
          <td colspan = "2"> <!--수요일-->
            <li></li>
          </td>
        </tr>
      </tbody>
      <thead class="day">
        <tr style="text-align:right" >
          <td>THU</td>
          <td class = "date">05</td>
          <td>FRI</td>
          <td class = "date">06</td>
          <td>SAT</td>
          <td class = "date">07</td>
          <td></td>
          <td>MEMO</td>
        </tr>
      </thead>
      <tbody id="todo-list">
        <tr class="text">
        <!--본문-->
          <td colspan = "2"> <!--목요일-->
            <li></li>
          </td>
          <td colspan = "2"> <!--금요일-->
            <li></li>
          </td>
          <td colspan = "2"> <!--토요일-->
            <li></li>
          </td>
          <td colspan = "2"> <!--메모장-->
            <li></li>
          </td>
        </tr>
      </tbody>
    </table>
  </div>
  </body>
</details>