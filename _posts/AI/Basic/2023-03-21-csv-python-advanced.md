---
title:  "CSV & 고급 파이썬"

categories:
  - Basic
tags:
  - [CSV, python]

toc: true
toc_sticky: true
 
date: 2023-03-21
last_modified_at: 2023-03-21
---

## CSV
* `name, age, address, gender`
* Comma Separated Value
* 각 열이 특정한 의미를 가짐

``` py
# moves.csv
# 국문 제목, 영문 제목, 개봉 연도
다크나이트, The Dark Knight, 2008
겨울왕궁, Frozen, 2013
슈렉, Shrek, 2001
슈퍼맨, Superman, 1978
```
<br>

``` py
# moves.csv
# 다른 구분 문자(delimiter)도 사용 가능
다크나이트| The Dark Knight| 2008
겨울왕궁| Frozen| 2013
슈렉| Shrek| 2001
슈퍼맨| Superman| 1978
```
![image](https://user-images.githubusercontent.com/31909322/226550334-09165b38-5287-4162-bc9e-a9cf8a9e411e.png){: width="60%" height="50%"}

<br>

### 데이터에 ','가 포함되어 있는 경우
``` py
# movies.csv
# 큰따옴표("")를 이용하여 데이터를 감싼다.
먹고 기도하고 사랑하라, "Eat, Pray, Love", 2010
"헬로우, 뉴욕", "Hello, New York", 2013
```
<br>

``` py
# 같은 데이터를 저장하는데 용량을 적게 소모함
# movies.csv
아이언맨,Iron Man,2008
겨울왕국,Frozen,2013

# movies.json
[{"ko": "아이언맨", "en": "Iron Man", "year": 2008},
{"ko": "겨울왕국", "en": "Frozen", "year": 2013}]
```
### CSV의 단점
``` py
# movies.csv
# 데이터 오염에 취약함
아이언맨, Iron, Man, 2008
겨울왕국, Frozen, 2013
```
![image](https://user-images.githubusercontent.com/31909322/226551034-8663a8a9-6058-456d-a03e-602c208de25c.png){: width="60%" height="50%"}

<br>

### CSV 사용법
``` py
import csv

with open('moves.csv') as file:
  reader = csv.reader(file, delimiter=',')

  for row in reader:
    print(row[0])
```

## 고급 파이썬 
### 함수를 리턴하는 함수
* 함수를 리턴값으로 갖는 경우도 있다
* 함수 내부에서 함수를 리턴하는 방법은, `lambda`를 사용할 수도 있고, 함수 내에서 `def`를 또 사용할 수 있다.
``` py
def adder(n):
  def helper(x):
    return x + n
  return helper

add_three = adder(3)
print(add_three(6))  # 9, 이 때 add_three는 함수 취급 helper의 return값을 가져온다
```
<br>

### map()
``` py
def get_eng_title(row):
  split = row.split(',')
  return split[1]

eng_titles = [get_eng_title(row) for row in movies]
eng_titles = map(get_eng_title, movies)
eng_titles = map(
  lambda row : row.split(',')[1],
  movies
)
```
<br>

### filter()
* filter()에 들어가는 함수는 boolean값을 가짐
``` py
def starts_with_r(word):
  return word.startswith('r')

words = ['real', 'man', 'rhythm', ...]
r_words = filter(starts_with_r, words)
```



<br>
<br>
<br>
<br>


