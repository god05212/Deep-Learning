# Chest X-Ray Images (Pneumonia)
## X-Ray 사진에서 폐렴을 감지하고 분류하기
프로젝트 기간: 2023/02/03(금) ~ 2023/02/17(금)  
<br/>
## 개요
폐렴을 감지하고 분류하는 딥 러닝 모델을 개발하는 프로젝트를 진행하였습니다. 폐렴은 세균성 폐렴, 바이러스성 폐렴, 마이코플라스마 폐렴, 곰팡이 성 폐렴 등 다양한 유형이 있는데, 이 데이터셋은 첫 두 유형에 속하는 폐렴 샘플로 구성되어 있습니다. 그러나 데이터셋이 매우 제한적이며 불균형한 특성을 가지고 있습니다.

이 프로젝트의 목표는 제한된 양의 데이터를 기반으로 강력한 딥 러닝 모델을 개발하는 것입니다. 의료 분야에서 머신 러닝과 딥 러닝은 중요한 역할을 수행하지만, 의료 분야의 문제는 단순한 분류 문제를 넘어서기 때문에 적용하기가 어렵습니다. 그러나 신중하고 조심스럽게 적용한다면, 의료 분야에 많은 이점을 제공할 수 있습니다.

따라서, X-Ray 사진에서 폐렴을 감지하고 분류하는 모델을 개발하여 의료 분야에 도움을 주고자 하였니다. 또한 제한된 양의 데이터로도 우수한 성능을 발휘하는 모델을 만들고자 하였습니다.  
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
- 이미지 데이터를 전처리하고 데이터를 생성하였습니다. 이를 통해 일반 및 폐렴 사진 간의 차이를 확인하였습니다.
- 데이터셋에는 의료 전문가가 라벨을 붙였습니다. 라벨링 과정에서 의료 전문가들은 각 데이터 포인트에 대해 폐렴 여부를 판단하고 해당 라벨을 할당하였습니다. 의료 전문가들은 자신들의 전문적인 지식과 경험을 바탕으로 판단을 내리며, 횡격막 주변의 경계선의 뚜렷함 등을 고려하여 라벨을 지정하였을 것으로 예상됩니다. 따라서, Convnet을 사용하여 폐렴을 감지하고 분류하였습니다.
- 데이터셋을 pandas DataFrame으로 변환한 후 countplot을 사용하여 긍정 사례와 부정 사례의 수를 시각화하였습니다.
- Convnet을 초기화하고, layers를 추가하여 모델을 정의하였습니다.
- 과대적합을 피하기 위해 데이터 확장(Data Augmentation)과 드롭아웃(Dropout)을 적용하였습니다.
- 모델을 학습시킨 후 test set에서 테스트하고, 정확도(Accuracy)를 평가하였습니다.
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
