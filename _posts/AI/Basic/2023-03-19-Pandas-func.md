---
title:  "Pandas Part 3. 연산과 함수"

categories:
  - Basic
tags:
  - [Pandas, Series, DataFrame]

toc: true
toc_sticky: true
 
date: 2023-03-19
last_modified_at: 2023-03-19
---

## 누락된 데이터 체크
* 튜토리얼의 데이터와 다르게 현실 데이터는 일부 누락되어 있응 형태가 많음
``` py
dataframe.isnull()
dataframe.notnull()
```
![image](https://user-images.githubusercontent.com/31909322/226280711-0020d159-ad6d-444e-a158-9b48eed95508.png)

<br>
<br>

``` py
dataframe.dropna()
dataframe['전화번호'] = dataframe['전화번호'].fillna('전화번호 없음')
```
![image](https://user-images.githubusercontent.com/31909322/226281029-8a88b1e6-8595-4eb1-87f2-b2a3d48a2fec.png)
<br>

## Series 연산
* numpy array에서 사용했던 Series연산자들을 동일하게 활용할 수 있음
``` py
A = pd.Series([2, 4, 6], index=[0, 1, 2])
B = pd.Series([1, 3, 5], index=[1, 2, 3])
A + B
A.add(B, fill_value=0)  # B에 없는 A의 데이터는 0으로 처리해서 덧셈해라
```
![image](https://user-images.githubusercontent.com/31909322/226281519-cc66f456-a3f8-4cc4-bfaf-8b578eccaf03.png)
<br>

## DataFrame 연산
* add(+), sub(-), mul(*), div(/)
``` py
A = pd.DataFrame(np.random.randint(0, 10, (2, 2)), columns=list("AB"))
B = pd.DataFrame(np.random.randint(0, 10, (3, 3)), columns=list("BAC"))
A + B
A.add(B, fill_value=0)
```
![image](https://user-images.githubusercontent.com/31909322/226281912-7eaee0d3-5293-4290-82e3-b1bda41a97a1.png)
<br>

## 집계함수
* numpy array에서 사용했던 sum, mean 등의 집계함수를 동일하게 사용할 수 있음
``` py
data = {
  'A' : [i+5 for i in range(3)],
  'B' : [i**2 for i in range(3)]
}
df = pd.DataFrame(data)
df['A'].sum()  # 18
df.sum()
df.mean()
```
![image](https://user-images.githubusercontent.com/31909322/226282438-74b3f7e5-2f88-4094-97b3-287934b1dd7c.png)
<br>


## 값으로 정렬하기
`sort_values()`
```py
df= pd.DataFrame({
  'col1': [2, 1, 9, 8, 7, 4],
  'col2': ['A', 'A', 'B', np.nan, 'D', 'C'],
  'col3': [0, 1, 9, 4, 2, 3],
})
```
![image](https://user-images.githubusercontent.com/31909322/226282795-41bcd196-0217-42d3-9366-93efc9193451.png)

<br>

``` py
df.sort_valuee('col1')
```
![image](https://user-images.githubusercontent.com/31909322/226282906-3c8937e8-cf9f-4c98-ad5f-379c5c73f4f0.png)

<br>

```py
df.sort_values('col1', ascending=False)
```
![image](https://user-images.githubusercontent.com/31909322/226283027-ec77647c-855e-4056-a932-9e74283197ca.png)

<br>

```py
df.sort_values(['col2', 'col1'])
```
![image](https://user-images.githubusercontent.com/31909322/226283079-0d1b5d53-bcae-410b-976f-db2848301d84.png)

<br>