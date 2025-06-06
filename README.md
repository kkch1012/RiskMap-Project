# RiskMap-Project(교통사고 위험 분석 프로젝트)
서울시 교통사고 데이터를 기반으로 기상, 인구, 교통 데이터를 병합하여 사고 위험도를 분석 및 시각화하는 프로젝트입니다.

## 프로젝트 환경 및 버전
- Python 3.11
- Pandas 2.x
- Scikit-learn 1.x
- Matplotlib / Seaborn
- Jupyter Notebook
- OS: Windows 10

## 데이터 설명

### /raw_data 디렉토리
- `거주인구.csv` : 분기별 자치구별 거주 인구 데이터 ( 2008. 1/4 ~ 2025. 1/4)
- `서울시 읍면동마스터 정보.csv` : 행정동별 코드, 시도 명칭
- `교통사고_현황2005.csv` : 교통사고 자치구별 월별 데이터 ( 2005.01 ~ 2024.12)
- `교통사고+현황(사고유형별).csv` : 교통사고 자치구별 사고유형별 데이터 (1988 ~ 2023)
- `기상개황.csv` : 기온, 강수량, 풍속 등 월별 기상 데이터(2005.01 ~ 2023.12)
- `서울시 행정동별 지하철 총 승차 승객수 정보.csv` : 행정동별 행정동ID 지하철 승차 승객수(2021.11.30 ~ 2025.04.06)

### /first_processing_data 디렉토리
- `거주인구.csv` : 월별 자치구별 거주 인구 데이터 전처리 파일(2008.01 ~ 2025.03)
- `교통사고(사고유형별).csv` : 사고유형별 교통사고 데이터 전처리 파일(2005 ~ 2023)
- `교통사고(월별).csv` : 자치구별 월별 사고 데이터 원본 ( 2005.01 ~ 2024.12)
- `교통사고(월별)_전처리.csv` : 전처리된 월별 사고 데이터 ( 2005.01 ~ 2024.12)
- `기상_전처리.csv` : 결측치 및 이상치 보정된 기상 데이터 ( 2005.01 ~ 2023.12)
- `대중교통_정제.csv` : 정제된 대중교통(버스/지하철) 이용량 데이터 ( 2021.11 ~ 2025.04)
- `버스승객수_교통사고_통합_합본.csv` : 버스승객수와 사고 데이터를 병합한 파일 ( 2017.01 ~  2025.04)
- `자치구별_지하철_승객수_합계.csv` : 자치구 기준 지하철 승차 승객수 합계 데이터 ( 2021.11 ~ 2025.04)
- `감전사고_데이터_수정본.csv` : 감전사고 원본 데이터 수정본 ( 2013.01 ~ 2025.03)
- `감전사고_전처리.csv` : 감전사고 데이터 전처리 파일 ( 2013.01 ~ 2025.03)
- `지하철_유동인구.csv` : 자치구별 지하철 승차 승객수 월별 합계 데이터 ( 2021.11 ~ 2025.04)

### /merged_data 디렉토리
- `인구_유동인구_병합.csv` : 거주인구와 지하철 유동인구 병합 데이터( 2008.01 ~ 2025.04)
- `최종_병합_데이터.csv` : 인구_유동인구_병합 데이터와 기상개황 데이터 병합 ( 2005.01 ~ 2025.04)
- `버스_사고_보정.csv` : 버스승객수와 사고 데이터를 병합한 파일 ( 2017.01 ~ 2025.04)
- `버스사고_보정_연월수정.csv` : 버스_사고_보정 수정본 ( 2017.01 ~ 2025.04)
- `최종_통합_데이터.csv` : 최종_병합 데이터와 버스사고_보정 수정본 병합 ( 2005.01 ~ 2025.04)
- `최종_통합_대중교통포함.csv` : 최종_통합_데이터와 대중교통 데이터 병합 ( 2005.01 ~ 2025.04)
- `최종_통합_정제완료.csv` : 최종_통합_대중교통포함 전처리 데이터 ( 2005.01 ~ 2025.03)
- `교통사고_갱신된_통합_데이터.csv` : 최종_통합_정제완료 데이터와 교통사고(월별) 전처리 수정본 병합 ( 2005.01 ~ 2025.03)

### /regression_data 디렉토리
- `선형회귀.csv` : 교통사고_갱신된_통합_데이터의 23,24년도의 데이터로 구마다 따로 선형회귀 학습 후 2008년부터 2022년까지의 구마다 따로 유동인구 예측한 데이터 ( 2005.01 ~ 2025.03)
- `랜덤포레스트.csv` : 같은 방식으로 랜덤포레스트 모델로 예측 ((대중교통,버스,지하철) 3개로 예측 하기 or 3개를 합쳐서 유동인구로 예측하기)
- `랜덤포레스트_교차검증.csv` : 랜덤포레스트 예측 K-Fold 교차검증으로 성능 평가
- `다항회귀.csv` : 같은 방식으로 다항회귀 모델로 예측 ((대중교통,버스,지하철) 3개로 예측 하기 or 3개를 합쳐서 유동인구로 예측하기)
- `다항회귀_교차검증.csv` : 다항회귀 예측 K-Fold 교차검증으로 성능 평가
- 
## 데이터 출처
- [서울열린데이터광장](https://data.seoul.go.kr/)
- [공공데이터포털](https://www.data.go.kr/)

## 주요 분석 내용
- 상관관계 분석: 인구, 교통, 기상 요인과 교통사고, 여러 다양한 인명 사고 간 관계 파악
- 결측값 처리: 선형회귀 기반 예측으로 일부 누락값 보정
- 군집화 분석: 자치구별 위험도 유형 분류
- PCA: 고차원 상관관계 데이터를 2D로 시각화
- 시계열 분석 및 예측: 미래 교통사고 발생 추정

## 결과 활용
- 자치구별 사고 위험도 지수 시각화
- 향후 특정 조건(기상, 인구 등)에서 사고 위험이 높은 지역 예측
- 정책 수립, 캠페인 타겟 선정 등에 활용 가능
