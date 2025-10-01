# Team Info

| (1) 주제 | **hi-meow : 딥러닝과 RAG 챗봇을 활용한 반려동물 케어 어플리케이션**
|:---  |---  |
| (2) 팀 번호 / 팀 이름 | 2-11 안냥 |
| (3) 팀 구성원 | 조준화, 안치산, 임경수 |
| (4) 팀 지도교수 | 정지훈 교수님 |
| (5) 회의록 | https://www.notion.so/jun-n/Hi-Meow-b32fb637ed5045b2aeda6fdb98449344 |

<br>

# About Our Project

최근 반려묘와 함께하는 가정이 늘어나면서, 고양이 건강 관리에 대한 관심도 높아지고 있습니다. 하지만 많은 초보 반려인들이 고양이의 안구 질환을 육안으로 식별하고 초기에 대처하는 데 어려움을 겪습니다. 안구 질환은 방치될 경우 실명과 같은 심각한 결과로 이어질 수 있습니다.

저희 hi-meow는 이러한 문제를 해결하기 위해 인공지능 기술을 활용하여 고양이 눈 사진을 분석하고, 질병을 조기 진단하며, 맞춤형 건강 관리 서비스를 제공하는 통합 애플리케이션입니다.

<br>

# Key Features

## 1. AI 기반 고양이 안구 질환 진단

사용자가 업로드한 고양이 눈 사진의 조명, 각도, 대비 등 품질을 자동으로 판단하고 최적의 분석을 위해 전처리합니다.

딥러닝 모델, 생성 모델(Generative model) 및 능동 학습(Active Learning) 기술을 활용하여 높은 정확도의 진단 결과를 제공합니다.

주요 5대 안구 질환(안검염, 결막염, 각막부골편, 비궤양성 각막염, 각막궤양)을 신속하게 진단합니다.

## 2. RAG 기반 챗봇 상담

눈 질병 상담: AI 진단 결과로 나온 질병에 대한 상세한 설명과 상황에 맞는 적절한 대처법을 RAG(검색 증강 생성) 기반 챗봇을 통해 제공합니다.

일반 건강 상담: 고양이의 특정 행동이나 상태에 대한 설명을 바탕으로 잠재적인 질병 가능성을 예측하고 대응 방안을 안내합니다.

<br>

# Tech Stack & Architecture

## System Architecture
<img width="1300" height="888" alt="image" src="https://github.com/user-attachments/assets/07581d0d-4c88-4964-95b5-f9e091fb27ca" />

## Database ERD
<img width="2656" height="1446" alt="image" src="https://github.com/user-attachments/assets/bd9a74f3-d7ed-4d5e-b270-3a6b9946e818" />

## Deployment (CI/CD)
hi-meow 서비스는 GitHub Actions를 통해 효율적인 CI/CD 파이프라인을 구축하여 안정적으로 배포됩니다.
- 인프라 구성 (Infra Provisioning): infra 저장소에서 terraform apply 워크플로우를 실행하여 CloudFront를 포함한 AWS 리소스 구성을 완료합니다. 이후, 생성된 결과값을 이용해 DNS 레코드를 수동으로 업데이트합니다.
- AI 서버 배포 (AI Server Deployment): 인프라 구성이 완료되면 AI 서버의 배포 워크플로우가 자동으로 트리거됩니다.
- API 서버 배포 (API Server Deployment): AI 서버 배포에 이어 API 서버의 배포 워크플로우가 트리거되어 전체 백엔드 배포가 완료됩니다.
- 프론트엔드 (Frontend): 프론트엔드 정적 파일은 항상 S3에 호스팅되며, 1번 단계에서 CloudFront 설정이 업데이트되고 DNS가 연결되면 새로운 버전이 사용자에게 제공됩니다.
