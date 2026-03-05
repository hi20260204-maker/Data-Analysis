# Iris 데이터셋 이용 ML 기초

```
import seaborn as sns # 그래프를 생성하게하는 모듈& 학습용 데이터 셋
from sklearn.datasets import load_iris
# scikit-learn에서 내장 데이터셋을 가져온다.
import numpy as np

iris = load_iris()
type(iris)
# 결과 sklearn.utils._bunch.Bunch

```
sklearn.utils._bunch.Bunch

```
iris.keys()
```
dict_keys(['data', 'target', 'frame', 'target_names', 'DESCR', 'feature_names', 'filename', 'data_module'])
```
X = iris['data']
print(type(X), X.shape)
```
<class 'numpy.ndarray'> (150, 4)

```
np.unique(X, return_counts=True)
# unique는 X에서 중복된 값들을 제거하고, 유일한 값들을 반환
# return_counts=True는 선택적인 매개변수로, 이를 사용하면 고유한 값들의 등장 횟수도 함께 반환
```
(array([0.1, 0.2, 0.3, 0.4, 0.5, 0.6, 1. , 1.1, 1.2, 1.3, 1.4, 1.5, 1.6,
        1.7, 1.8, 1.9, 2. , 2.1, 2.2, 2.3, 2.4, 2.5, 2.6, 2.7, 2.8, 2.9,
        3. , 3.1, 3.2, 3.3, 3.4, 3.5, 3.6, 3.7, 3.8, 3.9, 4. , 4.1, 4.2,
        4.3, 4.4, 4.5, 4.6, 4.7, 4.8, 4.9, 5. , 5.1, 5.2, 5.3, 5.4, 5.5,
        5.6, 5.7, 5.8, 5.9, 6. , 6.1, 6.2, 6.3, 6.4, 6.5, 6.6, 6.7, 6.8,
        6.9, 7. , 7.1, 7.2, 7.3, 7.4, 7.6, 7.7, 7.9]),
 array([ 5, 29,  7,  7,  1,  1,  8,  4,  7, 20, 21, 25, 11,  6, 12,  7,  7,
         6,  6, 12,  6, 11,  5,  9, 14, 10, 27, 11, 13,  8, 12,  8,  5,  4,
         7,  5,  6,  4,  5,  3,  8,  9,  7,  7,  9, 11, 14, 17,  6,  3,  8,
        10, 12, 11, 10,  5,  8,  9,  4, 10,  8,  5,  3, 10,  3,  5,  1,  1,
         3,  1,  1,  1,  4,  1]))

```
df = pd.DataFrame(iris['data'], columns=iris['feature_names'])
df
```

``` python
import numpy as np
import pandas as pd

import seaborn as sns
```

``` python
iris = sns.load_dataset("iris")
iris.shape
```

``` python
iris.shape[0] # 전체 데이터 수
```

``` python
iris.shape[1] == len(iris.columns) # 전체 컬럼 수
```

``` python
# sepal_length == 5.1 & 5.0
cond1 = iris['sepal_length'] == 5.1
cond2 = iris['sepal_length'] == 5.0

iris[cond1|cond2]

# 코드가 너무 길어짐 >> 변경 오직 or 조건일때만 isin을 사용 not and 조건
con3 = iris['sepal_length'].isin([5.1, 5.0])
iris[con3]
```

``` python
# species의 ㄱ밧이 setosa가 아닌 데이터 조회
con = iris['species'] != 'setosa' #파이썬을 이용한 방식
iris[con]
```

``` python
#다른 방식을 이용해서 pandas에서의 방식 => ~ 연산자(=not)사용
con = iris['species'] == 'setosa'
iris[~cond]
```

``` python
#pandas의 shape에서 첫번째(=0)차원은 index이기 때문에 슬라이싱을 하면 row가 추출됨
iris[:5] #.head()
```

``` python
iris[-5:] #.tail()
```

``` python
iris[:3] # row 데이터를 추출할 때는 슬라이싱
```

``` python
#iris[["petal_length","species"]] -> 컬럼추출
#[:3] -> row 추출
iris[["petal_length","species"]][:3]
```

``` python
#loc[row, column] ==> shape(row, column)
iris.loc[:3, ["petal_length","species"]]
```

