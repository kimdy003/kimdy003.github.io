---
title:  "Pandas Series"

categories:
  - Basic
tags:
  - [Pandas, Series]

toc: true
toc_sticky: true
 
date: 2023-03-17
last_modified_at: 2023-03-17
---

# Pandas
<hr>

* 구조화된 데이터를 효과적으로 처리하고 저장
* Array 계산에 특화된 Numpy를 기반으로 설계
<br>

# Series
<hr>
* numpy array가 보강된 형태
* Data와 Index를 가지고 있음


``` python
import pandas as pd

data = pd.Series([1,2,3,4])
data  

# 1,2,3,4
'''
0 1
1 2 
2 3
3 4
dtype: int64
'''
```
<br>

## 인덱스를 가지고 있고 인덱스로 접근 가능
```python
data = pd.Series([1, 2, 3, 4], index=['a', 'b', 'c', 'd'])
data['b']

# 2
'''
a 1
b 2
c 3
d 4
dtype: int64
'''
```
<br>

## name 인자로 이름을 지정할 수 있음
``` py
data = pd.Series([1, 2, 3, 4], index=['a', 'b', 'c', 'd'], name='Title')

'''
a 1
b 2
c 5
d 4
Name: Title, dtype: int64
'''
```

## Dictionary로 변환
``` py
population_dict = {
    'korea': 5180,
    'japan': 12718,
    'china': 141500,
    'usa': 32676
}
population = pd.Series(population_dict)

'''
china 141500
japna 12718
korea 5180
usa 32676
dtype: int64
'''
# key값 정렬도 되는 모양이다..
```
