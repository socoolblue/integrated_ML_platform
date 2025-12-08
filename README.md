# 세종대학교 소재허브 AI 기반 소재 설계 자동화 플랫폼 Integrated Machine Learning Platform (IMLP)

Integrated Machine Learning Platform(IMLP)은 세종대학교 소재허브 연구단에서 신소재 개발 가속화를 위해 구축한 AI 기반 기계학습 통합 플랫폼입니다. 복잡하고 비선형적인 재료 시스템의 상관관계를 정밀하게 분석하며, 단일 모델의 한계를 극복하기 위해 여러 머신러닝(ML) 및 딥러닝(DL) 모델을 병렬적으로 학습하고 검증합니다. IMLP는 기존의 경험적 방식에서 벗어나, 데이터 기반의 지능형 예측 및 최적 설계 환경을 구현합니다.

 ## 주요 기능

### 1.	양방향 학습 구조
- Forward Prediction: 조성 및 공정 조건을 입력으로 받아 물리적, 기계적 특성(물성)을 정밀하게 예측합니다.

- Backward Prediction: 원하는 목표 물성을 입력으로 받아 이를 만족하는 최적의 조성 및 공정 조건을 역으로 탐색하고 제안합니다.

### 2.	알고리즘 통합 및 최적화
IMLP는 단일 모델의 한계를 극복하기 위해 16종 이상의 머신러닝 및 딥러닝 모델을 상호 보완적으로 활용하는 병렬 학습 구조를 채택하였습니다. 이 통합 엔진은 복잡한 재료 데이터에 내재된 문제를 효과적으로 보정하고, 다양한 조건에서 신뢰성 있는 예측 결과를 도출합니다.

### 3.	전주기 AI 기반 설계 및 분석 시스템
본 플랫폼은 소재 연구의 전주기를 포괄하는 연속적인 AI 주도형 데이터 파이프라인을 제공하며, 실험 데이터뿐만 아니라 시뮬레이션 및 문헌 데이터를 통합 처리합니다. 소재 탐색은 아래와 같은 4단계 흐름을 통해 자동화됩니다.
```
Data Standardization (표준화) → Prediction (예측) → Optimization (최적화) → Visualization (시각화)
```


## 파일 구성
bash
```
 project/
│
├── 5-Fold Cross Validation with Hold-Out Dataset .ipynb
├── 6-Fold Cross Validation.ipynb
├── 8-Fold Cross Validation with Hold-Out Dataset.ipynb
├── 9-Fold Cross Validation.ipynb
├── HRS.ipynb
├──Leave-one-out Cross Validation.ipynb
├──phosphor data.csv
└── README.md
```

## 설치 및 환경 설정
필수 라이브러리 설치
```
pip install numpy scikit-learn matplotlib
```

## 실행 방법

1. 저장소 클론
```
git clone https://github.com/yourname/repo
cd repo
```

2. Notebook 실행
```
jupyter notebook
```

3. 원하는 코드 오픈 후 셀을 순차적으로 실행

4. 결과로 각 Fold의 성능과 평균 R², MSE가 출력됨

## 출력 지표

Notebook에서는 아래와 같은 최종 평균 성능 지표를 제공합니다:

- MSE_train_mean

- R2_train_mean

- MSE_val_mean

- R2_val_mean


## 모델 평가 흐름
```
flowchart TD
A[Load Data] --> B[Create 6 Folds]
B --> C[Train Model per Fold]
C --> D[Predict Train/Validation]
D --> E[Calculate R² & MSE]
E --> F[Aggregate Results]
F --> G[Output Mean Metrics]
```

## 레퍼런스
Lee, J.-W., Park, C., Lee, B.D., Park, J., Goo, N.H., & Sohn, K.-S. A machine-learning-based alloy design platform that enables both forward and inverse predictions for thermo-mechanically controlled processed (TMCP) steel alloys.

## 라이선스
이 저장소의 코드는 MIT 라이선스를 따릅니다.
