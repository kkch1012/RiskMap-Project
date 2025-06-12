# RiskMap-Project(교통사고 위험 분석 프로젝트)
서울시 교통사고 데이터를 기반으로 기상, 인구, 교통 데이터를 병합하여 사고 위험도를 분석 및 시각화하는 프로젝트입니다.

## 프로젝트 환경 및 버전

- Python 3.12.7
- OS: Windows 10
- Jupyter Notebook

### 사용 라이브러리
- Pandas 2.2.2
- NumPy 1.26.4
- Matplotlib 3.9.2 / Seaborn 0.13.2
- GeoPandas 1.0.1
- Shapely 2.1.1
- Folium 0.19.4
- Scikit-learn 1.5.1

## 데이터 설명

### /data/raw_data 디렉토리
- `Resident_population.csv` : 분기별 자치구별 거주 인구 데이터 (2008. 1/4 ~ 2025. 1/4)
- `Seoul_master_information.csv` : 행정동별 코드, 시도 명칭
- `Traffic_accident_month_2005.csv` : 교통사고 자치구별 월별 데이터 (2005.01 ~ 2024.12)
- `Traffic_accident_type.csv` : 교통사고 자치구별 사고유형별 데이터 (1988 ~ 2023)
- `Weather.csv` : 기온, 강수량, 풍속 등 월별 기상 데이터 (2005.01 ~ 2023.12)
- `Seoul_subway.csv` : 행정동별 지하철 승차 승객수 (2021.11.30 ~ 2025.04.06)
- `transportation.csv` : 행정동별 대중교통 총 승차 승객수 정보
- `Seoul_bus.csv` : 행정동별 버스 총 승차 승객수 정보
- `pedestrain.csv` : 보행자 사고 원본 데이터
- `hit_and_run.csv` : 뺑소니 사고 원본 데이터
- `bike.csv` : 자전거 사고 원본 데이터
- `Electric_shock_accident.xlsx` : 감전사고 원본 데이터
- `Disaster_Accident.csv` : 재난사고 데이터
- `fire_data.csv` : 화재사고 원본 데이터
- `weather_accident.csv` : 기상상태별 교통데이터
- `Traffic_accident_year_2005.csv` : 교통사고 현황 연도별 데이터 (2005~)
- `Traffic_accidents_vehicle.csv` : 차종별 교통사고 데이터
- `Resident_population_preprocessing.csv` : 거주인구, 유동인구 병합 전처리 데이터

### /data/first_processing_data 디렉토리
- `bike_processing.csv` : 자전거 사고 전처리 완료 데이터
- `Bus_accident_total_data_preprocessing.csv` : 버스사고 전처리 보정 데이터
- `population_average_2005_2023.csv` : 인구 연평균 전처리 데이터
- `Disaster_Accident_preprocessing.csv` : 재난사고 전처리 데이터
- `Electric_shock_accident_preprocessing.csv` : 감전사고 전처리 데이터
- `fire_tidy_cases.csv` : 화재사고 전처리 데이터
- `fire_count.csv` : 화재 소계 (방화, 실화, 기타불명 필터링)
- `hit_and_run_processing.csv` : 뺑소니 전처리 완료 데이터
- `pedestrain_processing.csv` : 보행자 전처리 완료 데이터
- `Resident_population_preprocessing_year_sum.csv` : 거주인구 연도별 합계
- `Resident_population_preprocessing.csv` : 월별 자치구별 거주 인구 전처리 데이터
- `Seoul_bus_preprocessing.csv` : 버스 이용량 전처리 데이터
- `Seoul_subway_dong.csv` : 자치구별 지하철 승객수 합계
- `Subway_move_people.csv` : 지하철 유동인구 월별 합계
- `Total_average_month.csv` : 인구 및 교통사고 월평균 데이터
- `Traffic_accident_month_preprocessing.csv` : 교통사고 월별 전처리 데이터
- `Traffic_accident_type_preprocessing.csv` : 교통사고 사고유형별 전처리 데이터
- `Traffic_accidents_filtered_metrics.csv` : 교통사고 인구10만/자동차1만대당 지표 추출 데이터
- `Traffic_accidents_multi_metric_tidy.csv` : 교통사고 지표 정제 데이터
- `Traffic_accidents_vehicle_tidy.csv` : 차량종류별 교통사고 데이터 전처리
- `Transportation_preprocessing_month.csv` : 대중교통 월별 전처리
- `transportation_processing.csv` : 대중교통 데이터 전처리 완료본
- `weather_tidy_data.csv` : 기상상태별 교통사고 초기 전처리
- `weather_metrics_no_fog.csv` : 안개 제거된 기상-사고 데이터
- `Weather_preprocessing.csv` : 기상 데이터 전처리 파일

### /data/merged_data 디렉토리
- `Basic_model.csv` : 기본 모델용 병합 데이터
- `Disaster_Electric_total_data.csv` : 감전사고 + 재난사고 병합 데이터
- `Bus_Accident_total_data_2017_2025.csv` : 버스+사고 병합 데이터 (2017~2025)
- `Bus_accident_total_data.csv` : 버스+사고 병합 데이터 (2005~2025)
- `Population_merged.csv` : 거주인구 + 지하철 유동인구 병합
- `Population_weather_merged.csv` : 인구 + 기상 병합
- `Total_data.csv` : 자치구 월 통합 데이터
- `Total_transportation_merged.csv` : 대중교통 포함 통합 데이터
- `Total_transportation_merged_preprocessing.csv` : 대중교통 포함 통합 데이터 전처리
- `Total_updated_data.csv` : 교통사고 갱신 통합 데이터
- `Accident_by_year_merged_hc.csv` : 연도별 보행자/자전거/뺑소니 사고 통합
- `merged_final.csv` : 기상상태/화재/차량용도별 교통사고 연합본
- `merged_result.csv` : 연 종합 데이터 통합본
- `merged_result_updated.csv` : 연 종합 데이터 + 기본 모델 전처리 병합본
- `merged_result_updated_last.csv` : 결측값 보정된 병합본
- `merged_result_with_metrics.csv` : 교통사고 월별 평균 데이터 → 연도별로 대체된 최종 병합본

### /data/regression_data 디렉토리
- `regression_final.csv` : 2005~2007 거주인구 선형회귀 보간 결과 (Accident_by_year_merged_hc 기반)
- `passerger_data.csv` : 최종 승객수 예측 데이터
- `passenger_data_2017_2023.csv` : 2017~2023 승객수 예측 결과
- `Basic_model_preprocessing.csv` : 기본 모델 입력 전처리 파일
- `new_model.csv` : 연 종합 데이터에서 2024~2026 선형회귀 예측 보간된 결과
- `new_model_with_fire.csv` : `화재_소계` 항목의 2024~2026 선형회귀 예측 포함
- `new_model_with_weather.csv` : 기상상태별 교통사고 항목의 2024~2026 예측 포함
- `new_model_final.csv` : 차량용도별 교통사고 항목의 2024~2026 예측 포함

### /data/map 디렉토리
- `HangJeongDong.geojson` : 서울시 자치구 경계 GeoJSON 파일

### /heatmaps 디렉토리
- `구별 히트맵` : 자치구별 시각화 히트맵 이미지 또는 결과 파일

### /result 디렉토리
- `서울시_자치구_위험지도_버전1.html` : 월별·자치구별 데이터로 모델링한 위험지수 지도 (버전 1)
- `서울시_자치구_위험지도_버전2.html` : 월별·자치구별 데이터로 모델링한 위험지수 지도 (버전 2)

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
