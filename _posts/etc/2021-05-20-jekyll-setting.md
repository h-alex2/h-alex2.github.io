---
title: "험난한 Jekyll 블로그 만들기"
date: 2021-05-20
category: github
tags:
  - Github
  - Jekyll
---

<br>


```
내 jekyll의 험난한 과정
1. 막무가내로 첫 블로그를 설치하고 눈누난나 잘 쓰고 있었는데 역시 실패했다.   
깃허브의 빌드 실패 폭탄 메일로 하루하루 10년 묵은 장아찌처럼 말라 비틀어져 가고있었다. 
2. 다시 시도하기 위해서 첫블로그를 삭제하고 계속 시도했는데 되질 않았다. 
jekyll serve를 키면 웹에서 켜지질 않고.. 이해가 가지 않는 에러들이 마구 떴다.
3. 결국엔 많이 쓰는 블로그 템플릿을 이용해서 최대한 많이 포스트를 보고 설명서를 익혀가면서 설치에 성공했다. 

되지 않았던 이유
1. 블로그 템플릿 readme를 제대로 읽지 않았음
2. jekyll 설명서를 제대로 읽지 않았음
3. 필요한 프로그램에 대한 이해도가 없었음 

jekyll 블로그 생성에 필요한 것
😭 설명서를 이해할만한 스킬을 가지고있거나 읽으려는 노력
😭 막무가내로 하지말고 절차를 밟으며 진행해야함
😭 인내심
```
<br>

---

<br>

### 설치에 도움된 사이트   
- <https://honbabzone.com/jekyll/start-gitHubBlog/>
- <https://velog.io/@zawook/Github-%EB%B8%94%EB%A1%9C%EA%B7%B8-%EB%A7%8C%EB%93%A4%EA%B8%B0-2>  
- <https://ansohxxn.github.io/>  
너무 큰 도움이 된 블로그들이다.. 그저 빛.. 🌞🌞


<div style="color: #002BFF;"> 필요한 것 </div>
- ruby , gem(루비설치시 함께 설치됨)
- git
- jekyll (이건 미리 설치안해도 된다. 밑 9번 차례에 설치하면 됨.)
- bundler (이건 미리 설치안해도 된다. 밑 9번 차례에 설치하면 됨.)


1. GITHUB Repositories 만들기 리파지토리 이름 : 자신의 아이디.github.io 이렇게.

2. 위에 준비물 다 설치하고 설치된 것 잘 설치됐는지 확인하기 위해서 
명령프롬프트나 터미널에 ruby -v, gem -v, git -v 눌려서 확인하기 (따로 따로 누르기)  
버전이 잘 안나온다면 설치가 제대로 되지않은 것. 다시 설치

3. 컴퓨터와 연동하기 위해서 내 컴퓨터에 블로그폴더 만들기

4. 명령프롬프트 폴더 위치로 바꿔놓기 D로 가고싶은데 기본이 c로 되어있다면 D: 입력 후 
cd D:\폴더위치쓰면 경로 바뀜

5. 내가 쓴 블로그 템플릿 : <https://github.com/mmistakes/minimal-mistakes>   
(이걸로 고른 이유 : minimal-mistakes는 쓰는 사람도 굉장히 많고 정보도 많은 것 같다. 라고 블로그에서 보았기 때문에) 
저 주소로 들어가서 code download -> 블로그 폴더에 파일,폴더들만 넣어놓기  
또는  
명령 프롬프트에 git clone https://github.com/mmistakes/minimal-mistakes.git . <- 점 붙이기(명령프롬프트 위치로 복사됨)

6. 옮긴 파일들에 Gemfile 있는지 확인하기 없으면 만들어줘야함. 저 템플릿에는 들어있음

7. 숨긴파일 보기에 체크 안되어 있으면 해놓고 숨긴 파일 중에 혹시 .git 이란 파일이 있는지 확인 있다면 삭제해주기

8. 명령프롬프트 - git init 입력

9. gem install jekyll bundler 입력 gem install jekyll하고 gem install bundler 이런식으로 따로 해줘도 된다 (bundle과 jekyll을 설치하는 것)

10. bundle install 입력

11. bundle exec jekyll serve 입력하면 server address가 나온다. 그곳으로 가면 jekyll 서버로 들어가지고 블로그 모습이 보이게 된다.  
혹시 안나온다면 윈도우의 경우 명령프롬프트 인코딩이 맞지 않아서 그럴수도 있으니 chcp 65001 명령어 입력하여 utf-8 인코딩으로 바꾸기  
또 server address는 떴지만 please add the following to your gemfile to avoid polling for changes: gem 'wdm', '>= 0.1.0' if Gem.win_platform 이런식으로 please라는게 뜨거나 한다면 명령프롬프트 gem install wdm 입력, 폴더 열어서 gemfile 메모장으로 열어서 밑에 gem 'wdm', '>= 0.1.0' 추가 -> Gemfile.lock파일 삭제하기 -> 명령프롬프트 bundle install 입력 
다시 bundle exec jekyll serve를 눌러서 그 줄이 안나오는지 확인 후 서버 주소로 들어가 잘 나오는지 확인한다. 

13. 이제 내 리포지토리와 연결해야한다.
git remote add origin (+) 내 repository주소 입력(저+는 입력하는거 x)

14. 잘 연결됐는지 확인하기위해 git remote -v 입력 잘 나오는지 확인하기

15. 이제 내 블로그 폴더에 있는 파일들을 웹 리포지토리에 넣어주는 작업을 할 차례다.
git add. 입력 (점을 꼭 붙여야한다. 전체 다 넣겠다는 말)
The file will have its original line endings 이런 에러가 떴는데 맥과 윈도우의 차이로 오는 에러라고 한다. 에러가 뜨면 git config --global core.autocrlf true 입력 (윈도우의 경우다)
다시 git add. 해주기

16. git commit -m "설명아무거나" 입력 (커밋에 들어갈 설명을 적는 것)

17. git push origin master 입력하면 내 리포지토리에 옮겨진 걸 확인할 수 있다.

18. 내 리포지토리-settings-pages에 가서 내 도메인이 publish됐는지 확인한 후 
내 블로그주소를 주소창에 입력해서 잘 나오는지 보기
난 나오지 않고 404page가 나와서 찾아봤는데 
명령프롬프트에 git commit --allow-empty -m "Trigger rebuild" 입력 -> git push origin master 해주면 된다. 

<br>

---

<br>


