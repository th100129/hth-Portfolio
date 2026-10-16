# 허태희 | AI Engineer Portfolio

AI 전공을 기반으로 **머신러닝·딥러닝 모델 개발부터 성능 평가, AI 서비스 구현 및 배포**까지 다양한 프로젝트를 수행했습니다.

컴퓨터 비전, 멀티모달 AI, 생성형 AI, 추천 시스템 분야에서 데이터 전처리, 모델 파인튜닝, 추론 최적화, 검색 파이프라인 구성과 서비스 연동을 경험했습니다. 특히 실험 결과와 오류 사례를 분석하고, 이를 바탕으로 모델과 서비스의 성능을 개선하는 과정에 관심이 있습니다.

- **주요 관심 분야:** AI/ML Engineering · Vision-Language Models · Computer Vision · Generative AI
- **학력:** 성신여자대학교 AI융합학부 AI전공 (2027년 2월 졸업 예정)
- **연구·발표:** HCLT 2026 논문 채택 및 포스터 발표

---

## Research Highlight

**한국 문화 멀티모달 QA를 위한 VLM 적응 및 추론 최적화**  
HCLT 2026 · Poster Accept

- **기반 모델:** A.X-4.0-VL-Light (7.69B)
- **핵심 접근:** DoRA 기반 파인튜닝, MC·SA·LA 유형별 추론 전략, 선택적 OCR·RAG, Multi-view TTA
- **연구 성과:** 종합 점수(Overall) **41.11 → 52.26 (+11.15p)** 개선 (동일 백본의 Zero-shot 대비)

---

## Projects

<details>
<summary><b>01. 한국 문화 멀티모달 QA — VLM 파인튜닝 및 추론 최적화</b> | 2026.07 ~ 2026.10</summary>

### 개요

한국 문화 관련 이미지와 질문을 바탕으로 정답을 생성하는 멀티모달 질의응답 시스템의 성능을 개선한 연구 프로젝트입니다. 약 1,000개의 학습 문항을 활용하는 저자원 환경에서 VLM 파인튜닝과 문제 유형별 추론 전략을 실험했습니다.

**역할:** 모델 학습·추론 실험, 오류 분석 및 성능 평가, 논문·포스터 작성 및 발표

### 주요 수행 내용

- **A.X-4.0-VL-Light(7.69B)** 기반으로 DoRA 파인튜닝을 수행하고, 공유 표현 학습 후 **객관식(MC)·단답형(SA)·서술형(LA)** 유형별 전문 어댑터 및 추론 전략 구성
- 객관식의 선택지 단위 판정, 단답형의 형식 제약·Beam Search 등 **문제 유형에 따른 추론 로직** 적용
- 이미지 내 문자 정보 활용을 위한 **선택적 OCR**, 외부 근거 활용을 위한 **선택적 RAG 라우팅** 실험
- 로지스틱 회귀 기반 라우팅과 검색 결과 적용 조건을 검토하고, 불필요한 외부 정보가 성능에 미치는 영향 분석
- SA·LA 유형에 **Multi-view Test-Time Augmentation(TTA)**을 적용하고 원본·추가 추론 결과의 채택 여부를 판단하는 합의 전략 구성
- Zero-shot 및 파인튜닝 모델의 결과를 비교하고, 문제 유형별 오류 사례를 분석하여 후처리·추론 전략 개선

### 성과

- 동일 백본 Zero-shot 대비 **Overall Score 41.11 → 52.26 (+11.15p)** 개선
- 저자원 멀티모달 QA 환경에서 문제 유형별 모델 적응과 추론 전략의 효과 검증
- **HCLT 2026 학술대회 논문 채택(Poster Accept) 및 포스터 발표**

### Tech Stack

`Python` `PyTorch` `Hugging Face Transformers` `PEFT` `DoRA` `VLM` `OCR` `RAG` `Beam Search` `TTA`

**Repository:** 링크 추가 예정  

</details>

<details>
<summary><b>02. AI 도서 큐레이션 서비스</b> | 2026.04 ~ 2026.05</summary>

### 개요

LLM 기반 사용자 의도 분석, 임베딩 검색, 리랭킹, 룰 기반 재정렬을 결합하여 사용자 취향과 상황에 맞는 도서를 추천하는 개인화 서비스입니다.

**역할:** 추천 파이프라인 성능 평가 · AI 서비스 배포 환경 구성

### 주요 수행 내용

- LLM 기반 사용자 의도 분류 및 질의 재작성을 활용해 추천 요청을 검색에 적합한 형태로 처리
- **Dense·BM25·Lookup** 검색 방식의 결과를 비교하며 방식별 특성과 추천 적합도 분석
- 장르, 목적, 리뷰, 책장 정보 등을 반영하는 룰 기반 재정렬 로직의 영향 검증
- 벡터 유사도에 따른 후보군 조기 제한 문제를 확인하고, 후보군 확장을 통해 평가 로직 개선
- 정성 평가 기준을 설정하고 질의 유형별 추천 결과를 분석하여 파이프라인 조합 비교
- Kubernetes 환경에서 AI 서버, 백엔드, 프론트엔드, 임베딩·리랭커 서버, PostgreSQL, Qdrant의 연결 구조 구성
- API 통신, ExternalName, 포트, Health Check 등을 점검하며 배포 환경의 동작 확인

### 성과

- 비교 실험 결과 **LLM 질의 재작성 + Dense 검색 + 현행 룰 기반 재정렬** 조합의 추천 품질이 가장 우수함을 확인
- 후보군 및 평가 로직 개선을 통해 개인화 재정렬 요소의 실제 효과 검증
- 모델·검색·데이터베이스·배포 환경을 연결하는 AI 서비스 구조 경험

### Tech Stack

`Python` `LLM API` `Embedding` `Reranker` `BM25` `Qdrant` `PostgreSQL` `Docker` `Kubernetes` `GitLab CI/CD`

**Repository:** [GitLab Repository](https://gitlab.com/book-curation/book-curation)

</details>

<details>
<summary><b>03. 웹캠 기반 집중 저하 감지 및 미션형 피드백 시스템</b> | 2026.06 ~ 진행 중</summary>

### 개요

웹캠 영상에서 얼굴 방향, 눈 감김, 자세 변화, 손-얼굴 접촉 등을 분석해 집중 저하 상태를 감지하고 행동 미션을 통해 집중 복귀를 유도하는 개인 프로젝트입니다.

**역할:** 실시간 집중도 분석 로직 · 행동 인식 기반 피드백 기능 구현

### 주요 수행 내용

- MediaPipe 기반 얼굴·손·자세 랜드마크를 활용해 사용자 행동 정보 실시간 추출
- 얼굴 미감지, 고개 숙임, 시선 이탈, 눈 감김 지속, 손-얼굴 접촉, 자세 흔들림 등을 감지 조건으로 설계
- 조건별 지속 시간을 반영하는 경고 발생 로직 구성
- 집중 저하 감지 시 경고음을 재생하고 행동 미션 수행을 통해 경고를 해제하는 피드백 흐름 구현
- 손가락 개수 및 손 제스처 인식으로 미션 수행 여부 판별
- 이벤트·미션 이력을 CSV·JSON으로 저장하고 세션별 리포트 생성 흐름 구성
- 얼굴·손·자세 감지, 상태 분석, 미션 관리, 로그 저장 기능을 모듈화

### Tech Stack

`Python` `OpenCV` `MediaPipe` `Computer Vision` `Face Mesh` `Hand Landmark` `Pose Landmark` `CSV` `JSON`

**Repository:** [GitHub Repository](https://github.com/th100129/webcam-situation-ai)

</details>

<details>
<summary><b>04. 사진·영상 기반 자동 가상현실 변환 시스템</b> | 2025.09 ~ 2026.01</summary>

### 개요

2D 사진과 영상의 깊이 정보를 추정하고, 결과를 3D 형태로 변환해 XR 환경에서 감상할 수 있도록 설계한 프로젝트입니다.

**역할:** AI 기반 변환 파이프라인 설계 · Unity XR 환경 구현

### 주요 수행 내용

- 2D 이미지·영상을 3D VR 콘텐츠로 변환하는 처리 파이프라인 설계
- **MiDaS 깊이 추정 모델**을 활용한 거리 정보 생성 및 깊이값 기반 3D 메쉬 변환 실험
- Unity 환경에서 변환 결과를 시각화하고 VR 콘텐츠 배치 및 인터랙션 구현
- 감성 분석 결과에 따라 조명·사운드가 변화하는 적응형 콘텐츠 연출 로직 구성
- 모델 출력과 XR 사용자 경험을 연결하는 서비스 구조 설계

### 성과

- 사진·영상 기반 깊이 추정 결과를 XR 콘텐츠로 연결하는 변환 흐름 구현
- 프로젝트 결과를 기반으로 **특허 출원 경험** 확보

### Tech Stack

`Python` `Unity` `C#` `MiDaS` `Depth Estimation` `Computer Vision` `XR` `Stable Diffusion`

**Repository:** [GitHub Repository](https://github.com/th100129/image-video-to-vr)

</details>

<details>
<summary><b>05. Stable Diffusion 기반 한국 전통 문양 이미지 생성 최적화</b> | 2025.09 ~ 2025.12</summary>

### 개요

한국 전통 문양 데이터로 이미지 생성 모델을 파인튜닝하고, 자연어 입력을 이미지 생성 프롬프트로 변환하는 자동화 파이프라인을 구축한 프로젝트입니다.

**역할:** 데이터셋 구축 · 이미지 생성 모델 파인튜닝 · 프롬프트 자동화

### 주요 수행 내용

- 한국 전통 문양 이미지 데이터 수집·정제 및 학습 데이터 전처리
- **Stable Diffusion XL** 기반 전통 문양 생성 모델 파인튜닝
- **Llama 3** 기반 사용자 요청 → 이미지 생성 프롬프트 자동 변환 파이프라인 구성
- 프롬프트 구조·생성 조건 조정에 따른 이미지 품질 및 처리 시간 비교
- 반복 생성 과정의 비효율을 개선하기 위한 최적화 실험 수행

### 성과

- 이미지 생성 시간을 기존 약 **20~30초에서 약 18초 수준**으로 단축
- 실험 조건에 따라 **최대 약 40%의 생성 시간 감소** 확인
- 자연어 요청 기반 프롬프트 생성 자동화 구현

### Tech Stack

`Python` `Stable Diffusion XL` `LoRA` `Llama 3` `Hugging Face` `PyTorch` `Image Generation`

**Repository:** [GitHub Repository](https://github.com/th100129/sdxl-korean-pattern-generator)

</details>

<details>
<summary><b>06. YOLO 기반 실내 식물 이미지 판별 및 관리 정보 제공 서비스</b> | 2025.07 ~ 2025.08</summary>

### 개요

실내 식물 이미지를 분석해 식물 종류를 판별하고, 식물별 관리 정보를 연결하는 AI 기반 식물 관리 서비스입니다.

**역할:** 객체 탐지 모델 학습 · 식물 관리 정보 연동 설계

### 주요 수행 내용

- 실내 식물 클래스의 이미지 데이터셋 구성 및 전처리
- **YOLOv5 객체 탐지 모델** 학습 및 식물 이미지 판별 성능 검증
- 물 주기, 햇빛, 온도 등 식물별 관리 정보 연동 기능 설계
- 병해 상태 확인을 위한 서비스 확장 기능 기획
- 이미지 추론 결과를 사용자 친화적인 관리 정보로 전달하는 서비스 흐름 구성

### Tech Stack

`Python` `YOLOv5` `PyTorch` `OpenCV` `Roboflow` `Computer Vision`

**Repository:** [GitHub Repository](https://github.com/th100129/plant_yolov5_model)

</details>

<details>
<summary><b>07. 딥페이크 탐지 모델 구현</b> | 2024.09 ~ 2024.12</summary>

### 개요

이미지·영상 데이터의 딥페이크 여부를 분류하는 딥러닝 모델을 구현하고, 실제 데이터셋을 활용해 성능을 평가한 프로젝트입니다.

**역할:** 데이터 전처리 · 모델 학습 · 성능 평가

### 주요 수행 내용

- 딥페이크 이미지·영상 데이터셋 전처리 및 학습 환경 구성
- Python 기반 딥러닝 모델을 활용한 위조 여부 분류 실험
- 데이터셋 기반 성능 평가 및 오탐·미탐 사례 분석
- 모델 한계와 보안·콘텐츠 검증 분야의 활용 가능성 정리

### Tech Stack

`Python` `PyTorch` `OpenCV` `Deep Learning` `Computer Vision`

**Repository:** [GitHub Repository](https://github.com/th100129/voiceDetection)

</details>

---

## Tech Stack

| Category | Technologies |
| --- | --- |
| **AI / Machine Learning** | `PyTorch` `Hugging Face Transformers` `PEFT` `DoRA` `YOLOv5` `MediaPipe` `Stable Diffusion XL` |
| **LLM / Multimodal** | `VLM` `LLM API` `RAG` `OCR` `Embedding` `Reranker` `Beam Search` `TTA` |
| **Data / Backend** | `Python` `FastAPI` `Flask` `REST API` `PostgreSQL` `Qdrant` `CSV` `JSON` |
| **Infra / Collaboration** | `Docker` `Kubernetes` `GitLab CI/CD` `Git` `GitHub` `GitLab` `Notion` |
| **XR / Development Tools** | `Unity` `C#` `OpenCV` `Roboflow` `VS Code` |

---

> 한국 문화 멀티모달 QA 프로젝트의 Repository 링크는 추후 추가 예정입니다.
