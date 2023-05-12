# DACON-Artist Classification-AI-Competition
## 1. 개요
https://dacon.io/competitions/official/236006/overview/description
  - 주제 : 예술 작품을 화가 별로 분류하는 AI 모델 개발
  - Task : Image Classification
  - 기간 : 2022.10.04 ~ 2022.11.14
  - 결과 : 5등 / 215
<!--  Other options to write Readme
  - [Deployment](#deployment)
  - [Used or Referenced Projects](Used-or-Referenced-Projects)
-->
## 2. 데이터셋 설명
<!--Wirte one paragraph of project description -->  
- train.csv : 학습 데이터셋은 대표적인 화가 50명에 대한 예술 작품(이미지) 제공 (5911개)
- test.csv : 테스터 데이터셋은 대표적인 화가 50명에 대한 예술 작품(이미지)의 **일부분만 제공** (12670)

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
