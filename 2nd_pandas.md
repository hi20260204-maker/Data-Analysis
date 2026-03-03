## 데이터
- 1차원의 데이터를 벡터
- 2차원의 데이터를 메트릭스<br>

```
import pandas as pd
import numpy as np
```

### 벡터
- 파이썬에서는 리스트(== 1차원의 데이터)<br>


```
lst = [1, 2, 3, 4, 5] # 파이썬에서 사용하는 벡터
# 넘파이에서 사용하는 벡터
arr =np.array(lst)
arr.size #numpy의 배열의 크기
arr.dtype   #numpy의 배열의 데이터 타입
```
- pandas에서 벡터는 Series로 표현함

```
arr1 = pd.Series(data = lst, index=['a1', 'a2', 'a3', 'a4', 'a5']) 
# 인덱스를 지정해 줄 수는 있지만 필수 X 
# 또한 제약 조건으로 인덱스의 길이와 데이터의 길이가 같아야 함
arr1
```
a1    1<br>
a2    2<br>
a3    3<br>
a4    4<br>
a5    5<br>
dtype: int64<br>


```
s1 = pd.Series(data=np.random.randn(5))
s1
```
0    0.082141<br>
1    0.416158<br>
2   -0.611223<br>
3    0.032467<br>
4   -0.359791<br>
dtype: float64<br>


```
dic = {
    'a1': 1,
    'a2': 2,
    'a3': 3,
    'a4': 4,
    'a5': 5
} # 키를 이용해서 데이터를 식별
dic.values()
dic.keys()
```
dict_values([1, 2, 3, 4, 5])<br>
dict_keys(['a1', 'a2', 'a3', 'a4', 'a5'])

```
s2 = pd.Series(data = dic) #dic을 이용한 series 생성
```
a1    1<br>
a2    2<br>
a3    3<br>
a4    4<br>
a5    5<br>
dtype: int64<br>

```
np.array(lst, dtype=np.int64).dtype
s3 = pd.Series(data = dic, dtype=np.int64, name="test") #name은 컬럼 정보
```
dtype('int64')<br>
a1    1<br>
a2    2<br>
a3    3<br>
a4    4<br>
a5    5<br>
Name: test, dtype: int64

```
arr #numpy array
arr[0] # 인덱싱이 가능
arr[1:2] # 슬라이싱 가능
```
array([1, 2, 3, 4, 5])<br>
np.int64(1)<br>
array([2])<br>


```
s1 #pandas series
s1[0] # 판다스 인덱싱 가능
s1[1:3] # 판다스 슬라이싱 가능
```
0    0.082141<br>
1    0.416158<br>
2   -0.611223<br>
3    0.032467<br>
4   -0.359791<br>
dtype: float64<br>
np.float64(0.08214138301507987)<br>
1    0.416158<br>
2   -0.611223<br>
dtype: float64<br>

```
s4 = pd.Series(
    np.random.randn(5) # 정규분포를 기준으로 랜덤하게 실수 추출
)
s4.shape, s4.size, s4.dtype

```
((5,), 5, dtype('float64'))
- numpy&pandas에는 평균, 중위값, 최대, 최소 등 다양한 통계함수들이 두현되어 있음
- 하지만 파이썬에는 없음 그래서 numpy&pandas를 사용해서 데이터 분석을 진행함

```
# 평균값 이상의 값만 출력되었으면!
# 1. 평균 구하기
s1.mean()
# 2. 평균보다 큰 데이터 조회
s1[s1>s1.mean()]
```
0    0.082141<br>
1    0.416158<br>
3    0.032467<br>
dtype: float64<br>


```
s1[[1,3]] # 데이터 조회
```
1    0.416158<br>
3    0.032467<br>
dtype: float64<br>

```
s1[[1,3]] = [2,4] # index(1,3)의 데이터를 2,4로 변경
```
0    0.082141<br>
1    2.000000<br>
2   -0.611223<br>
3    4.000000<br>
4   -0.359791<br>
dtype: float64<br>
```
s1 + s4 #벡터 간의 값은 같은 자리수에서만 가능
```
0    0.038587<br>
1    3.619074<br>
2   -1.624621<br>
3    4.080476<br>
4   -0.213831<br>
dtype: float64<br>
```
type(s1) # 타입 조회
```
pandas.Series
```
s1.to_numpy # 판다스 시리즈를 넘파이로
```
<bound method IndexOpsMixin.to_numpy of 0    0.082141<br>
1    2.000000<br>
2   -0.611223<br>
3    4.000000<br>
4   -0.359791<br>
dtype: float64>

```
list(s1.to_numpy()) # 넘파이를 리스트로
```
[np.float64(0.08214138301507987),<br>
 np.float64(2.0),<br>
 np.float64(-0.6112234785902574),<br>
 np.float64(4.0),<br>
 np.float64(-0.35979135869196494)]<br>
- 벡터 1차원 데이터, 스칼라의 집합
- 메트릭스 2차원 데이터이고, 벡터의 집합

```
# 판다스에서 벡터는 Series => Series는 스칼라의 집합
one = pd.Series([1,2,3])
two = pd.Series([1,2,3,4,5])
#판다스에서 메트릭스는 DataFrame -> DatraFrame는 Series의 집합
df = pd.DataFrame(data={
    'one':one, 'two':two
})
df # two의 값이 one보다 적게 있어서 df를 만들때 부족한 값을 NaN으로 일단은 넣어둠(비워둠)
```


| | one| two|
| --- | --- | --- |
| 0 | 1.0 | 1 |
| 1 | 2.0 | 2 |
| 2 | 3.0 | 3 |
| 3 | NaN | 4 |
| 4 | NaN | 5 |

```
df.index # 파이썬 range(시작(포함), 끝(비포함), 간격)-> range(0,5) ==> 0,1,2,3,4
'one' in df.columns
```
RangeIndex(start=0, stop=5, step=1)<br>
True

```
data = [
    {'a':1, 'b':2},{'a':5, 'b':10, 'c':10}
] # 슬라이싱은 불가

pd.DataFrame(data=data)
```


| | a| b|c|
| --- | --- | --- |---|
| 0 | 1 | 2 | NaN|
| 1 | 5 | 10 | 10.0|

```
df.to_dict() # datagrame -> python dict
df.to_json()
df['one'] # pd.Series
```
{'one': {0: 1.0, 1: 2.0, 2: 3.0, 3: nan, 4: nan},<br>
 'two': {0: 1, 1: 2, 2: 3, 3: 4, 4: 5}}<br>
'{"one":{"0":1.0,"1":2.0,"2":3.0,"3":null,"4":null},"two":{"0":1,"1":2,"2":3,"3":4,"4":5}}'<br>
0    1.0<br>
1    2.0<br>
2    3.0<br>
3    NaN<br>
4    NaN<br>
Name: one, dtype: float64<br>

```
df["three"] = df["one"]+df["two"]
df
```


| | one| two|three|
| --- | --- | --- |---|
| 0 | 1.0 | 1 | 2.0|
| 1 | 2.0 | 2 |4.0|
| 2 | 3.0 | 3 |6.0|
| 3 | NaN | 4 |NaN |
| 4 | NaN | 5 |NaN |
