# Exoplanet Classification Project


## 프로젝트 소개

NASA Kepler 우주망원경 관측 데이터를 이용하여 외계행성 후보 신호와 가짜 신호(False Positive)를 분류하는 머신러닝 프로젝트이다.

## 데이터셋

- Dataset: NASA Kepler Exoplanet Search Results
- Source: Kaggle
- 문제 유형: Binary Classification

## 사용 모델

- Logistic Regression (Baseline)
- Random Forest (Proposed Model)

## 성능 결과

| Model | Accuracy | F1-score | ROC-AUC |
|---------|---------|---------|---------|
| Logistic Regression | 0.6717 | 0.6912 | 0.6766 |
| Random Forest | 0.8552 | 0.8493 | 0.8554 |

## 사용 라이브러리

- pandas
- numpy
- scikit-learn
- matplotlib
- seaborn

## 실행 방법

```bash
pip install -r requirements.txt
python machine_learning_project.py
```

## 프로젝트 구조

```text
.
├── data/
│   └── exoplanets.csv
├── machine_learning_project.py
├── requirements.txt
└── README.md
```

## 참고사항

본 프로젝트는 Google Colab 환경에서 개발되었습니다.
.ipynb 파일을 GitHub에 업로드했을 때 렌더링 오류가 발생하여, 동일한 코드를 .py 파일 형식으로 변환하여 제출하였습니다.

코드는 기존 Colab 노트북의 실행 순서를 그대로 따르며, 데이터셋은 data/ 폴더에 포함되어 있습니다.
