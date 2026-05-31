# Exoplanet Classification Project

## 프로젝트 개요
이 프로젝트는 케플러 행성 후보 데이터(`data/cumulative.csv`)를 사용하여
행성 여부를 분류하는 머신러닝 모델을 학습하고 평가하는 프로젝트입니다.

## 데이터셋
- `data/cumulative.csv`에 포함되어 있음
- 코드에서 상대경로로 읽도록 설정되어 있습니다

## 파일 구조

.
├── data/
│ └── cumulative.csv # 데이터셋
├── Machine_Learning_Project.py # 메인 코드
├── README.md
└── requirements.txt # 필요한 패키지


## 설치 방법
Python 3.8 이상에서 아래 명령어로 패키지 설치:

```bash
pip install -r requirements.txt
실행 방법
프로젝트 실행:
python Machine_Learning_Project.py
필요하면 코드 안의 함수나 모듈 단위로 실행 가능

참고 사항

본 프로젝트는 Google Colab 환경에서 개발되었습니다.
.ipynb 파일을 GitHub에 업로드했을 때 렌더링 오류가 발생하여, 동일한 코드를 .py 파일 형식으로 변환하여 제출하였습니다.

코드는 기존 Colab 노트북의 실행 순서를 그대로 따르며, 데이터셋은 data/ 폴더에 포함되어 있습니다.
