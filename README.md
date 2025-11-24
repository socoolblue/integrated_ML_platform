# Integrated_ML_platform
이 코드는 그룹 기반 6‑Fold 교차검증(Leave‑One‑Group‑Out)으로 여러 회귀 모델의 일반화 성능을 비교하는 실험을 재현합니다.
>  핵심 포인트
> - 입력 CSV를 읽어 X(특징)와 Y(다중 타깃 2개) 로 분리
> - 그룹 단위로 데이터를 6개 Fold로 나누어 Leave‑One‑Group‑Out(logo) CV 수행
> - 각 모델에 대해 **Train/Validation MSE, R²** 평균을 출력
> - 재현 및 확장에 용이하도록 **한 파일 내 다수의 모델**을 동일 프로토콜로 평가

## 데이터 형식
- CSV 경로: 코드 내 `'Input_data_path'` **문자열을 실제 CSV 경로**(예: `'./data/dataset.csv'`)로 바꿉니다.
- 데이터 배열: `xy = np.loadtxt(<CSV_PATH>, delimiter=',', dtype=np.float32)` 로 읽은 뒤 `xy.reshape(-1, 18)`을 수행합니다.
- **특징(X)**: 마지막 2개 열을 제외한 모든 열 → `x_data = xy_data[:, :-2]`
- **타깃(Y)**: **마지막 2개 열** → `y_data = xy_data[:, -2:]` (다중 출력 회귀)
> 열 개수(여기서는 18)와 **타깃 2열** 가정은 노트북에 포함된 기본값입니다. 데이터가 다르면 **`reshape()` 과 타깃 분할 인덱스**를 맞춰 수정해야 합니다.
---
## 교차검증 전략
- **사용 전략:** LeaveOneGroupOut (LOGO)
- **그룹 라벨:** 코드 내 `groups = np.full((N), 5)` 와 `cut_data = 912` 를 이용해 **연속 구간을 동일 크기 그룹**으로 나눕니다.
  - `for i in range(int(len(groups)/cut_data)):`
    `groups[i*cut_data:(i*cut_data)+cut_data] = i`
  - 데이터 길이에 맞게 `cut_data` 를 조정하거나, **직접 생성한 그룹 라벨**(예: 배치/실험일자/시편ID)을 `groups` 에 할당할 수 있습니다.
---
## 🤖 포함된 회귀 모델
아래 모델들이 LOGO‑CV 프로토콜로 평가됩니다.
- `ARDRegression`
- `AdaBoostRegressor`
- `Bay_Reg`
- `GaussianProcessRegressor`
- `GradientBoostingRegressor`
- `GradientBoosting_Regressor`
- `KNeighborsRegressor`
- `KernelRidge`
- `Lasso`
- `LinearRegression`
- `MultiOutputRegressor`
- `PLSRegression`
- `RandomForestRegressor`
- `Ridge`
- `SVR`
- `XGBRegressor`
> 다중 타깃 지원이 필요한 경우 `MultiOutputRegressor` 래퍼를 함께 사용합니다.
**평가 지표**
- **R²** (`sklearn.metrics.r2_score`, `multioutput='variance_weighted'`)
- **MSE** (`sklearn.metrics.mean_squared_error`, `multioutput='uniform_average'`)
- **6개 Fold 평균**(Train/Validation) 지표를 `print(MSE_tr/6, r2_tr/6, MSE_val/6, r2_val/6)` 형태로 출력합니다.
---
##  환경 구성
```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\Scripts\activate
pip install numpy scikit-learn matplotlib xgboost
pip install tensorflow-cpu  
```
> 노트북에 `%matplotlib inline` 매직이 포함되어 있어 Jupyter 환경에서 바로 그래프를 볼 수 있습니다.
---
##  실행 방법
1. **CSV 경로 지정:** 노트북의 `'Input_data_path'` 문자열을 실제 파일 경로로 교체
2. **(선택) 그룹 설정:** `cut_data` 를 데이터 크기에 맞게 조정하거나 `groups` 배열을 직접 정의
3. Jupyter에서 **Run All** 실행
4. 콘솔 출력에서 각 모델의 **Train/Val MSE, R² 평균** 확인
---

##  라이선스
연구 재현을 위해 자유롭게 사용하시되, 데이터/코드의 2차 배포 정책은 소속 연구실 규정을 우선합니다.
