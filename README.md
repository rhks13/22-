## 2022년 통계 데이터 분석 / 활용대회
# 코로나 19 전후 폐업 요인분석

## 배경
+ 주제 선정
  + 코로나 전후로 외식업 자영업자들의 폐업의사와 실제 폐업률이 증가
  + 팬데믹으로 인해 기존과 달라진 경제/소비 상황에 맞춰 창업위험요인을 더욱 면밀하게 파악할 필요성
+ 분석 필요성 및 전략
  + 기존 상권 분석시스템과 달리 주요폐업요인을 면밀하게 분석
  + 분류결과의 설명변수를 도출할 수 있도록 모델을 설계하고 폐업여부를 예측할 것
  
  
## 분석 과정
### 데이터 선정
  + 업체자료, 상권자료, 경제지표
    + 업체자료 : 서울시에 외식업 사업자등록이 되어있는 업체자료
    + 상권자료: 해당 업체가 속한 상권의 특징을 나타나내는 자료
    + 경제지표 : 업체의 인허가 시기 기준 경제상황을 파악할 수 있는 경제지표
 
 + 기존 원자료 존재변수를 바탕으로 파생변수 생성
    + 공시지가 * 시설총규모 => 추정임대료
    + 인허가 일자 & 폐업일자 => 1년/3년 내 폐업여부(종속변수)
    + 집객시설 / 생활인구 => 시설밀도
    + etc..
 
### 데이터 전처리
+ 업체자료, 상권자료, 경제지표의 병합
  + 신규 창업자의 입장에서 수집할 수 있는 정보만을 이용
  + 업체자료 - 경제지표 : 인허가 일자 기준
  + 업체자료 - 상권자료 : 업체의 좌표 & 상권의 중심좌표 
  + 결측치 MICE 대체

### 데이터 분석
+ 참고사항
  + 분류모델 : 5가지의 분류모델 후보 중 성능지표를 바탕으로 XGBoost 선정
  + 불균형성 : 종속변수의 불균형 => 오버샘플링 기법(ADASYN)사용 => 모델의 설명력, 정확도 향상

+ 1년 내 폐업여부/3년 내 폐업여부 예측모델 

  ![image](https://user-images.githubusercontent.com/69777594/230303556-420f8be2-080e-45f4-adea-7d6380c96508.png)
  + 대출금리, 업종분류, 상주인구가 공통으로 주요한 영향력 행사
  + 단기간 폐업 여부에는 요식업 종류가, 장기간 폐업여부에는 유동인구의 연령층이 큰 요인으로 작용

+ 코로나 시기 구분 모형 결과 및 해석

  ![image](https://user-images.githubusercontent.com/69777594/230304806-e5cbfa8e-2877-42b2-8c9e-f43043eef175.png)
  + 코로나 이전에는 대출금리의 단순 고저가 아닌 평시 대비 변화의 영향을 받음
  + 코로나 이후에는 소비자 물가지수로 인한 급격한 물가상승의 영향을 받음

## 분석 활용 전략
### 기대효과 및 방향성 제시
+ 현실적인 창업요건의 기준점 마련
+ 시기/지역별로 해당 모델의 해석을 통해 상권/지역별 맞춤 정책 실시 가능성

