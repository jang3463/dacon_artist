# KT-ETRI-AI-Competition
## 1. 개요
https://www.etnews.com/20220615000156  
https://aifactory.space/competition/detail/2048
  - 주제 : 실시간 OTT 서비스 이용자 수 트래픽 데이터를 기반으로 이상 발생 시점을 탐지
  - Task : Time series, Anomaly Detection
  - 기간 : 2022.04.18 ~ 2022.05.13, 2022.06.14(발표)
  - 결과 : 최우수상 2등
  - 방법 : Unsupervised Anomaly Detection, AutoEncoder에 적대적 학습(adversarial training)을 접목하여 모델 구축
<!--  Other options to write Readme
  - [Deployment](#deployment)
  - [Used or Referenced Projects](Used-or-Referenced-Projects)
-->
## 2. 데이터셋 설명
<!--Wirte one paragraph of project description -->  
- 미디어 서버 13종으로부터 수집된 5분 주기의 트랜잭션 데이터 24개월치가 제공.


- 파일명 설명
  - INFO.csv : 상품 가입/해지, 약관 동의, 구매, 포인트 조회를 위한 서버
  - LOGIN.csv : 로그인, 본인 인증, PIN 관리를 위한 서버
  - MENU.csv : 초기 메뉴, 채널 카테고리 메뉴 제공을 위한 서버
  - STREAM.csv :  VOD 스트리밍을 위한 서버


- 데이터 컬럼 설명
  - Timestamp: [YYYYMMDD_HHmm(a)-HHmm(b)] 형식을 가지며 수집 범위는 YYYY년 MM월 DD일 HH시 mm분(a)부터 HH시 mm분(b)
  - Server: 수집 서버 분류
  - Request: 수집 범위 내 발생한 서비스 요청 수
  - Success: 수집 범위 내 발생한 서비스 요청 성공 수
  - Fail: 수집 범위 내 발생한 서비스 요청 실패 수
  - Session: 수집 시점의 미디어 스트리밍 세션 수

**서버 중 하나라도 이상이면 최종 이상이라고 간주

## 3. 수행방법
<!-- Write Overview about this project -->
- 본 과제의 특징은 어떤 시점에 이상이 발생하였는지의 레이블 정보가 제공되지 않는다는 것 (Unsupervised learning)
- 먼저 데이터 전처리 과정에서 4종류의 데이터프레임을 하나로 concat. 
- 그 후, 정규화와 지수 가중 함수를 적용하여 데이터 스무딩을 진행. 시간 데이터를 묶어 예측하도록 재구성하는 것이 중요한 과정
- 모델 구축에서는 [USAD(Unsupervised anomaly detection on multivariate time series)](https://dl.acm.org/doi/pdf/10.1145/3394486.3403392)를 사용
- USAD 모델은 Autoencoder와 GAN의 장점을 결합하여 구성되어 있어 안정적인 학습이 가능
- 결과적으로, 158개의 이상 탐지를 성공하였고, F2_Score는 0.7234를 기록

## 4. 한계점
<!-- Write Overview about this project -->
- 이 프로젝트에서는 결측치를 0으로 대체하는 방법을 사용했는데, 최선의 방법은 아니였음. 예를 들어, 평균 대치나 회귀분석을 통해 결측치를 예측하는 등 다른 방식으로 시도해볼 필요 있음. 

## Team member
장종환 (개인 참가)
