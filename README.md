# 허태희 포트폴리오

AI 전공을 기반으로 Python, 머신러닝·딥러닝, 생성형 AI 기술을 활용한 프로젝트를 수행했습니다.
추천 시스템, 컴퓨터 비전, 이미지 생성, XR 콘텐츠 등 다양한 AI 서비스 구현 경험을 보유하고 있으며, 모델 개발뿐 아니라 데이터 처리, 성능 평가, API 연동 및 배포 환경 구성까지 경험했습니다.

---

## 프로젝트

## 1. AI 도서 큐레이션 서비스

### 기간 | 2026.04 ~ 2026.05
### 역할 | 추천 파이프라인 성능 평가 · AI 서비스 배포 환경 구성

LLM 기반 사용자 의도 분석과 임베딩 검색, 리랭킹, 룰 기반 재정렬을 결합하여 사용자 취향과 상황에 맞는 도서를 추천하는 개인화 도서 추천 서비스입니다.

### 주요 수행 내용

* LLM 기반 사용자 의도 분류 및 질의 재작성 방식을 활용해 사용자의 추천 요청을 검색에 적합한 형태로 처리
* Dense 검색, BM25 검색, Lookup 검색 방식의 추천 결과를 비교하며 검색 방식별 특성과 성능을 분석
* 장르, 목적, 리뷰, 책장 정보 등을 반영하는 룰 기반 재정렬 로직의 영향도를 검증
* 추천 결과가 벡터 유사도에 의해 조기 제한되는 문제를 확인하고, 후보군을 확장하는 방식으로 평가 로직 개선
* 정성 평가 기준을 기반으로 질의 유형별 추천 결과를 분석하고 최적 추천 파이프라인 도출
* Kubernetes 환경에서 AI 서버, 백엔드, 프론트엔드, 임베딩 서버, 리랭커 서버, PostgreSQL, Qdrant 간 연결 구조 구성
* 서비스 상태 확인, API 통신 점검, ExternalName 연결, 포트 및 health check 확인을 통해 배포 환경 운영 흐름 경험

### 성과

* 질의 재작성, 검색 방식, 추천 룰을 비교한 결과 **LLM 질의 재작성 + Dense 검색 + 현행 룰 기반 재정렬** 조합이 가장 높은 추천 품질을 보임을 확인
* 추천 후보군 확장 및 평가 로직 개선을 통해 룰 기반 개인화 요소의 실제 효과를 검증
* 모델 성능뿐 아니라 AI 추천 서비스가 동작하기 위한 검색·DB·모델 서버·배포 환경의 전체 구조를 이해

### Tech Stack

`Python` `LLM API` `Embedding` `Reranker` `Qdrant` `PostgreSQL` `Docker` `Kubernetes` `GitLab CI/CD`

### Repository

[GitLab Repository](https://gitlab.com/book-curation/book-curation)

---

## 2. 웹캠 기반 집중 흐림 감지 및 미션형 피드백 시스템

### 기간 | 2026.06 ~ 진행 중
### 역할 | 실시간 집중도 분석 로직 · 행동 인식 기반 피드백 기능 구현

웹캠 영상을 기반으로 사용자의 얼굴 방향, 눈 감김, 자세 변화, 손-얼굴 접촉 등을 분석하여 집중이 흐트러진 상태를 감지하고, 미션 수행을 통해 다시 집중할 수 있도록 유도하는 개인 프로젝트입니다.

### 주요 수행 내용

* MediaPipe Face Mesh, Hands, Pose 랜드마크를 활용해 얼굴·손·자세 정보를 실시간으로 추출
* 얼굴 미감지, 고개 숙임, 시선 이탈, 눈 감김 지속, 손-얼굴 접촉, 자세 흔들림 등을 집중 흐림 판단 요소로 설계
* 눈을 일정 시간 이상 감고 있는 상태를 별도 집중 저하 조건으로 추가하고, 조건별 지속 시간을 기반으로 경고 발생 로직 구현
* 집중 저하가 감지되면 경고음을 재생하고, 랜덤 행동 미션을 수행해야 경고가 해제되도록 미션형 피드백 흐름 구성
* 손가락 개수와 손 제스처를 인식해 사용자의 미션 수행 여부를 판별하는 기능 구현
* 집중도 변화, 감지 이벤트, 미션 수행 결과를 세션 단위로 CSV·JSON 형태로 저장하고 리포트 생성 흐름 자동화
* 기능별 모듈을 분리하여 얼굴·손·자세 감지, 집중도 분석, 미션 관리, 로그 저장 기능을 구조화

### Tech Stack

`Python` `OpenCV` `MediaPipe` `Computer Vision` `Face Mesh` `Hand Landmark` `Pose Landmark` `CSV` `JSON`

### Repository

[GitHub Repository](https://github.com/th100129/webcam-situation-ai)

---

## 3. 사진·영상 기반 자동 가상현실 변환 시스템

### 기간 | 2025.09 ~ 2026.01
### 역할 | AI 기반 변환 파이프라인 설계 · Unity XR 환경 구현

2D 사진과 영상을 분석하여 깊이 정보를 추정하고, 이를 3D 형태로 변환해 가상현실 환경에서 감상할 수 있도록 구현한 프로젝트입니다.

### 주요 수행 내용

* 2D 사진·영상을 3D VR 공간으로 변환하기 위한 전체 파이프라인 설계
* MiDaS 기반 깊이 추정 모델을 활용해 이미지의 거리 정보를 생성하고, 깊이값을 기반으로 3D 메쉬 변환 실험 수행
* Unity 3D 환경에서 변환된 결과물을 시각화하고, VR 환경에서 사용자 경험을 구성
* 감성 분석 결과를 바탕으로 조명과 사운드가 자동으로 변화하는 적응형 콘텐츠 연출 로직 구현
* AI 모델의 출력 결과가 단순 분석 결과에 그치지 않고 실제 XR 콘텐츠 경험으로 이어지도록 서비스 구조 설계
* 프로젝트 결과를 기반으로 특허 출원 경험 확보

### Tech Stack

`Python` `Unity` `C#` `Computer Vision` `MiDaS` `Depth Estimation` `XR` `Stable Diffusion`

### Repository

[GitHub Repository](https://github.com/th100129/image-video-to-vr)

---

## 4. Stable Diffusion 기반 한국 전통 문양 이미지 생성 최적화

### 기간 | 2025.09 ~ 2025.12
### 역할 | 데이터셋 구축 · 이미지 생성 모델 파인튜닝 · 프롬프트 자동화

한국 전통 문양 데이터를 기반으로 이미지를 생성하고, 사용자 입력에 맞는 프롬프트를 자동 생성하여 이미지 생성 품질과 처리 효율을 높이는 프로젝트입니다.

### 주요 수행 내용

* 한국 전통 문양 이미지 데이터셋을 수집·정제하고, 학습에 적합한 형태로 전처리
* Stable Diffusion XL 모델을 기반으로 한국 전통 문양 특성을 반영할 수 있도록 파인튜닝 수행
* Llama 3 기반 LLM을 활용해 사용자 요청을 이미지 생성용 프롬프트로 자동 변환하는 파이프라인 구축
* 프롬프트 구조와 생성 조건을 조정하며 이미지 생성 품질 및 처리 시간 개선
* 반복 생성 과정에서 발생하는 비효율을 줄이기 위해 모델 및 파이프라인 최적화 실험 수행

### 성과

* 이미지 생성 시간을 기존 약 20~30초 수준에서 약 18초 수준으로 단축
* 최대 약 40%의 생성 시간 감소 효과 확인
* 사용자의 자연어 요청을 이미지 생성 프롬프트로 변환하는 자동화 흐름 구현

### Tech Stack

`Python` `Stable Diffusion XL` `LoRA` `Llama 3` `Hugging Face` `PyTorch` `Image Generation`

### Repository

[GitHub Repository](https://github.com/th100129/sdxl-korean-pattern-generator)

---

## 5. YOLO 기반 실내 식물 이미지 판별 및 관리 정보 제공 서비스

### 기간 | 2025.07 ~ 2025.08
### 역할 | 객체 탐지 모델 학습 · 식물 관리 정보 연동 설계

실내 식물 이미지를 분석해 식물 종류를 판별하고, 식물별 관리 방법과 병해 가능성 정보를 제공하는 AI 기반 식물 관리 서비스입니다.

### 주요 수행 내용

* 몬스테라, 바질, 토마토 등 실내 식물 클래스를 대상으로 객체 탐지 데이터셋 구성
* YOLOv5 기반 식물 이미지 판별 모델 학습 및 성능 검증
* 식물 종류별 특성을 고려해 물 주기, 햇빛, 온도 등 관리 정보를 제공하는 기능 설계
* 식물 이미지 분석 결과를 기반으로 병해 상태를 확인할 수 있는 확장 기능 기획
* AI 모델의 예측 결과를 사용자가 이해하기 쉬운 관리 정보로 연결하는 서비스 흐름 구성

### Tech Stack

`Python` `YOLOv5` `PyTorch` `OpenCV` `Roboflow` `Computer Vision`

### Repository

[GitHub Repository](https://github.com/th100129/plant_yolov5_model)

---

## 6. 딥페이크 탐지 모델 구현

### 기간 | 2024.09 ~ 2024.12
### 역할 | 딥러닝 모델 학습 · 데이터셋 기반 성능 평가

이미지 및 영상 데이터에서 딥페이크 여부를 판별하기 위한 딥러닝 기반 탐지 모델을 구현하고, 실제 데이터셋을 활용해 성능을 평가한 프로젝트입니다.

### 주요 수행 내용

* 딥페이크 이미지·영상 데이터셋을 기반으로 학습 데이터 전처리 및 모델 학습 환경 구성
* Python 기반 딥러닝 모델을 활용해 위조 여부를 분류하는 탐지 시스템 구현
* 실제 데이터셋을 바탕으로 모델 성능을 평가하고, 오탐·미탐 사례를 분석
* 딥페이크 탐지 기술이 보안, 콘텐츠 검증, 디지털 신뢰성 확보에 활용될 수 있는 가능성 조사
* 실험 결과와 모델 한계를 정리하며 AI 보안 분야 적용 가능성 분석

### Tech Stack

`Python` `Deep Learning` `Computer Vision` `OpenCV` `PyTorch`

### Repository

[GitHub Repository](https://github.com/th100129/voiceDetection)

---

## Skills

### AI / Machine Learning

`Python` `PyTorch` `YOLO` `Stable Diffusion` `LLM API` `Embedding` `Reranker` `Computer Vision`

### Data / Backend

`PostgreSQL` `Qdrant` `CSV` `JSON` `REST API` `Flask`

### Infra / Collaboration

`Docker` `Kubernetes` `GitLab CI/CD` `Git` `GitHub` `GitLab` `Notion`

### XR / Development Tools

`Unity` `C#` `OpenCV` `Roboflow` `VS Code`
