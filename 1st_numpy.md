# 데이터 분석
## numpy
- jupyter, numpy 사용<br>

### scaler : 0차원 물리량
- N(자연수) Z(정수) Q(유리수) R(실수)

### vector : 1차원 물리량/scaler의 집합(묶음)
- 파이썬으로 따지면 list
- ex. 'a' in ['a', 'b', 'c']
- 변수가 1개

### matrix : 2차원 물리량/vector의 집합(묶음)
- 차원이 2개 -> 변수가 2개

### 대각행렬
- 스케일 변환
- 주대각선 성분을 제외한 모든 성분이 0인 정사각 행렬

### 정방행렬(square matrix)
> n개의 행과 n개의 열을 가지는 정사각형 행렬
- 주대각선
 
### 단위행렬
- 대각행렬이면서 대각선의 항들이 모두 1인 정방행렬 또는 단위행렬

### 영행렬
- 모든 원소가 0인 행렬

### 전치행렬 
- 대각선을 기준으로 위치가 바뀜

### 대칭행렬
- 정방행렬 n x n 행렬이 자신의 전치 행렬과 똑같을 때 대칭행렬이라고 한다.

### 직교행렬
- 선형 변환 중 회전 변환을 의미
- 어떤 행렬의 행 벡터와 열 벡터가 유클리드 공간의 정규 직교를 이루는 행렬을 의미한다.

### Numpy array vs Python list
- Numpy 는 배열을 생성하고 배열 내부의 숫자 데이터를 조작하는 빠르고 효율적인 방법을 광범위하게 제공
- Python 목록은 단일 목록 내에 다양한 데이터 유형 포함
- Numpy 배열의 모든 요소는 동질적

### numpy 명령어
>vector = np.array(lst)(                               )#-lst 파이썬을 이용한 벡터 데이터 vector는 객체<br>
>vector.shape                                           # -len<br>
>vector.dtype                                           # 타입에 대한 정보<br>
>.szie                                                  # 스칼라 전체 수<br>
>.ndim                                                  # 차원의 수<br>
>.shape                                                 # 차원의 모양(벡터 수, 스칼라 수)<br>
> np.vstack(list)                                       # 각 배열을 쌓음 버티컬 기준으로
> np.hstack                                             # 각 배열을 호리즌탈 기준으로 쌓음
>arr3_=arr3[:, np.newaxis].shape                        # 축을 새로 다시 만들어줘<br>
>np.expand_dims(arr4, axis=1)                           # arr4[:, np.newaxis]<br>
>np.expand_dims(arr4, axis=0)                           # arr4[ np.newaxis, :]<br>
>arr3.T # transposed 약자                               #전체 데이터의 수는 각 차원의 곱과 같다.<br>
arr3.reshape(2,-1) # reshape(2,-1) -> 벡터 차원의 크기는 2이고, 나머지는 알아서.<br>
arr3_f = arr3.astype(np.float64)                        #타입 변경.<br>
 
 ---

