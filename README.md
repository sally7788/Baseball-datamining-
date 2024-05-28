 # <p align="center"> ⚾ 2022~2023년 잠실야구장 관중수 예측 ⚾ </p>
 
<p align="center">
  <img src="https://github.com/sally7788/Baseball-datamining-/assets/143007050/07ac414c-c19b-4b93-b228-f72f0b1519b6">
</p>

 ## <p align="center"> 데이터마이닝 8조  </p>

 ---
 
 ## <p align="center"> 🔔 1.개요 🔔 </p>

##### KBO는 지금 관중 150만 시대를 맞이하면서 흥행을 이어 나가고 있다. 하지만 관중이 증가함에 따라 쓰레기 처리 문제, 특정 시간대의 인파 몰림, 관리 인원과 대중교통의 부족 등의 문제점이 발생하고 있다. 이러한 문제점을 파악하고 관중수를 예측하여 관중 증가에 따른 문제 해결에 이바지하려 한다. 
##### 먼저 경기장의 관중 수를 예측하기 위해 경기 진행 팀들의 성적 관련 요인, 기상 요인, 경기장에서 발생하는 이벤트 등을 데이터로 사용하려 한다. 이러한 데이터 수급을 위해 KBO 공식 홈페이지에 있는 과거 데이터를 기반으로 순위, 관중 수 등을 크롤링하였으며, 기상 데이터는 기상청을 통해 수집하였고 이를 기반으로 전처리, 시각화 과정을 통해 데이터의 분포 등을 파악하였다.  
##### 마지막으로 관중 수를 예측하는 것이 목적이기 때문에 regression 모델을 통해 연속형 변수 예측을 시도한다. 회귀 모델 선정 과정을 통해 Lasso Regression과 SGD Regression, Ridge Regression을 채택하였고 위 모델들의 결과를 비교하여 최종 모델을 완성하려 한다.

### <p align="center"> 🔔 2. 발표자료 & train, test data 🔔  </p>
📌 발표 ppt => [Click Here!](https://drive.google.com/file/d/11rzQTefHaXWNB837G_iiDbad_A95-Cv2/view?usp=sharing)

📌 분석에 사용한 데이터 => [Click Here!](https://drive.google.com/file/d/1AcNk-mEE3DN4pKmjd5q9in9jdaVVeqv8/view?usp=sharing)

### 💡데이터 선정 
#### 1️⃣ 경기 요인: 날짜, 요일, 홈팀, 어웨이 팀, 홈/어웨이 각 순위, 승률, 연승
#### 2️⃣ 날씨 요인: 평균 기온, 합계 일사량, 일 강수량 
#### 3️⃣ 추가 요인: 공휴일 및 주말, 경기장 이벤트 여부, 경기 시작 시간 
#### 4️⃣ 타겟 데이터: 잠실 야구장 관중수 
잠실 야구장의 최대 관중수 23750명을 기준으로 타겟 데이터의 백분율로 변환했다. 

### 💡데이터 전처리 
 #### 1️⃣ 칼럼 명 변경 
 한글 칼럼명을 영어 칼럼명으로 변경하였다. 

#### 2️⃣ 데이터 수치화  
연승(1패, 1승)을 (-1, 1)로 변경하였다. 공휴일과 이벤트 여부를 0, 1 binary 형태로 표현하였다. 

#### 3️⃣ 결측치 제거 
날씨 데이터 중 결측치를 모두 0으로 처리하였다. 
#### 4️⃣ 날짜 데이터 구분 
연도, 월, 일, 요일 로 구분하여 인덱싱하였다. 요일을 월:0, 화:1, 수:2, 목:3, 금:4, 토:5, 일:6 의 숫자로 변환한 후, 원 핫 인코딩을 이용하여 변환했다.
#### 5️⃣ 팀명 숫자로 변경 
LG:0, 두산:1, KIA:2, KT:3, NC:4, SSG:5, 롯데:6, 삼성:7, 키움: 8, 한화: 9 
이후 숫자로 변환한 팀을 원 핫 인코딩으로 변환했다.
  
  
### 💡Goal

##### 잠실 야구장 관중 수를 예측하여 쓰레기 발생량, 특정 시간 인파 몰림, 이벤트 참여 예상 인원, 구단 내 음식점 판매량을 예측할 수 있다. 이는 쓰레기 처리 문제를 효율적으로 해결할 수 있고, 관리 인원 추가 배치 등 인파 통제 전략을 수립 가능하게 한다. 또한 이벤트와 행사 시점을 선정하고 수량을 주문하는 데에 큰 도움이 되며 음식과 음료의 수익화의 바탕이 된다. 
---

## <p align="center"> 🔔 3. 모델 학습 🔔  </p>

### 💡 Lasso Regression  결과
#### 가장 높은 성능, 데이터에 가장 적합한 모델 
##### selectKBest(ANOVA F-score) feature selection-25개 특성 선택
##### GridSearch 이용한 하이퍼파라미터 튜닝-alpha:0.001
<table style="width: 40%;">
  <tr>
   <td> </td> <th style="text-align: center;"> MSE</th> <th style="text-align: center;"> R^2 </th> <th style="text-align: center;"> RMSE </th>
  </tr>
 <tr> 
  <td> Train </td> <td> 0.01347</td> <td> 0.80742</td> <td> 0.11605</td>
 </tr>
 <tr> 
  <td> Test </td> <td> 0.02087</td> <td> 0.64689</td> <td> 0.14446</td>
 </tr>
</table>

### 💡 SGD Regression  결과
##### selectKBest(ANOVA F-score) feature selection-25개 특성 선택
##### standard Scaler 사용 
##### K-fold cross validation 사용 n_split=5
##### GridSearch 이용한 하이퍼파라미터 튜닝-alpha:10
<table style="width: 40%;">
  <tr>
   <td> </td> <th style="text-align: center;"> MSE</th> <th style="text-align: center;"> R^2 </th> <th style="text-align: center;"> RMSE </th>
  </tr>
 <tr> 
  <td> Train </td> <td> 0.01369</td> <td> 0.80417</td> <td> 0.11702</td>
 </tr>
 <tr> 
  <td> Test </td> <td> 0.02268 </td> <td> 0.61616</td> <td> 0.15061</td>
 </tr>
</table>

### 💡 Ridge Regression  결과
##### feature selection-25개 특성 선택
##### standard Scaler 사용 
##### K-fold cross validation 사용 n_split=5
##### GridSearch 이용한 하이퍼파라미터 튜닝-alpha:0.001
<table style="width: 40%;">
  <tr>
   <td> </td> <th style="text-align: center;"> MSE</th> <th style="text-align: center;"> R^2 </th> <th style="text-align: center;"> RMSE </th>
  </tr>
 <tr> 
  <td> Train </td> <td> 0.01355</td> <td> 0.80618</td> <td> 0.11642</td>
 </tr>
 <tr> 
  <td> Test </td> <td> 0.022</td> <td> 0.62773</td> <td> 0.14832</td>
 </tr>
</table>

## <p align="center"> 🔔 4. 기대효과 및 결론 🔔  </p>
Lasso regression이 가장 좋은 결과를 보였다. 추후 개선할 때에는 더 많은 데이터를 확보하고, 각 시즌별 특성을 고려한 피처를 선택해야 하고, 더 많은 평가 지표를 사용해야하고, 다양한 튜닝 방식을 적용해야 한다. 

### 💡 기대효과
 #### 1️⃣ 마케팅 및 판매 
 예측된 관중 수에 맞추어 티켓 프로모션이나 할인 이벤트를 기획할 수 있다. 

#### 2️⃣ 경기 운영 최적화 
관중 수에 따라 필요한 경기장 스태프의 수를 미리 결정할 수 있어 인력을 효율적으로 운영할 수 있다. 

#### 3️⃣ 팬 경험 향상 
예측된 관중 수에 따라 경기 장 내 서비스 품질을 높일 수 있는 방안을 마련할 수 있다. 
#### 4️⃣ 날짜 데이터 구분 
스폰서와 광고 계약 시, 예상 관중 수 데이터를 활용하여 더 유리한 조건을 협상할 수 있다. 

---

## <p align="center"> 🔔 5. 팀원 🔔  </p>


|<img src="https://avatars.githubusercontent.com/u/62709976?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/138552558?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/70998377?v=4" width="150" height="150"/>|<img src="https://avatars.githubusercontent.com/u/143007050?v=4" width="150" height="150"/>|
|:-:|:-:|:-:|:-:|
|[@mouseeater](https://github.com/mouseeater)|[@shekxkx](https://github.com/shekxkx)|[@chlwldnd542](https://github.com/chlwldnd542)|yunjoo<br/>[@sally7788](https://github.com/sally7788)|
김민준|최민지|최지웅|강연주 
---




