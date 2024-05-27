 # <p align="center"> 🎮2022~2023년 잠실야구장 관중수 예측 🎮 </p>
 ## <p align="center"> 데이터마이닝 8조  </p>

 ---
 
 ## <p align="center"> 🔔 1.개요 🔔 </p>

##### KBO 관중 150만 시대를 맞이하면서 구단 별 관중 수를 예측하기 위해 경기 요인, 날씨 요인, 경기장 이벤트 등의 추가 요인을 데이터로 구성하여 regression 모델을 사용하였따. 쓰레기 처리 문제 해결, 인파 몰림 예상, 관리 인원 효율적 배치, 대중교통 추가 배치, 구단 내 음식 수요예측을 위해 관중수를 예측할 필요성이 증가하였다. KBO 공식 홈페이지에 기록된 데이터를 기반으로 누적 순위표, 관중 수를 크롤링하였으며 기상청에서 날씨 데이터를 수집하였다. 데이터 전처리, 시각화 이후 Lasso Regression과 SGD Regression, Ridge Regression을 사용하여 최종 모델을 평가하였다. 

### 💡데이터 선정 
#### 1️⃣ 경기 요인: 날짜, 요일, 홈팀, 어웨이 팀, 홈/어웨이 각 순위, 승률, 연승
#### 2️⃣ 날씨 요인: 평균 기온, 합계 일사량, 일 강수량 
#### 3️⃣ 추가 요인: 공휴일 및 주말, 경기장 이벤트 여부, 경기 시작 시간 
#### 4️⃣ 타겟 데이터: 잠실 야구장 관중수 
잠실 야구장의 최대 관중수 23750을 기준으로 타겟 데이터의 백분율로 변환했다. 

### 💡데이터 전처리 
 #### 1️⃣ 칼럼 명 변경 
 한글 칼럼명을 영어 칼럼명으로 변경하였다. 

#### 2️⃣ 데이터 수치화  
연승(1패, 1승)을 (-1, 1)로 변경하였다. 공휴일과 이벤트 여부를 0, 1 binary 형태로 표현하였다. 

#### 3️⃣ 결측치 제거 
날씨 데이터 중 결측치를 제거하였다. 
#### 4️⃣ 날짜 데이터 구분 
연도, 월, 일, 요일 로 구분하여 인덱싱하였다. 
요일을 숫자로 변경했다. 월:0, 화:1, 수:2, 목:3, 금:4, 토:5, 일:6 
이후 숫자로 변환한 요일을 원 핫 인코딩으로 변환했다.
#### 5️⃣ 팀명 숫자로 변경 
LG:0, 두산:1, KIA:2, KT:3, NC:4, SSG:5, 롯데:6, 삼성:7, 키움: 8, 한화: 9 
이후 숫자로 변환한 팀을 원 핫 인코딩으로 변환했다.
  
  
### 💡Goal

  <br> We planned a solution using smartphone applications to solve these problems and reduce the seniors' fear of using digital devices. This solution allows seniors to learn and practice functions such as kiosk ordering, movie booking, and bus reservation, and we introduced a reward system to increase their accomplishment  with these exercises.


---

## <p align="center"> 🔔 2. Explanation of "OrderAttack" 🔔  </p>

### 🔔 Login & Register
<table style="width: 40%;">
  <tr>
   <td style="text-align: center;">
      <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%E1%84%92%E1%85%AC%E1%84%8B%E1%85%AF%E1%86%AB%E1%84%80%E1%85%A1%E1%84%8B%E1%85%B5%E1%86%B8.gif" alt="Image 1" style="width: 40%;">
      <p>Login & Register</p>
    </td>
  </tr>
</table>

### 🍔 Ordering by Kiosk Step
<table style="width: 40%;">
  <tr>
    <td style="text-align: center;">
      <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%9B%80%EC%A7%A4%20%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC%20%EC%84%B1%EA%B3%B5.gif" alt="Image 1" style="width: 100%;">
      <p>Kiosk Step</p>
    </td>
   <td style="text-align: center;">
     <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%E1%84%8F%E1%85%B5%E1%84%8B%E1%85%A9%E1%84%89%E1%85%B3%E1%84%8F%E1%85%B32.gif" alt="Image 2" style="width: 100%;">
      <p>Kiosk Step</p>
    </td>
</table>

#### You will practice ordering food using a kiosk at a fast food restaurant. Real photo verification will help you improve your IT ordering skills.

### 📽Booking a Movie Step
<table style="width: 40%;">
  <tr>
    <td style="text-align: center;">
      <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EB%AC%B4%EB%B9%84%20%EC%9B%80%EC%A7%A4.gif" alt="Image 1" style="width: 100%;">
      <p>Movie Step</p>
    </td>
   <td style="text-align: center;">
      <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EB%AC%B4%EB%B9%84%20%EC%84%B1%EA%B3%B5.gif" alt="Image 1" style="width: 100%;">
      <p>Movie Step</p>
    </td>
  </tr>
</table>

#### You will practice using the application to book tickets for a movie that is currently playing.

### 🍔 Bonus Stage
<table style="width: 50%;">
  <tr>
    <td style="text-align: center;">
      <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%E1%84%87%E1%85%A9%E1%84%82%E1%85%A5%E1%84%89%E1%85%B31.gif" alt="Image 1" style="width: 100%;">
      <p>Bonus stage</p>
     </td>
     <td style="text-align: center;">
     <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%E1%84%87%E1%85%A9%E1%84%82%E1%85%A5%E1%84%89%E1%85%B32.gif" alt="Image 1" style="width: 100%;">
      <p>Bonus stage</p>
    </td>
  </tr>
</table>

#### You will practice using the application to book tickets for a movie that is currently playing.

### 👛 Get Rewards : Wallet

<table style="width: 100%;">
  <tr>
    <td style="text-align: center;">
      <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%ED%82%A4%EC%98%A4%EC%8A%A4%ED%81%AC%20%EC%A7%80%EA%B0%91%20%ED%9A%8D%EB%93%9D%20%EC%9B%80%EC%A7%A4.gif" alt="Image 1" style="width: 100%;">
      <p>Wallet in Kiosk 1st step</p>
    </td>
    <td style="text-align: center;">
      <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%9B%80%EC%A7%A4%20%EB%AC%B4%EB%B9%84%20%EC%A7%80%EA%B0%91%20%ED%9A%8D%EB%93%9D.gif"alt="Image 1" style="width: 100%;">
      <p>Wallet in Movie 1st step</p>
    </td>
    <td style="text-align: center;">
      <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%E1%84%87%E1%85%A9%E1%84%82%E1%85%A5%E1%84%89%E1%85%B31.gif" alt="Image 1" style="width: 100%;">
      <p>Wallet in Kiosk Bonus step</p>
    </td>
  </tr>
</table>

#### As you progress through each level, you'll be able to change your wallet as a reward for your skills. Build your wallet with a sense of accomplishment.
---

## <p align="center"> 🔔 3. Architecture 🔔  </p>
<img width="1032" alt="오더어택 아키텍쳐" src="https://github.com/leeinsunny/orderattack_photo/blob/main/real_architecture.png">

 - 📱 FrontEnd
   - The app was developed using  Android Studio, Kortlin, and Pigma.
   - The Google Maps platform was used to utilize the map API.

 - 💻 BackEnd
    - Firebase was used for app data storage and management.
    - Google login was facilitated through the use of Authentication.
    - Firestore was used to manage user and other data.      
 - 🧠 AI Model
   - Tesseract replaces letters with text in photos taken from the gallery  
   - Google Bert recognizes the text that Tesseract has replaced.

---
## <p align="center"> 🔔 4. Execution Method 🔔  </p>
### For Android User
#### 📌 You can download language file => [Click Here!](https://drive.google.com/file/d/1vmn5PTXRt147OB2GA3CgqgqTOmZucqq-/view?usp=sharing)
#### 📌 Android AVD size=1440*3040
#### 📌 You have to give permission for INTERNET & Location

---

## <p align="center"> 🔔 5. Scalability 🔔  </p>
### 👑 Ranking System
<img width="200" alt="오더어택 순위" src="https://github.com/leeinsunny/orderattack_photo/blob/main/rank.png">

- Designed to encourage people to practice continuously ​
- Allow user to continue their social activities on their own through digital devices.​
- With RecyclerView for smooth, responsive displays, we handle real-time data effectively, enhancing user interaction. 


### 🎀Decorating Your Wallet
<img width="200" alt="오더어택 지갑" src="https://github.com/leeinsunny/orderattack_photo/blob/main/wallet.png">

- A gaming element to instill fun and motivate the user to practice by allowing them to acquire a new wallet every step they clear.​
- Which can be obtained upon clearing a game stage, in the database.


### 🏘️ Healing Town
<img width="200" alt="오더어택 club" src="https://github.com/leeinsunny/orderattack_photo/blob/main/vilage.png">

- Here, seniors can create and participate in the club they want.​
- This allows seniors to meet offline.
  
<img width="200" alt="오더어택 채팅" src="https://github.com/leeinsunny/orderattack_photo/blob/main/chat.png">

- A community page will further engage users, enabling real-time posts and interactions, powered by Firebase’s scalable infrastructure

### 🔣Language Extension
<img width="200" alt="오더어택 언어확장" src="https://github.com/leeinsunny/orderattack_photo/blob/main/vilage.png">

- It aims to help more seniors escape digital alienation ​by changing the learning language of AI models


---

## <p align="center"> 🔔 6. Member 🔔  </p>

| [<img src="https://avatars.githubusercontent.com/u/105425832?v=4">](https://github.com/leeinsunny) |[<img src="https://avatars.githubusercontent.com/u/98581610?v=4">](https://github.com/uykm) | [<img src="https://avatars.githubusercontent.com/u/143007050?v=4">](https://github.com/sally7788) | [<img src="https://avatars.githubusercontent.com/u/136828827?v=4">](https://github.com/Hz2314) |
|:---:|:---:|:---:|:---:
이인선|신민규|강연주|박현정

---

## <p align="center"> 🔔 7. Youtube & Material 🔔  </p>
📌 You can see our solution's presentation => [Click Here!](https://youtu.be/d3jnIkHnQaE?si=BAbnH9W2WJpt7Ij)

📌 You can download our solution's presentation material => [Click Here!]("링크")

<table style="width: 100%;">
    <tr>
        <td style="text-align: center;"> 
            <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C1.PNG" alt="Image 1" style="width: 100%;">
            <p>1</p> 
        </td>
        <td style="text-align: center;"> 
            <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C2.PNG" alt="Image 2" style="width: 100%;">
            <p>2</p> 
        </td>
        <td style="text-align: center;"> 
            <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C3.PNG" alt="Image 3" style="width: 100%;">
            <p>3</p>
        </td>
        <td style="text-align: center;"> 
            <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C4.PNG" alt="Image 4" style="width: 100%;">
            <p>4</p>
        </td>
    </tr>
    <tr>
        <td style="text-align: center;"> 
            <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C5.PNG" alt="Image 5" style="width: 100%;">
            <p>5</p> 
        </td>
        <td style="text-align: center;"> 
            <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C6.PNG" alt="Image 6" style="width: 100%;">
            <p>6</p> 
        </td>
        <td style="text-align: center;"> 
            <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C7.PNG" alt="Image 7" style="width: 100%;">
            <p>7</p>
        </td>
        <td style="text-align: center;"> 
            <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C8.PNG" alt="Image 8" style="width: 100%;">
            <p>8</p>
        </td>
    </tr>
    <tr>
        <td style="text-align: center;"> 
            <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C9.PNG" alt="Image 9" style="width: 100%;">
            <p>9</p> 
        </td>
        <td style="text-align: center;"> 
            <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C10.PNG" alt="Image 10" style="width: 100%;">
            <p>10</p> 
        </td>
        <td style="text-align: center;"> 
            <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C11.PNG" alt="Image 11" style="width: 100%;">
            <p>11</p>
        </td>
        <td style="text-align: center;"> 
            <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C12.PNG" alt="Image 12" style="width: 100%;">
            <p>12</p>
        </td>
    </tr>
   <tr>
        <td style="text-align: center;"> 
            <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C13.PNG" alt="Image 13" style="width: 100%;">
            <p>13</p> 
        </td>
        <td style="text-align: center;"> 
            <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C14.PNG" alt="Image 14" style="width: 100%;">
            <p>14</p> 
        </td>
        <td style="text-align: center;"> 
            <img src="https://github.com/leeinsunny/orderattack_photo/blob/main/%EC%8A%AC%EB%9D%BC%EC%9D%B4%EB%93%9C15.PNG" alt="Image 15" style="width: 100%;">
            <p>15</p>
        </td>
        <td style="text-align: center;"> 
              <img src="" alt="" style="width: 100%;">
            <p></p>
        </td>
    </tr>
</table>


