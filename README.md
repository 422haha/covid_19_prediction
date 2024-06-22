# COVID-19 신규 확진자 예측 프로젝트

이 프로젝트는 머신러닝 모델을 이용하여 대한민국의 COVID-19 신규 확진자 수를 예측하는 것을 목표로 합니다.

## 프로젝트 개요

COVID-19는 새로운 유형의 코로나바이러스(SARS-CoV-2)에 의한 호흡기 감염질환으로, 2019년 12월 중국에서 처음 발견된 이후 전 세계적으로 확산되었습니다. 본 프로젝트에서는 시계열 예측 모델인 Facebook Prophet을 사용하여 대한민국의 신규 확진자 수를 예측합니다.

## 프로젝트 기간

- 2022년 1월 11일 ~ 2022년 1월 18일

## 데이터

### 데이터 출처

- 질병관리청에서 제공하는 COVID-19 정식 보도자료: [링크](http://ncov.mohw.go.kr/)
- 데이터 수집 기간: 2020-01-21 ~ 2022-01-17

### 데이터 전처리

- 결측치 처리
- 이상치 처리
- 사용한 컬럼: `date`, `confirmed`

## 사용한 라이브러리

- pandas
- plotly
- fbprophet
- numpy

## 예측 모델

- 사용한 모델: Facebook Prophet
- 모델 파라미터:
  - `changepoint_prior_scale=0.5`
  - `changepoint_range=0.95`
  - `yearly_seasonality=False`
  - `weekly_seasonality=True`
  - `daily_seasonality=True`
  - `seasonality_mode='additive'`

## 결과

예측 결과는 다음과 같습니다:

- yhat: 예측값
- yhat_lower: 오차를 고려한 예측 최소값
- yhat_upper: 오차를 고려한 예측 최대값

### 시각화

- 확진자 트렌드 그래프
  
  ![](C:\Users\KMY\AppData\Roaming\marktext\images\2024-06-22-14-46-53-image.png)

- 예측 결과 그래프
  
  <img src="file:///C:/Users/KMY/AppData/Roaming/marktext/images/2024-06-22-14-47-26-image.png" title="" alt="" data-align="center">

- changepoints 그래프
  
  <img src="file:///C:/Users/KMY/AppData/Roaming/marktext/images/2024-06-22-14-47-55-image.png" title="" alt="" data-align="center">

## 예측 성능 평가

```python
Actual values (last 7 days): [670269, 674649, 678807, 683341, 687753, 691936, 695788]
Predicted values (last 7 days): [716343.59514415, 721836.63776902, 727308.35647069, 732755.81703892,
738198.75331907, 743524.70559555, 748717.35735997]

MAE (Mean Absolute Error): 49448.89
RMSE (Root Mean Squared Error): 49499.54
```

## 교차 검증

교차 검증을 통해 모델의 성능을 평가하였습니다:

```python
   horizon         mse         rmse         mae      mape     mdape     smape  coverage
0   9 days  28062852.6  5297.438113  3971.922882  0.013028  0.010014  0.012925  0.000000
1  10 days  31454803.6  5608.457736  4230.266156  0.013785  0.010972  0.013670  0.000000
2  11 days  34456410.6  5869.958247  4437.570800  0.014315  0.011912  0.014190  0.000000
3  12 days  37019052.3  6084.328427  4603.435502  0.014703  0.012744  0.014568  0.055556
4  13 days  39469560.7  6282.480332  4759.719749  0.015098  0.013616  0.014956  0.111111
```

### 교차 검증 결과 시각화

<img src="file:///C:/Users/KMY/AppData/Roaming/marktext/images/2024-06-22-14-48-53-image.png" title="" alt="" data-align="center">

## 결론

본 프로젝트에서는 Facebook Prophet 모델을 이용하여 COVID-19 신규 확진자 수를 예측하였습니다. 예측 성능을 향상시키기 위해 추가적인 변수와 보다 체계적인 실험이 필요합니다.

## 실습 환경

- 사용한 도구: Python, Colab
- 실습 환경: Google Colaboratory

## 참고문헌

1. 배진수, 김성범 (2021). 머신러닝 모델을 이용한 대한민국 코로나 신규 확진자 예측. 대한산업공학회지, 47(3), 272-279.
2. 배진수, 김성범 (2020). 머신러닝과 딥러닝 기반의 코로나 신규 확진자 추세 예측. 대한산업공학회 추계학술대회 논문집, 3675-3685.
3. 김명휘 (2021). 정확한 딥러닝 기반 예측 모델을 활용한 코로나 확진자 예측 모델. 상명대학교 일반대학원.
