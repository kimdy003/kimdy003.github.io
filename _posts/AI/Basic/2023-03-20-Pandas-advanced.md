---
title:  "Pandas 심화"

categories:
  - Basic
tags:
  - [Pandas, Series, DataFrame]

toc: true
toc_sticky: true
 
date: 2023-03-20
last_modified_at: 2023-03-20
---

## 조건으로 검색하기
### masking 연산
``` py
import numpy as np
import pandas as pd

df = pd.DataFrame(np.random.rand(5, 2), columns=['A', 'B'])
df['A'] < 0.5
```
![image](https://user-images.githubusercontent.com/31909322/226284580-2daae030-ff26-483b-994b-72394e654fbe.png)

<br>

### 조건에 맞는 DataFrame row 추출
``` py
import numpy as np
import pandas as pd

df = pd.DataFrame(np.random.rand(5, 2), columns=['A', 'B'])
df[(df['A'] < 0.5) & (df['B'] > 0.3)]
# or
df.query('A < 0.5 and B > 0.3')
```
![image](https://user-images.githubusercontent.com/31909322/226285053-1381fb8f-3425-44db-a4c4-a027add114cf.png)

<br>

### 조건으로 검색하기
``` py
df['Animal'].str.comtains('Cat')
df.Animal.str.math('Cat')
```
![image](https://user-images.githubusercontent.com/31909322/226328995-e6e00eef-c43e-43c4-96f7-3578547f15c3.png)

<br>

## 함수로 데이터 처리하기
### apply를 통해서 함수로 데이터를 다룰 수 있다.
``` py
df = pd.DataFrame(np.arange(5), columns=['Num'])
def square(x):
    return x ** 2
df['Num'].apply(square)
df['Square'] = df.Num.apply(lambda x : x ** 2)
```
![image](https://user-images.githubusercontent.com/31909322/226329381-3f643335-e028-4548-944b-7551afdb1a10.png)

<br>

``` py
df = pd.DataFrame(columns=['phone'])
df.loc[0] = "010-1234-1235"
df.loc[1] = "공일공-일이삼사-1235"
df.loc[2] = "010.1234.일이삼오"
df.loc[3] = "공1공-1234.1이3오"
df["preprocess_phone"] = ''
```
![image](https://user-images.githubusercontent.com/31909322/226329628-cb2c61b9-9561-415a-bde9-bbe274433e60.png)

<br>

``` py
def get_preprocess_phone(phone):
    mapping_dict= {
      "공": "0", "일": "1", "이": "2", "삼": "3",
      "사": "4", "오": "5",
      "-": "", ".": "",
    }
    for key, value in mapping_dict.items():
      phone = phone.replace(key, value)
    return phone

df["preprocess_phone"] = df["phone"].apply(get_preprocess_phone)
```
![image](https://user-images.githubusercontent.com/31909322/226330143-3a3f6d62-2a76-451f-a4cb-8f40b59344c3.png)

<br>

### replace: apply 기능에서 데이터 값만 대체 하고 싶을 때
``` py
df.Sex.replace({"Male": 0, "Female": 1})
df.Sex.repalce({"Male": 0, "Female": 1}, inplace=True)
```
![image](https://user-images.githubusercontent.com/31909322/226330434-8279cffa-4d7f-4310-80a1-6c15e30478f2.png)

<br>

## 그룹으로 묶기
### 간단한 집계를 넘어서서 조건부로 집계하고 싶은 경우
``` py
df = pd.DateFrame({
    "key":['A', 'B', 'C', 'A', 'B', 'C'], 
    'data1': [1, 2, 3, 1, 2, 3], 
    'data2': np.random.randint(0, 6, 6)
  })
df.groupby('key')
# <pandas.core.groupby. ~~~~ >
df.groupby('key').sum()
df.groupby(['key', 'data1']).sum()
```

![image](https://user-images.githubusercontent.com/31909322/226331010-2fb098ef-8962-4d5c-899e-b1877963ce1a.png)

<br>

### aggregate : groupby를 통해서 집계를 한번에 계산하는 방법
``` py
df.groupby('key').aggregate(['min', np.median, max])
df.groupby('key').aggregate({'data1': 'min', 'data2': np.sum})
```
![image](https://user-images.githubusercontent.com/31909322/226331332-baa20e4b-b4e4-428f-9206-1f8017c8e6e9.png)

<br>

### filter : groupby를 통해서 그룹 속성을 기준으로 데이터 필터링
``` py
def filter_by_mean(x):
  return x['data2'].mean() > 3
df.groupby("key").mean()
df.groupby("key").filter(filter_by_mean)
```
![image](https://user-images.githubusercontent.com/31909322/226331684-15da3c4b-0cc2-41a7-b69f-0ab892c6e471.png)

<br>

### apply: groupby를 통해서 묶인 데이터에 함수 적용
``` py
df.groupby('key').apply(lambda x: x.max() - x.min())
```
![image](https://user-images.githubusercontent.com/31909322/226331844-d2f35af4-4cd2-475f-8a8f-0a2839341a69.png)

<br>

### get_group: groupby로 묶인 데이터에서 key값으로 데이터를 가져올 수 있다.
``` py
df = pd.read_csv("./univ.csv")
df.head()
df.groupby("시도").get_group("충남")
ln(df.groupby("시도").get_group("충남"))
# 94
```
![image](https://user-images.githubusercontent.com/31909322/226332222-2d5f2296-f186-4db9-b3e2-7e9a4a59fcee.png)

<br>

## MultiIndex & pivot_table
### MultiIndex: 인덱스를 계층적으로 만들 수 있다.
``` py
df = pd.DataFrame(
    np.random.randn(4, 2),
    index=[['A', 'A', 'B', 'B'], [1, 2, 1, 2]],
    columns=['data1', 'data2']
)
```
![image](https://user-images.githubusercontent.com/31909322/226332619-9a858aa7-0f6e-4b30-aa85-ed3a28a6c7b9.png)

<br>

### 열 인덱스도 계층적으로 만들 수 있다.
``` py
df = pd.DataFrame(
  np.random.randn(4, 4)
  columns=[['A', 'A', 'B', 'B'], ['1', '2', '1', '2']]
)
```
![image](https://user-images.githubusercontent.com/31909322/226332886-6bfa96c8-97d9-4e2f-a0c8-afdea1ee060a.png)

<br>

### 다중 인덱스 컬럼의 경우 인덱싱은 계층적으로 한다.
* 인덱스 탐색의 경우에는 loc, iloc를 사용가능하다
``` py
df['A']
df['A']['1']
```
![image](https://user-images.githubusercontent.com/31909322/226333096-0d45a3e7-5af7-4185-9ded-3cf5fe78eff9.png)

<br>

## pivot_table
* 데이터에서 필요한 자료만 뽑아서 새롭게 요약
* 분석 할 수 있는 기능 엑셀에서의 피봇 테이블과 같다.
* Index : 행 인덱스로 들어갈 key
* Column: 열 인덱스로 라벨링될 값
* Value : 분석할 데이터
![image](https://user-images.githubusercontent.com/31909322/226333423-e8141bbd-9cfa-4bce-b05b-76711d185e6b.png)

<br>

``` py
# aggfunc의 Default는 np.mean
df.pivot_table(
  index='sex', columns='class', values='survived', aggfunc=np.mean
)
```
![image](https://user-images.githubusercontent.com/31909322/226333728-38c007e0-de17-4122-a608-4b0b90c9fc6a.png)

<br>

``` py
df.pivot_table(
  index='월별', columns='내역', values=['수입', '지출']
)
```
![image](https://user-images.githubusercontent.com/31909322/226333991-0158c025-953f-4bf5-a6ae-9cc666c89fd2.png)

<br>