# 📈SKN16-2nd-2Team ( 멕시코 학생 학업 중퇴 예측)
SKN 16기 2차 단위프로젝트

## 📝중고등학생 중퇴 예측
**기간:** 2025.08.04 ~ 2025.08.05  
**팀원:** 신지윤, 이경은, 이광식, 진세현, 허원준  

---

## 📋1. 프로젝트 개요
본 프로젝트는 학생들의 학업 및 생활 데이터를 기반으로 학교 중퇴 가능성을 예측하는 머신러닝, 딥러닝 모델을 개발하는 것을 목표로 한다.  
이를 통해 실제 교육 현장에서 조기 개입이 가능하도록 지원하며, 맞춤형 상담 및 지원 정책 수립에 기여할 수 있다.

---

## ✔️2. 프로젝트 배경
학생 중퇴는 개인의 학업 단절뿐만 아니라 장기적인 사회적 손실로 이어지는 주요 교육 문제 중 하나이다.  
<img width="492" height="685" alt="뉴스" src="https://github.com/user-attachments/assets/efbc34bf-0bb7-4920-a711-00562034ac48" />

위 멕시코 뉴스와 같이 학업 중퇴 현상은 **다양한 요소가 복합적으로 상호작용한 결과**이다. 

기존의 사후적 관리 방식은 중퇴 예방에 한계가 있으며, 이에 따라 **기존 요소 분석에 따른 조기 예측과 선제적 개입의 필요성**이 대두되고 있다.  
본 프로젝트는 학습 데이터 분석을 통해 중퇴 가능성을 사전에 식별함으로써, 효과적인 교육 지원 정책 마련을 목표로 한다.

---

## 💡3. 기대 효과
- **관리 효율성 향상:** 학생 관리 시스템 자동화 및 교육 현장의 의사결정 효율성 증대  
- **조기 개입 강화:** 중퇴 위험군 학생을 사전에 예측하여 맞춤형 상담 및 지원 프로그램 제공  
- **교육 정책 혁신:** 데이터 기반 근거를 활용한 중퇴 예방 정책 수립 지원  

---

## 📖4. 데이터셋 소개
- **데이터 출처:** [National Survey on School Dropout (Kaggle)](https://www.kaggle.com/datasets/renecardoso/national-survey-on-school-dropout/data)
- **데이터 크기:**  파일 df02_TipoModulo / 10,602 × 54
- **특성 수:** 총 67개 (범주형/수치형 혼합) → 분석에 사용된 컬럼 54개
- **가상 데이터 생성:**  가상으로 데이터 생성하여 새로운 학생 데이터 분석에 적용
- **가상 데이터 크기:** 300 x 52
- **가상 데이터 특성 수:** 총 51개 (범주형/수치형 혼합) → 중요 변수만 사용하여 생성
---



## 🛠️5. 분석 절차


### 프로젝트 구조


```
📦 SKN16-2nd-2Team
│
├── 📄 README.md                  # 프로젝트 개요 및 실행 방법
├── 📄 requirements.txt           # Python 패키지 의존성
├── 📄 .gitignore                 # Git 제외 파일
│
├── 📂 data                       # 데이터 관리 폴더
│   ├── raw                       # 원본 데이터
│   │   ├── dropout_survey.csv
│   │   └── virtual_student_data.csv
│   ├── processed                 # 전처리된 데이터
│   │   ├── train.csv
│   │   └── test.csv
│   └── external                  # 외부 참고 데이터 (예: 심리 요인 관련 데이터)
│
├── 📂 notebooks                  # Jupyter Notebook 폴더
│   ├── 01_EDA.ipynb              # 데이터 탐색 및 시각화
│   ├── 02_Preprocessing.ipynb    # 전처리 및 피처 엔지니어링
│   ├── 03_Modeling.ipynb         # 머신러닝/딥러닝 모델 학습
│   ├── 04_Evaluation.ipynb       # 모델 평가 및 비교
│   └── 05_Streamlit_Demo.ipynb   # Streamlit UI 테스트
│
├── 📂 src                        # 프로젝트 핵심 소스코드
│   ├── init.py
│   ├── data_preprocessing.py     # 데이터 전처리 모듈
│   ├── feature_selection.py      # 변수 선택 및 중요도 분석
│   ├── model_training.py         # 모델 학습 및 저장
│   ├── model_evaluation.py       # 모델 성능 평가
│   ├── utils.py                  # 공통 유틸리티 함수
│   └── inference.py              # 모델 로드 및 예측 모듈
│
├── 📂 models                     # 학습된 모델 저장
│   ├── gradient_boosting.pkl
│   ├── random_forest.pkl
│   └── logistic_regression.pkl
│
├── 📂 streamlit_app              # Streamlit 배포 관련 폴더
│   ├── app.py                    # 메인 Streamlit 실행 파일
│   ├── components                # UI 컴포넌트
│   │   ├── student_list.py
│   │   ├── student_detail.py
│   │   └── riskvisualization.py
│   ├── pages                     # Streamlit 멀티페이지 관리
│   │   ├── 1학생별위험도분석.py
│   │   ├── 2학생데이터관리.py
│   │   └── 3모델성능확인.py
│   └── assets                    # 이미지 및 아이콘 리소스
│       ├── logo.png
│       └── style.css
│
├── 📂 reports                    # 분석 보고서 및 문서
│   ├── figures                   # 분석 시각화 결과
│   │   ├── correlation_heatmap.png
│   │   ├── feature_importance.png
│   │   └── model_comparison.png
│   ├── presentation              # 발표 자료
│   │   └── SKN16-2nd-2Team_PPT.pptx
│   └── final_report.md           # 최종 프로젝트 보고서
│
└── 📂 tests                      # 테스트 코드
    ├── test_preprocessing.py
    ├── test_model_training.py
    └── test_inference.py
    
```
    

    


### 🔧기술 스택
<img src="https://img.shields.io/badge/GIT-F05032?style=for-the-badge&logo=git&logoColor=white"/>  <img src="https://img.shields.io/badge/GitHub-181717?style=for-the-badge&logo=github&logoColor=white"/>  <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white"/>  <img src="https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white"/>
  <img src="https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white"/>  <img src="https://img.shields.io/badge/Numpy-013243?style=for-the-badge&logo=numpy&logoColor=white"/>  <img src="https://img.shields.io/badge/Matplotlib-11557C?style=for-the-badge&logo=matplotlib&logoColor=white"/>  <img src="https://img.shields.io/badge/Seaborn-9AABA6?style=for-the-badge&logo=seaborn&logoColor=white"/>  <img src="https://img.shields.io/badge/LogisticRegression-7C4DFF?style=for-the-badge"/>  <img src="https://img.shields.io/badge/RandomForest-43A047?style=for-the-badge"/>  <img src="https://img.shields.io/badge/GradientBoost-0460EB?style=for-the-badge"/>  <img src="https://img.shields.io/badge/Plotly-3F4F75?style=for-the-badge&logo=plotly&logoColor=white"/>  <img src="https://img.shields.io/badge/Scikit--learn-F7931E?style=for-the-badge&logo=scikit-learn&logoColor=black"/>    <img src="https://img.shields.io/badge/st--aggrid-2C8EBB?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/pickle-000000?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/warnings-FD6C24?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/os-232F3E?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/time-0E7490?style=for-the-badge"/>
  <img src="https://img.shields.io/badge/platform-3D4451?style=for-the-badge"/>


### 5.1 EDA 및 전처리
- **데이터 구조 확인:** 변수명, 데이터 타입, 결측치 여부 점검  
- **분석 대상 데이터 선정:** 학습 등급이 4~7 구간에 해당하는 학생만 필터링  
- **시각화 분석:** 변수별 중요도 시각화를 통해 상위 15개 변수 선정 (막대 그래프)  
<img width="1004" height="641" alt="스크린샷 2025-08-05 155525" src="https://github.com/user-attachments/assets/14c50658-c9fb-449e-83de-bd3323db02c6" />

**데이터 전처리**  
- 결측치 처리: 값이 0인 경우 무응답으로 간주하고 결측치 처리  
- 불필요 변수 제거: 예측에 기여하지 않는 변수 제거  

**변수 정제 및 상관 분석**  
- 상관 분석: 전체 변수와 타깃 변수 간 상관계수 분석  
- 변수 제거: 상관성이 낮거나 중복되는 변수 제거 후 상관행렬 재확인  
- 주요 변수 선정: 피처 중요도 분석을 통해 주요 변수 선정  
<img width="867" height="576" alt="스크린샷 2025-08-05 170258" src="https://github.com/user-attachments/assets/16af2f33-afb8-4dfe-936d-dd735ad4ed2e" />

---

### 📊5.2 머신러닝 모델링
<img width="939" height="605" alt="스크린샷 2025-08-05 155346" src="https://github.com/user-attachments/assets/78e30d29-358a-4fb5-9561-9aef69db8d28" />

| 모델                | Accuracy | Precision | Recall  | F1     | AUC    |
|---------------------|----------|-----------|---------|--------|--------|
| Logistic Regression | 0.9793   | 0.9200    | 0.8679  | 0.8932 | 0.9946 |
| Random Forest       | 0.9807   | 0.8869    | 0.9245  | 0.9053 | 0.9906 |
| Gradient Boosting   | 0.9844   | 0.9242    | 0.9198  | 0.9220 | 0.9968 |

✅ **최종 선정 모델:** Gradient Boosting (F1: 0.9220)  
- 모든 지표에서 균형 잡힌 성능  
- 특히 F1-Score와 AUC에서 최고 성능 기록  

---

### 💻5.3 Streamlit 구현




- 메인 화면: 학생별 중퇴 가능성을 위험도로 나누어 시각화
<img width="1418" height="405" alt="11" src="https://github.com/user-attachments/assets/48e35900-adb7-4538-8248-c5b982cd407b" />
<img width="1413" height="797" alt="22" src="https://github.com/user-attachments/assets/e11c70f8-d520-4471-b23d-d5e4b75b173c" />




- 학생 리스트: 학생 리스트, 위험도별 학생 확인 가능
  
![111](https://github.com/user-attachments/assets/a4625248-482e-4452-ba71-0e6cf453f703)

- 학생 클릭하여 개별 예측 화면으로 이동 가능
  
![5](https://github.com/user-attachments/assets/63cf6722-941e-48e9-b145-9a4abb14d5e6)





- 학생 데이터 관리:
![심리상태변화](https://github.com/user-attachments/assets/091a313e-88bc-4850-889c-b10be174ad3e)


<img width="983" height="772" alt="14" src="https://github.com/user-attachments/assets/cbc35e15-74eb-45b8-9096-da5824d89910" />



-최종 streamlit 구현 화면

![project2_2](https://github.com/user-attachments/assets/97028d17-f97a-46ba-9c8c-b7cae8056cfa)

 


---

## ✒️6. 결론

본 프로젝트는 기존에 있던 데이터 기반 분석을 통해 가상 데이터셋을 만들어 학생 중퇴 가능성을 예측한다.
이를 활용해 교육 현장에서 조기 개입을 가능하게 하여 학생들의 실제 학업 중퇴율을 낮출 수 있다. 
위에서 중퇴와 관련된 중요 변수를 살펴보면, *절망감, 스트레스, 사회화문제, 우울증* 등이 가장 큰 요소로 작용하고 있다.
이에 따라 학생 상담과 조사를 통해 위 요소를 고려하여 학업 스트레스와 정신적인 문제를 해소하는 방법을 찾을 수 있다. 
간단한 해소 방법으로 *운동, 식이요법, 인지행동치료, 긍정심리* 등이 있다. 이를 통해 학생들의 부정적인 심리를 줄여줄 수 있다. 



머신러닝 모델 중 Gradient Boosting이 가장 우수한 성능을 보였으며, 향후 실제 교육 현장에 적용 시 학생 관리 효율성과 중퇴 예방 정책 수립에 기여할 것으로 기대된다.
