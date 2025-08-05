# **풍력발전기 블레이드 결함 탐지 솔루션 개발**
| 항목             | 내용                                                                 |
|------------------|----------------------------------------------------------------------|
| 프로젝트 기간     | 2022.11 – 2024.06                                                    |
| 참여 인원        | 4명                                                                   |
| 🔗 Repository       | [View on GitHub](https://github.com/sbinhigher/image_labeling_project) |
## 🔍 프로젝트 분류  
`이미지 처리(Image Processing)` · `이미지 객체 탐지(Object Detection)` · `데이터 라벨링(Data Labeling)`
## 🙋 역할  
- 이미지 객체 탐지 모델링 및 프로젝트 매니징 총괄  
- 현장성과 정확도를 모두 반영한 진단 기준 수립 주도
## 📂 프로젝트 배경
- 드론으로 촬영된 블레이드 이미지를 **전사 수작업 검수**하느라 시간이 과도하게 소요됨  
- **엔지니어별 결함 판단 기준 상이**로 인해 검사 정확도와 신뢰도에 문제 발생
## 💡 문제 해결 방법
1. **결함 유형 및 위험도 레벨에 대한 기준 정립**  
2. **자율주행 드론**을 활용해 블레이드 전면 이미지 수집  
3. 이미지 기반 **객체 탐지 모델(YOLOv7)** 구축으로 자동 진단 시스템화  
4. Ground Truth를 기반으로 한 평가체계로 진단 정확도 정량화
## 🚀 목표 및 성과
| 항목 | 기존 | 개선 | 성과 |
|------|-----------|------------|------|
| ⏱️ 진단 소요 시간 | 이미지당 평균 96.42초 | 이미지당 평균 5.99초 | **진단 시간 93.8% 단축** |
| 📏 위험도 기준 | 주관적・불일치 기준 | 정량 기준 수립 | **표준화된 위험도 분류체계 확립** |
| 🎯 진단 정확도 | 측정 불가 | Ground Truth 기반 평가 | **재현율(Recall) 0.9 달성** |
## 🛠️ 사용기술 및 툴(tool)

<p>
  <img src="https://img.shields.io/badge/Python-3776AB?style=flat&logo=python&logoColor=white"/>
  <img src="https://img.shields.io/badge/OpenCV-5C3EE8?style=flat&logo=opencv&logoColor=white"/>
<a href="https://github.com/WongKinYiu/yolov7">
  <img src="https://img.shields.io/badge/YOLOv7-black?style=flat&logo=github&logoColor=white"/>
</a>
  <img src="https://img.shields.io/badge/NumPy-013243?style=flat&logo=numpy&logoColor=white"/>
  <img src="https://img.shields.io/badge/Labelme-FFB000?style=flat&logo=OpenCV&logoColor=white"/>
  <img src="https://img.shields.io/badge/GCP-4285F4?style=flat&logo=googlecloud&logoColor=white"/>
</p>

## 📌 Pain Point & 개선 방안
> 
> ### Pain Point 1: 대용량 고해상도 이미지 데이터 처리 어려움
> - 48MP 고해상도 이미지로 인해 데이터 처리 및 저장이 무거웠음  
> - 라벨링 작업에 소요되는 시간과 검수 부담이 큼
> 
>> **해결 방법**  
>> - 최적화된 이미지 리사이징 (0.5~0.8배, 0.75배 최종 선정) 및 정방형 크기로 데이터 경량화  
>> - Instance Segmentation 방식 채택으로 결함 특성 세분화 및 라벨링 품질 향상  
>> - 외부 인력과 엔지니어의 3회 검수 및 피드백 체계 구축

> ### Pain Point 2: 일부 결함 신뢰도 저하 및 결함 예측 데이터 부재
> - 다발성 결함 탐지 시 신뢰도가 낮음  
> - SCADA 로그 데이터 권한 문제로 결함 발생 예측에 어려움 존재
> 
>> **해결 방법**  
>> - ‘다발성 결함’ 카테고리 신설로 기준 명확화  
>> - SCADA 데이터 협조 불가에 따라 이미지 기반 탐지 솔루션 고도화에 집중  
>> - YOLOv7-seg 모델 기반 하이퍼파라미터 튜닝 및 이미지 증강 적용

> ### Pain Point 3: 비라벨링 이미지 데이터 활용 및 데이터 분할 문제
> - 라벨링 되지 않은 이미지 데이터의 활용 방안 마련 필요  
> - 효율적인 Train-Validation-Test 데이터셋 분할 필요
> 
>> **해결 방법**  
>> - 비라벨링 이미지셋에서 20% 샘플링 활용해 모델 성능 개선 시도  
>> - 각 호기 및 파트별로 균등하게 샘플링하여 데이터셋 분할 (8:1.5:0.5)
