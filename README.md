# DACON-Artist Classification-AI-Competition
## 1. 개요
https://dacon.io/competitions/official/236006/overview/description
  - 주제 : 예술 작품을 화가 별로 분류하는 AI 모델 개발
  - Task : Image Classification
  - 기간 : 2022.10.04 ~ 2022.11.14
  - 결과 : 5등 / 215 => 수상
<!--  Other options to write Readme
  - [Deployment](#deployment)
  - [Used or Referenced Projects](Used-or-Referenced-Projects)
-->
## 2. 데이터셋 설명
<!--Wirte one paragraph of project description -->  
- train.csv : 학습 데이터셋은 대표적인 화가 50명에 대한 예술 작품(이미지) 제공 (5911개)
- test.csv : 테스터 데이터셋은 대표적인 화가 50명에 대한 예술 작품(이미지)의 **일부분만 제공** (12670개)
<img width="300" height="400" alt="image" src="https://github.com/jang3463/dacon_artist/assets/70848146/47866fd0-63a3-4e1f-9b70-c9cc8802c031">
<img width="300" height="400" alt="image" src="https://github.com/jang3463/dacon_artist/assets/70848146/a93cfcbd-aba6-4764-b041-c23d892b10d9">

## 3. 수행방법
<!-- Write Overview about this project -->
- 본 과제의 특징은 테스트 데이터 셋은 예술작품(이미지)의 일부분(약1/4)만을 제공하기 때문에 train과 test 사이의 domain gap 발생
- 이를 해결 하기 위해서 train시에 이미지를 가로,세로를 1/2 비율로 Random Crop하도록 augmentation 진행
- 추가적으로 Overfitting을 방지하고 데이터 diversity를 늘리기 위해서, CutMix, CutOut과 같은 data augmentation 기법 적용
- 모델로는 CNN과 Transformer를 결합한 ConvNext_Large 모델 사용
- 최종적으로 F1-score 0.85487 달성

## 4. 한계점
<!-- Write Overview about this project -->
- train 데이터에 존재하는 화가의 작품 개수가 불균형 해서 data imbalance의 문제가 있었음. 이 부분을 해소하기위한 방법이 부족했음
- 모든 화가의 작품을 균등하게 학습할 수 있도록 Weighted Random Sampling 진행하면 더 좋은 성능을 얻을 것으로 보임

## Team member
장종환 (개인 참가)
