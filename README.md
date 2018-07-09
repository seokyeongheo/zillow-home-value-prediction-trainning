# Datascience School 8th section B. Team Project. 

- 주제 : [Kaggle : Zillow's Home Value Prediction(Zestimate)](https://www.kaggle.com/c/zillow-prize-1)
- 기간 : 2018.06.15 - 2018.07.07
- 구성원 : 백승흔, 전찬민, 정혜란, 허석영


# _TIME LINE_

## OT _ 180614

개요
팀명, 주제 선정 : “알밥양많이”, Zillow Prize.

주안점 - 데이터를 어떻게 설명할 것인가?(효과적 이해, 설명)
중요한 데이터, 그래프만 선별해서 어떤 의미가 있는지 명확하게 설명해야 한다.
모든 내용, 연결이 논리 정연하게 근거 기반으로 이루어져야 한다.

타임라인
(1) EDA
데이터를 탐구한다. 
데이터 타입이 무엇인가, 데이터 분포는 어떠한가, 타깃의 분포는 어떠한가, missing value의 유의미한 상관관계 표현. 

(2) Feature Selection(Feature Engineering)
불필요한 정보를 제거한다.
Feature 전부 사용하지 않고, 몇 가지만 선택해서 사용하기에 Feature Selection이라고 한다.

(3) MODELING(ols regression)
법칙(명제)를 도출할 수 있는 모델을 만든다. 


—TODO—

(1) 모임 시간 정하기
6.19(화) 스터디 후 (약 15:00) : EDA 공유, f/b 1
6.23(토) 수업 후 (약 14:00) : EDA 공유, f/b 2

(2) 헬로데이터과학 참고해서 전체 가이드 잡기.
https://medium.com/@nureechung/eda-%EB%8D%B0%EC%9D%B4%ED%84%B0-%EC%84%A4%EB%AA%85%EC%84%9C%EC%97%90%EC%84%9C-%EC%8B%9C%EC%9E%91%ED%95%98%EA%B8%B0-230060b9fc17



## 1차 : EDA
데이터 탐구. 데이터 타입이 무엇인지, 데이터 분포는 어떠한지, 타깃의 분포는 어떠한지, missing value, 유의미한 상관관계 표현. 
데이터를 충분히 살펴보고 이해하고, 해당 데이터 관련 가설을 세우고, 그래프로 시각화한다.

— TODO — 

1.개별 독립 변수 분석
각 독립 변수의 요약통계지표 구하기
시각화(데이터 내용, 형태에 따라)
원본데이터 관찰

2.독립 변수 간 관계 분석



## 2차 : EDA

인사이트 공유
1. 집값을 찾는 것이 아니라, z-e의 모델을 파악하는 것. z-e의 logerror와 유사한 모델을 찾는다.
2. missing value를 고려. 
Missing value(NaN)의 의미를 아는 것이 첫 출발(NaN이 무엇인지 알아야)
모양, 관계를 파악한다.

— TO DO —
1.data_description 이해하기
2.개별 분석 공유하기(자료, 노하우)
3.토요일 과제 명확하게 세우기(데이터 분담)


## 3차 : EDA
Missing value 처리 : 속성 간 상관관계 고려
자료형 변환 : Binary 1, 0 / String 숫자

— TO DO —
1.속성 분배
2.논문을 통해, 속성 간 관계 파악(해당 속성이 어떤 의미인지 파악하기)



## 4차 : EDA, Featrue Selection

속성 제거
'calculatedbathnbr'
'calculatedfinishedsquarefeet'
'taxvaluedollarcnt',
'taxamount'
'regionidcounty'
'regionidcity'

eg.
regionidzip - 위도, 경도
architectureStypetype - 방 갯수, 지역(동부 / 서부), 기간(연도)
buildingquarlity - 연도, 자재, 



— TO DO —

(i) Dependent Column 처리 : 속성 간 종속 관계 파악(pairplot, heatmap 등)
(ii) Missing Value(결측치) 처리 : 다른 속성과의 상관관계 파악 




## 5차 : (다시) EDA

두 속성(columns) 간 관계 파악
두 속성만 데이터프레임으로 만들어서 눈으로 비교
페어플롯, 디스트플롯으로 비교



## 6차 : EDA 마무리

1.모델링의 근거를 마련하기 위해 개별 feature의, 각 feature 간 성질에 대한 가설 수립
- real number data의 경우. feature의 성질, feature 간 성질에 대해서 "검정" 시도.(근거 마련)
- category data의 경우. 개별 feature의 성질, feature 간 성질에 대해서 알기 위해 데이터 하나씩 뜯어보기.

2.확보한 인사이트, 괜찮은 방법론(접근법) 공유



## 7차 : 재정립. Modeling(with EDA, feature selection)

목적 : 
심플하면서(Engineering 관점. 가장 단순한 모델)
잘 맞으면서(VP가 높다)
성능도 좋은(다른 지표가 높다)
모델을 찾아서 만드는 것. 

검증 방법 :
(1) 새로운 데이터 활용
(2) 교차 검증(cross validation)

인사이트 : 
가중치의 절대값이 높을수록 좋다.
모델을 검증할 때는 새로운 데이터를 집어넣어봐야 알 수 있다.
전처리를 하지 않고 모델을 만드는 것은 큰 의미가 없다.
카테고리 값 NaN값 처리. 다른 데이터를 기반으로 회귀분석을 시도한다.(F-검정으로, NaN값을 어떻게 처리하면 좋을지 결정)
조건수는 10보다 작아야 좋다.
결측치가 많다고 속성을 제거하면 안 된다. 
- 특징값을 고려해서 mean, median 등을 채워넣는다.
- correlation이 높은 다른 속성을 고려해서 채워넣는다.
- 분포를 고려해서 난수를 채택해서 채워넣는다.
Collaborative filtering 아이디어 적용한다
Missing Value들을 클래스로 만들어서 모델링 후 prob(F)가 큰 경우에, Nan값을 제대로 처리해야 한다. 

— TODO —

(1) Missing Value 처리

A. correlation이 높은 다른 속성을 고려해서 채워넣는다.
dtype(real) : 상관계수가 높은 속성으로 채워넣는다
dtype(cat) : 

B. 분포를 고려해서 난수를 채택해서 채워넣는다.
C. 특징값을 고려해서 mean, median, mode 등을 채워넣는다.
>> A, B, C의 VP 비교하여 가장 나은 방법을 선택한다.



(2) Feature Selection

Class Selection(가중치가 높은 일부 클래스만 사용한다)
Feature Selection
카테고리, 실수 변수로 나눠서 모델링, VP 확인.



(3) 모델링, VP 확인

— DONE —
스케일링
영향력 적은 클래스 분류
Partial Regression
Category Variable OLS
Whole OLS
Numeric Variable VIF
변수 변환 (로그, 제곱근). 독립변수의 분포 확인 후.
다항 회귀. 차수 결정 후.(최적 정규화)
레버리지, 아웃라이어 제거
잔차의 정규성 검정
회귀 분석 결과의 진단(정규성 검정, qq plot, 모든 독립변수와 잔차 간 관계 그리기, 정규성 검정)
VP 확인

— TODO —
PCA
4분위수 및 특징값 구하기
상관계수 구하기
카이 제곱 분포 구하기



