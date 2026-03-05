```python
import numpy as np
import pandas as pd 

#데이터 시각화
import seaborn as sns
import matplotlib.pyplot as plt

df = sns.load_dataset("anscombe")
```

```python
#info()
#-> 각 컬럼의 데이터 타입 / 각 컬럼의 결측치 데이터 수 / shape정보 => 전체 데이터의 수(각 차원간의 곱) / 메모리 사용량

df.info()
```

```python
df.head() #input 데이터가 default가 5라서 5개만 나옴
```

```python
df.head(10)#input 데이터가 10개 :: df = 인스턴스 / head = 메쏘드 
```

```python
df["dataset"].nunique() # 전체 데이터셋의 수 ==> 문자열에서만 사용
```

```python
df["dataset"].nunique() # 데이터셋의 이름 리스트 ==> 문자열에서만 사용
```

```python
cond1 = df["dataset"] =="I"
cond2 = df["dataset"] == "III"

cond = cond1|cond2 #둘다 보고싶어요

df[cond] #I데이터 셋만 추출 가능
```

```python
df[cond].shape
```

```python
#groupby를 이용하자 
#len(datasets) = df.nunique()
#dataset의 값을 기준으로 나눠짐
datasets = df.groupby(["dataset"])
df1 = datasets.get_group(("I",))
df2 = datasets.get_group(("II",))
df3 = datasets.get_group(("III",))
df4 = datasets.get_group(("IV",))

df1.shape, df2.shape, df3.shape, df4.shape
```

```python
re1 = df1[['x','y']].agg(["mean","std","var"]) #한번에 평균 표준편차 분산이 구해지는
re1
```

```python
# 그래프 그리기
# 도화지를 그리자
fig = plt.figure()

#그래프가 그려질 박스를 그리자
#그래프(x축, y축)가 그려질 박스를 그리자
#plot => 그래프야
axes1 = fig.add_subplot(2,2,1) # add_subplot(row위치, column수, 그래프의 위치)
axes2 = fig.add_subplot(2,2,2)
axes3 = fig.add_subplot(2,2,3)
axes4 = fig.add_subplot(2,2,4)
```

```python
axes1.plot(
    df1['x'], #X좌표의 데이터
    df1['y'], #Y좌표의 데이터,
    "o"       #그래프에 표시될 모양
)

axes2.plot(
    df2['x'], #X좌표의 데이터
    df2['y'], #Y좌표의 데이터,
    "o"       #그래프에 표시될 모양
)

axes3.plot(
    df3['x'], #X좌표의 데이터
    df3['y'], #Y좌표의 데이터,
    "o"       #그래프에 표시될 모양
)

axes4.plot(
    df4['x'], #X좌표의 데이터
    df4['y'], #Y좌표의 데이터,
    "o"       #그래프에 표시될 모양
)

fig
```


```python
fig = plt.figure() #도화지 만들자!
plt.plot(np.arange(2,8)) # 첫번째 그래프 추가
plt.plot(np.arange(4,7)) # 두번째 그래프 추가
plt.show()
```

```python
fig, ax = plt.subplots(2,2, figsize=(15,10))

ax[0,0].plot(np.arange(2,8))
ax[0,1].plot(np.arange(2,9))
ax[1,0].plot(np.arange(2,10))
ax[1,1].plot(np.arange(2,11))
```

```python
fig, ax = plt.subplots()

x = range(1,50)
y = np.log(x)

ax.plot(x,y)
ax.tick_params(
    axis='x',
    colors='red',
    labelrotation=45
)
ax.set_xticks(range(2,50,5))

plt.show()
```
