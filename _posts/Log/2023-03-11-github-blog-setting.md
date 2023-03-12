---
title:  "GitHub Blog 세팅"
excerpt: "GitHub Blog 세팅"

categories:
  - Log
tags:
  - [GitHub Blog, jekyll, Minimal_Mistakes]

toc: true
toc_sticky: true
 
date: 2023-03-11
last_modified_at: 2023-03-11
---

## 기본 데이터 입력
* 수정 파일 : github.io 폴더 > _config.yml

``` yml
minimal_mistakes_skin    : "dark"  # 전체적인 블로그의 색감을 정하는 값입니다.
# "air", "aqua", "contrast", "dark", "dirt", "neon", "mint", "plum", "sunrise"

# Site Settings
locale                   : "ko-KR"   # 블로그의 주요 언어입니다. 한국어로 보려고 ko-KR로 설정했습니다.
title                    : "DY Blog 📂" # 사이트 탭에서 보이는 이름입니다.
title_separator          : "-"
subtitle                 : # site tagline that appears below site title in masthead
name                     : "do0_kim"  # 화면 하단 영역의 이름입니다.
description              : "공부 & 자료정리"
url                      : # "https://kimdy003.github.io"
baseurl                  : # the subpath of your site, e.g. "/blog"
repository               : "kimdy003/comments"
teaser                   : # path of fallback teaser image, e.g. "/assets/images/500x300.png"
logo                     : # path of logo image to display in the masthead, e.g. "/assets/images/88x88.png"
masthead_title           : "정리하는 개발자"  # 화면 title 입니다.
breadcrumbs              : true # true, false (default)  #블로그 path들이 표시되는 값입니다.
words_per_minute         : 200
```

## Site Author
``` yml
# Site Author
author:
  name             : "Do0_Kim"
  avatar           : # path of avatar image, e.g. "/assets/images/bio-photo.jpg"
  bio              : "<br>평생 공부 : Today I Learned 🌙"
  location         : "Republic of Korea"
  email            :
  links:
    - label: "Email"
      icon: "fas fa-fw fa-envelope-square"
      # url: "mailto:your.name@email.com"
    - label: "GitHub"
      icon: "fab fa-fw fa-github"
      url: "https://github.com/kimdy003"
    # - label: "Instagram"
    #   icon: "fab fa-fw fa-instagram"
    #   # url: "https://instagram.com/"
```