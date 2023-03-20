---
title:  "Pandas Part 2. DataFrame"

categories:
  - Basic
tags:
  - [Pandas, DataFrame]

toc: true
toc_sticky: true
 
date: 2023-03-18
last_modified_at: 2023-03-18
---

# DataFrame
<hr>
``` py
gdp_dict = {
    'korea': 169320000,
    'japan': 516700000,
    'china': 1409250000,
    'usa': 2041280000,
}
gdp = pd.Series(gdp_dict)
country = pd.DataFrame({
    'population': population,
    'gdp': gdp
})
```

![image](https://user-images.githubusercontent.com/31909322/226269071-b51c49f0-fd52-49a6-8550-6c612f965f23.png)

<br>

## 딕셔너리로 변환할 수 있음
``` py
country.index
# Index(['china', 'japan', 'korea', 'usa'], dtype='object')

country.columns
# Index(['gdp', 'population'], dtype='object')

country['gdp']
type(country['gdp'])
# pandas.core.series.Series
```
<br>

## Series도 numpy array처럼 연산자를 활용
``` py
gdp_per_capita = country['gdp'] / country['population']
count['gdp per capita'] = gdp_per_capita
```
![image](https://user-images.githubusercontent.com/31909322/226270064-e1ecaa63-8d81-46ad-9536-90b4a57cc0de.png)
<br>

## 데이터 프레임을 저장
``` py
country.to_csv("./country.csv")
country.to_excel("country.xlsx")

country = pd.read_csv("./country.csv")
country = pd.read_excel("country.xlsx")
```
![image](https://user-images.githubusercontent.com/31909322/226271213-923a51f3-eca3-4f07-a64e-77199020f6b6.png)
<br>

# 💡 Indexing / Slicing
<hr>

## .loc: 명시적인 인덱스를 참조하는 인덱싱/ 슬라이싱
``` py
country.loc['china']

country.loc['japan':'korea', :'population']
```
![image](https://user-images.githubusercontent.com/31909322/226272655-2595767f-f8ee-46c0-a7f0-8a3e382853c4.png)
<br>

## .iloc: 파이썬 스타일 정수 인덱스 인덱싱/ 슬라이싱
``` py
country.iloc[0]

country.iloc[1:3, :2]
```
![image](https://user-images.githubusercontent.com/31909322/226272655-2595767f-f8ee-46c0-a7f0-8a3e382853c4.png)

<br>

## DataFrame 새 데이터 추가/ 수정
```py
dataframe = pd.DataFrame(columns=['이름', '나이', '주소'])
dataframe.loc[0] = ['임원군', '26', '서울']
dataframe.loc[1] = {"이름": '철수', '나이': '25', '주소': '인천'}

dataframe.loc[1, '이름'] = '영희'
```
![image](https://user-images.githubusercontent.com/31909322/226273605-50d506f2-9201-4201-be70-4785b5b972ac.png)

<br>

## DataFrame 새 컬럼 추가
``` py
dataframe['전화번호'] = np.nan
dataframe.loc[0, '전화번호'] = '01012341234'

len(dataframe)
```
![image](https://user-images.githubusercontent.com/31909322/226279427-5218180f-2545-4f1f-9bb4-75cb7b2eb217.png)
<br>

## 컬럼 선택하기
* 컬럼 이름이 하나만 있다면 Series
* 리스트로 들어가 있다면 DataFrame
``` py
dataframe["이름"]
dataframe[['이름', '주소', '나이']]
```
![image](https://user-images.githubusercontent.com/31909322/226280243-c5b30d8b-ad04-4c19-a364-1376cb77ad4c.png)
<br>

