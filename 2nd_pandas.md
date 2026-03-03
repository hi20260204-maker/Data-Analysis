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
