# Chest X-Ray Images (Pneumonia)
## X-Ray 사진에서 폐렴을 감지하고 분류하기
프로젝트 기간: 2023/02/03(금) ~ 2023/02/17(금)  
<br/>
## 개요
X-Ray 사진에서 폐렴을 감지하고 분류하는 프로젝트입니다. 폐렴은 매우 흔한 질병입니다. 1) 세균성 폐렴 2) 바이러스성 폐렴 3) 마이코플라스마 폐렴 4) 곰팡이 성 폐렴 중 하나 일 수 있습니다. 이 데이터 셋에는 처음 두 클래스에 속하는 폐렴 샘플로 구성됩니다. 데이터 셋에는 매우 적은 수의 샘플로 구성되어 있으며 너무 불균형합니다. 이 커널의 목표는 제한된 양의 데이터에서 처음부터 강력한 딥 러닝 모델을 개발하는 것입니다. 어떻게 작동하는지 안다면, 제한된 양의 데이터로도 좋은 모델을 만들 수 있을 것입니다.  
머신 러닝과 딥 러닝은 의료 분야에서 큰 역할을 지니고 있지만 단순한 분류 문제 그 이상이기에 의료 분야에 적용하는 것은 그리 간단하지 않습니다. 하지만 매우 조심스럽게 적용된다면, 세상에 엄청난 이로움을 줄 수 있습니다. 따라서, 의료 분야에 도움 될 수 있도록 X-Ray 사진에서 폐렴을 감지하고 분류하는 모델을 만들고자 하였습니다.  
<br/>
## 사용한 데이터셋
Chest X-Ray Images (Pneumonia)  
- Paul Mooney  
- https://www.kaggle.com/paultimothymooney  
- https://www.kaggle.com/datasets/paultimothymooney/chest-xray-pneumonia  
- Data: https://data.mendeley.com/datasets/rscbjbr9sj/2
- License: CC BY 4.0
- Citation: http://www.cell.com/cell/fulltext/S0092-8674(18)30154-5  

위 데이터셋은 3개의 폴더(train, test, val)로 구성되며 각 이미지 범주(Pneumonia/Normal)에 대한 하위 폴더를 포함합니다. 5,863개의 X-Ray 사진(JPEG)와 2개의 카테고리(Pneumonia/Normal)가 있습니다. 흉부 X-Ray 사진(전후방)은 광저우 여성 아동 의료 센터의 1~5세 소아 환자의 회고록에서 선택되었습니다. 모든 흉부 X-Ray 사진은 환자의 임상 치료 일환으로 수행되었습니다. 흉부 X-Ray 이미지 분석을 위해 모든 흉부 X-Ray 사진은 초기에 저품질 또는 판독 불가능한 스캔을 모두 제거하여 품질 관리를 위해 선별되었습니다. 그런 다음 이미지에 대한 진단은 AI 시스템 훈련을 위해 승인되기 전에 두 명의 전문 의사에 의해 등급이 매겨졌습니다. 채점 오류를 설명하기 위해 세 번째 전문가도 평가 세트를 확인했습니다.  
<br/>
## 프로젝트 목록
1. LOADING DATA  
2. DATA VISUALIZATION  
3. MODEL BUILDING  
4. CONCLUSION  
<br/>

## 프로젝트 수행 과정
- 이미지 데이터 전처리 및 데이터를 생성하였습니다.
- 무작위로 일반 및 폐렴 사진을 봄으로써 두 경우의 차이점을 봐보았습니다.
- 데이터 셋에는 의료 전문가가 라벨을 붙입니다. 따라서 일반인이 해독하기 어렵지만 횡격막 주변의 경계선의 뚜렷함 여부가 결정적인 요인이 될 수 있을 것 같습니다. 그럼에도 불구하고, 예외가 있을 것으로 보이므로 이 진단은 주관적인 문제로 보고, Convnet을 통해 살펴보았습니다.
- countplot으로 표시하기 위해 데이터 셋을 pandas dataframe으로 변경한 후 긍정 사례와 부정 사례의 수를 표시하였습니다.
- Convnet을 초기화하고, layers를 추가하여 정의하였습니다.
- 과대적합을 피하기 위해 데이터 확장(Data Augmentation)과 드롭아웃(Dropout)을 적용하였습니다.
- 모델을 학습시킨 후 test set에서 테스트하고, Accuracy를 평가하였습니다.
<br/>

## 모델의 test dataset에 대한 accuracy (소숫점 다섯 째 자리에서 반올림)
| Model | accuracy |
|:----------------------------------------|:-------|
| Convolutional neural network            | 0.8894 |
<br/>

## 최종 모델
Convolutional neural network
- test dataset에 대한 결과
    - accuracy: 약 0.8894
