# 6-Fold Cross Validation for Regression Models

### Lasso Regression & PLS Regression Evaluation Notebook

이 저장소는 회귀 모델(Lasso Regression, PLSRegression)의 6-Fold Cross Validation 실험을 수행하고 모델 성능(R², MSE)을 평가하는 Jupyter Notebook을 포함합니다.
Notebook 기반으로 모델의 일반화 성능을 분석하고 비교하는 데 목적이 있습니다.

 ## 주요 기능 (Features)

6-Fold Cross Validation 수행

Lasso Regression 모델 학습 및 검증

PLSRegression 모델 학습 및 검증

Fold별 R², MSE 계산

평균 성능 지표 산출

학습 및 검증 결과 시각화

## 파일 구성
bash
```
 project/
│
├── 6-Fold Cross Validation.ipynb
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

3. 6-Fold Cross Validation.ipynb 오픈 후 셀을 순차적으로 실행

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

## 라이선스
필요시 MIT License 등으로 오픈소스화 가능합니다.
