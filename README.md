# Customer_Relationship_Management
스포츠센터 회원의 행동 정보를 이용해서 관리
## 탈퇴회원과 지속회원의 차이
### 탈퇴회원  
<img width="507" alt="image" src="https://user-images.githubusercontent.com/24906028/179410826-89c904ac-3b63-434f-87cd-2e72dc5e9ec1.png">

### 지속회원
<img width="500" alt="image" src="https://user-images.githubusercontent.com/24906028/179410835-987ca776-1f34-42d3-951d-0c95ea4b3754.png">  
지속회원의 routine_flg 평균값은 0.98로 대부분 정기적으로 이용하고 있지만 탈퇴 회원은 0.45로 거의 절반은 랜덤하게 이용하고 있다.

## 군집화하여 행동 패턴을 파악하고 행동 예측
고객의 한달 이용 이력 평균, 중앙값, 최댓값, 최솟값, 회원기간을 기준으로 4개의 군집으로 K-means Clustering 수행  
클러스터링에 사용한 변수는 5개로 시각화를 위해 PCA를 활용해 2차원으로 차원축소  
![image](https://user-images.githubusercontent.com/24906028/179411204-a05527a8-aaa4-4d0a-adee-52c4131dc980.png)  
탈퇴회원을 특정하기 위해 is_deleted열을 customer_clustering에 추가해서 cluster 및 is_deleted로 집계  
<img width="158" alt="image" src="https://user-images.githubusercontent.com/24906028/179411276-af784bf9-8517-4e49-b035-a8d79fac1be6.png">  
그룹 2와 그룹 3은 지속회원이 많고 그룹 1은 탈퇴회원만 있으며 그룹 0은 골고루 포함  
그룹 2는 회원기간이 짧지만 초기에 의욕적이어서 전체적으로 이용률이 높으며  
그룹 3은 회원기간이 길고 이용률은 그룹 2보다 낮지만 지속회원이 많아 이용이 안정적인 그룹  
<img width="160" alt="image" src="https://user-images.githubusercontent.com/24906028/179411467-8c38fe73-0733-4ec9-b604-ded8c9bb48fa.png">  
지속회원이 많은 그룹 0, 그룹 3에는 정기적으로 이용하는 회원이 많다.

## 다음 달 이용 횟수 예측
과거 6개월의 이용 데이터를 사용해 다음 달의 이용 횟수 예측

### 변수 기여도
<img width="136" alt="image" src="https://user-images.githubusercontent.com/24906028/179412134-ad247e4a-9963-4952-8ec2-39de54b6e409.png">  
가장 최근 달의 이용 횟수가 다음 달 이용 횟수에 가장 큰 영향

### 6개월 동안 달마다 7번, 8번, 6번, 4번, 4번, 3번 방문한 회원과 6번, 4번, 3번, 3번, 2번, 2번 방문한 회원(두 회원 모두 재적 기간 8개월)의 다음 달 방문횟수 예측
<img width="159" alt="image" src="https://user-images.githubusercontent.com/24906028/179413152-9ebc966c-aa0f-4479-97de-878fddaf7068.png">

## 탈퇴 예측
### 변수 기여도
<img width="210" alt="image" src="https://user-images.githubusercontent.com/24906028/179419030-50c72d54-d958-48c2-832c-28f8340c3399.png">

### 예측하기
count_1 = 3  
routine_flg = 1  
period = 10  
campaign_name ='입회비무료'  
class_name = '종일'  
gender = 'M'  
<img width="32" alt="image" src="https://user-images.githubusercontent.com/24906028/179419330-51c63053-50a3-4a3c-a8ff-ecbf789a22f7.png">  
탈퇴로 예측함


