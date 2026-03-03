# [컴투스 인턴십] [Unity] 미니게임천국 - 젠킨스 CI/CD 구조 개선 / SDK 업데이트 / 신규 빌드 배포 (2026.01 ~ 2026.02)

**🔹 진행 기간 :** **2026.01 ~ 2026.02**

## 🔷 사용 기술 스택

| 분류 | 내용 |
|------|------|
| **Engine** | Unity 6 |
| **Version Control** | SVN |
| **Build Target** | Android, iOS |

## 🔷 업무 내용

**🔹 젠킨스 CI/CD 구조 구성**

<img src="https://github.com/user-attachments/assets/6fdc9c11-3fc6-4d6b-bd31-509b66890915" width="75%">

⬆ 플랫폼 및 용도별 빌드 Job 분리

<img src="https://github.com/user-attachments/assets/e218ce62-ff8e-49a8-bd4d-5533177f6cf1" width="75%">

⬆ 빌드 Job 내 매개변수 설정 (버전 및 빌드 넘버, 사용 스테이지 등 설정)

<img src="https://github.com/user-attachments/assets/b53cd1af-797e-4259-889b-0b50e7941df5" width="75%">

⬆ 스테이지 단위 빌드 파이프라인 구성

<img src="https://github.com/user-attachments/assets/c089ffbc-c7ef-491f-b907-c4c5a11b4971" width="75%">

⬆ 스테이지 내 기능별 Job 분리

<img src="https://github.com/user-attachments/assets/125f29c2-8e23-470e-863b-97ff9605935d" width="75%">

⬆ 앱 업로드 플랫폼에 빌드 결과물 자동 배포


**🔹 SDK 업데이트**




**🔹 신규 빌드 배포**

⬆ Android/iOS 플랫폼 빌드 진행 및 스토어 업로드 :

플랫폼별 빌드 세팅/빌드 (Android : 키스토어, iOS : XCode, 프로비저닝 등)

신규 빌드 배포를 위해 PM/서비스운영팀/QA 팀 등과 협업 수행
