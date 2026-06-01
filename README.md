# Exoplanet Classification Project

## 프로젝트 개요

본 프로젝트는 NASA Kepler 우주망원경이 관측한 데이터를 활용하여 관측 신호가 실제 외계행성 후보인지(False Positive가 아닌지) 자동으로 분류하는 머신러닝 모델을 구축하는 것을 목표로 한다.

원본 데이터셋의 레이블은 다음과 같이 3개로 구성되어 있다.

- CONFIRMED
- CANDIDATE
- FALSE POSITIVE

본 프로젝트에서는 문제를 단순화하여 다음과 같은 이진 분류(Binary Classification) 문제로 재정의하였다.

- Class 1 : CONFIRMED + CANDIDATE (외계행성 후보 신호)
- Class 0 : FALSE POSITIVE (가짜 신호)

---

## 데이터셋

### 데이터 출처

- Kaggle NASA Kepler Exoplanet Search Results Dataset
- https://www.kaggle.com/datasets/nasa/kepler-exoplanet-search-results

### 사용 Feature

본 프로젝트에서는 총 10개의 주요 Feature를 사용하였다.

- koi_period
- koi_duration
- koi_depth
- koi_prad
- koi_insol
- koi_model_snr
- koi_steff
- koi_slogg
- koi_srad
- koi_kepmag

### 결측치 처리

결측치는 각 Feature의 중앙값(Median)으로 대체하였다.


---

## 데이터 분할

훈련 데이터와 테스트 데이터를 다음과 같이 분할하였다.

- Train : 80%
- Test : 20%

또한 클래스 비율 유지를 위해 Stratified Split을 적용하였다.

---

## 사용 모델

### 1. Baseline Model

- Logistic Regression

선형 모델을 기준선(Baseline)으로 사용하여 성능 비교를 수행하였다.

### 2. 제안 모델

- Random Forest Classifier

비선형 관계를 학습할 수 있는 앙상블 모델(Random Forest)을 사용하였다.

---

## 하이퍼파라미터 최적화

Random Forest 모델에 대해 GridSearchCV를 이용하여 최적의 하이퍼파라미터를 탐색하였다.

탐색 범위

```python
{
    "n_estimators": [100, 200],
    "max_depth": [10, 20]
}
```

최적 파라미터

```python
{
    "n_estimators": 200,
    "max_depth": 10
}
```

---

## 평가 지표

다음 평가 지표를 사용하였다.

- Accuracy
- F1-score
- ROC-AUC

---

## 실험 결과

| 모델 | Accuracy | F1-score | ROC-AUC |
|--------|--------|--------|--------|
| Logistic Regression | 0.6717 | 0.6912 | 0.6766 |
| Random Forest | 0.8552 | 0.8493 | 0.8554 |

Random Forest 모델이 모든 평가 지표에서 Logistic Regression보다 우수한 성능을 보였다.

---

## Feature Importance

Random Forest Feature Importance 분석 결과 중요도가 높은 변수는 다음과 같다.

1. koi_prad
2. koi_period
3. koi_insol
4. koi_depth
5. koi_duration

행성의 크기와 식(Transit) 현상 관련 특성이 외계행성 후보 분류에 중요한 영향을 미치는 것으로 확인되었다.


---

## 실행 환경

- Python 3.10+
- pandas
- numpy
- matplotlib
- seaborn
- scikit-learn

---

## 설치 방법

```bash
pip install -r requirements.txt
```

---

## 실행 방법

```bash
python machine_learning_project.py
```

실행 시 다음 과정이 수행된다.

1. 데이터 로드
2. 결측치 처리
3. 데이터 분할
4. Logistic Regression 학습 및 평가
5. Random Forest 학습 및 평가
6. GridSearchCV 하이퍼파라미터 탐색
7. Feature Importance 시각화

---

## 참고사항

본 프로젝트는 Google Colab 환경에서 개발되었습니다.
.ipynb 파일을 GitHub에 업로드했을 때 렌더링 오류가 발생하여, 동일한 코드를 .py 파일 형식으로 변환하여 제출하였습니다.

코드는 기존 Colab 노트북의 실행 순서를 그대로 따르며, 데이터셋은 data/ 폴더에 포함되어 있습니다.
