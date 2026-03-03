``` python
#특정 데이터를 join하거나 grouping하여 조회하는 것 해보자

import numpy as np
import pandas as pd

import seaborn as sns
```

``` python
df = sns.load_dataset('titanic')
df.shape #(전체 데이터의 수, 전체 변수의 수)
```

``` python
df.info()
```

``` python
df.head() #상위 5개의 데이터를 프린트
```

``` python
#is로 시작하는 함수명은 대부분 True/False값으로 리턴...True는 결측치
df.isnull()
```

``` python
df['deck'].isnull().sum() #결측치의 수치와 같음 true는 1이니까

#df['deck'].isnull() -> 벡터
#벡터.sum() -> 스칼라
#통계함수를 쓰면 차원이 하나 축소하는 것
```

``` python
df.isnull().sum() 
#df.isnull().sum()는 메트릭스임
#메트릭스.sum() -> 벡터
```

``` python
df.isnull().sum().sum()
#전체 결측치의 합
```

``` python
df.shape[0], len(df)
#전체 데이터를 구하기
#둘다 같음
```

``` python
arr = (df.isnull().sum() / len(df))*100
#전체 데이터중 결측치가 차지하는 비중
arr
```

``` python
type(arr)
```

``` python
arr.mean(), arr.max()
```

``` python
arr.sort_values(ascending=False) #내림차순 정렬
```

``` python
#0보다 큰 경우만 출력
arr = (df.isnull().sum()/len(df))*100
arr[arr>0].sort_values(ascending=False)
```

``` python
df.info()
```

``` python
#숫자만 분리
df_number = df.select_dtypes(include=np.number) #정수 &실수를 select

df_number.shape
```

``` python
df_number.head()
```

``` python
df_number.mean()
```

``` python
df_number.median()
```

``` python
df_number['fare'].median(), df_number['fare'].mean()
```

``` python
df_number.max()
```

``` python
#지금까지 column축의 평균만 보고 있었음
#row의 평균도 구할 수 있음

df_number.max(axis=1)
```

``` python
df_number.max() - (df_number.std() + df_number.min())
#각 컬럼별 최대값 - (각 컬럼별 표준편차 + 각 컬럼별 최소값)
```

``` python
df_number.describe()
```

``` python
df_object = df.select_dtypes(exclude = np.number) #정수 & 실수 뺀 나머지(문자열)
df_object.shape
```

``` python
df_object.mode() #최빈값
```

``` python
df_object['class'].unique() #유니크한 데이터 리스트
```

``` python
df_object['deck'].nunique() #결측치를 제외한 유니크 데이터 수
```

``` python
df_object['deck'].unique() #결측치가 포함된
```

``` python
df_object.describe()
```

``` python
```

-   map()`<br>`{=html}
    -   벡터 데이터를 조작하는 함수

``` python
s1 = pd.Series({
    'one': 1, 'two':2, 'three':3
})

s2 = pd.Series({
    1: 'triangle', 2:'square', 3:'circle'
})

s3 = pd.Series({
    4: 'triangle', 5:'square', 6:'circle'
})
```

``` python
s1.map(s2) #s1의 키로 s2의 value데이터와 연결됨 -> s1 value값과 s2의 키값이 같아야함
```

``` python
s1.map(s3)
```

``` python
df = sns.load_dataset('titanic')
```

``` python
df['alive'].head()
```

``` python
replace_alive = {
    'no':0, 'yes':1
}

df['new_alive']=df['alive'].map(replace_alive)

df[['new_alive','alive']].head()
```

``` python
df['new1_alive'] = df['alive'].map(lambda value:1 if value=='yes' else 0)

df
```

``` python
def change_alive(value):
    result = 0

    if value=='yes':
        result = 1

    return result


df['new2_alive'] = df['alive'].map(change_alive) 
df[['new2_alive', 'new1_alive', 'new_alive', 'alive']].head()
```

-   map() : map은 벡터일때만 사용가능`<br>`{=html}
-   apply() : 벡터 또는 메트릳그 둘다 사용가능

``` python
df = sns.load_dataset("titanic")
df.shape

df_number = df[['survived', 'pclass', 'age','sibsp','parch','fare']]
df_number.shape
```

``` python
df_number.apply(lambda x:x*2, axis=1)
```

``` python
#생종률은 가족의 숫자에 영향을 끼친다..? 가족을 살리기위해 본인의 희생을 한건가?
def get_family_number(row):
    return row['sibsp']+row['parch'] #family

df_number['family_number'] = df_number.apply(lambda row: get_family_number(row), axis=1)

df_number[['family_number', 'sibsp', 'parch']].tail()
```

``` python
```


``` python
df = sns.load_dataset('titanic')
df.shape
```

``` python
select_cols = [
    'age', 'sex', 'pclass', 'fare', 'survived'
]

df = df[select_cols]
df.shape
```

``` python
df.head()
# select_cols에 있는 survived 콜럼과 나머지 콜럼들이 얼마나 관여가 되어있는가
# groupby -> mysql에서 배웠어요
# sex를 이용해서 그룹을 나누자!!

df['sex'].nunique() # 몇개의 그룹으로 나눠질지?
```

``` python
groupeds = df.groupby(['sex'])
```

``` python
type(groupeds)
```

``` python
for group in groupeds:
    print(type(group), len(group))
```

``` python
for key,df_by_key in groupeds:
    print(f": {key}")
    if key[0]=='male':
        print(df_by_key)
#key = "male","female"
```

``` python
# 남자/여자 데이터들에 대한 평균값
groupeds.mean()
```

``` python
#여기서 남자 데이터만 뽑고 싶음
df_male = groupeds.get_group(('male',))

df_male
```
