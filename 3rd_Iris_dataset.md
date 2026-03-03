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
