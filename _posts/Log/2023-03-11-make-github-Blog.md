---
title:  "GitHub Blog 시작하기"
excerpt: "jekyll과 Minimal_Mistakes를 사용하여 GitHub Blog 만들기"

categories:
  - Log
tags:
  - [GitHub Blog, jekyll, Minimal_Mistakes]

toc: true
toc_sticky: true
 
date: 2023-03-11
last_modified_at: 2023-03-11
---



## Ruby 세팅
[Rudy for Windows](https://rubyinstaller.org/downloads/archives/)에서 Rudy + Devkit 2.6.5-1 을 다운 받는다.  
![image](https://user-images.githubusercontent.com/31909322/224531719-e1cb816a-b011-4ccb-aa4e-e19b687c6fad.png)

<div class="notice--primary" markdown="1">
여기서 Ruby + Devkit 2.6.5-1 버전으로 꼭 다운해야한다.  

제일 최신버전과 2.6.5 아래 버전하고는 충돌이 일어난다.

</div>

<br>

### Jekyll 세팅
``` 
gem install bundler jekyll
```
이와 같은 명령어를 통해 다운로드를 해준다.  
이 명령어를 사용할 때 `username.github.io` 위치의 cmd 창에서 다운하는 것을 권장한다.  
`ruby -v`와 `jekyll -v`를 통해 정상적으로 설치되었는지 확인!!

<br>

## Minimal-Mistakes 테마
* [Minimal-Mistakes](https://github.com/mmistakes/minimal-mistakes)  
위 링크에서 Minimal-Mistakes를 다운 받는다.

![image](https://user-images.githubusercontent.com/31909322/224532198-6491d779-ec26-4f35-af9f-d70104a8b5b6.png)  
<br>

여기서 빨간색 부분의 파일은 지워도 되는 파일  
<br>

## Github-Blog Repository 만들기
이 때 github.io앞에 들어가는 이름은 현재 github ID와 동일해야한다.  

![image](https://user-images.githubusercontent.com/31909322/224531418-d4a2de1c-18cb-4253-8468-febdaee6ae27.png)

<br>

### 생성한 Repository를 Local 환경으로 Clone 해 온다.
github Desktop을 사용하면 쉽게 가져올 수 있다.  
현재의 repo의 폴도에서 명령프롬프트(CMD)창을 연다.
```
bundle exec jekyll serve
```
이와 같은 코드를 입력하면, `.jekyll-cache` 폴더와 `Gemfile.lock` 파일이 생긴다.  
이 두 가지가 정상적으로 생겨야만, 로컬 서버에 연결할 수 있다.  

![image](https://user-images.githubusercontent.com/31909322/224532512-ee426cb5-d535-4aee-abe8-b92e1f23fb97.png)

Server running... press ctrl-c to stop.으로 된다면 정상적으로 열렸습니다.

[http://127.0.0.1:4000](http://127.0.0.1:4000) 으로 바로 확인해보세요.  
확인하시는 중에는 CMD창을 종료하시면 안됩니다!  
모든 Repo의 변동사항을 확인해서 Serve에서 바로 확인하실 수 있습니다.
<br>

