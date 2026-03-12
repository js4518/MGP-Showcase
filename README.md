# [컴투스 인턴십] [Unity] 미니게임천국 - 젠킨스 CI/CD 구조 개선 / SDK 업데이트 / 신규 빌드 배포 (2026.01 ~ 2026.02)

**🔹 진행 기간 :** **2026.01 ~ 2026.02**

## 🔷 사용 기술 스택

| 분류 | 내용 |
|------|------|
| **Engine** | Unity 6 |
| **Version Control** | SVN |
| **CI/CD** | Jenkins |
| **SDK** | Hive SDK, Hive AdKit, Liapp |
| **Build Target** | Android, iOS |

## 🔷 업무 내용

### 🔹 젠킨스 CI/CD 구조 개선

#### 🔹 플랫폼 및 용도별 빌드 Job 분리

<img src="https://github.com/user-attachments/assets/6fdc9c11-3fc6-4d6b-bd31-509b66890915" width="95%">

　

 　

#### 🔹 빌드 Job 내 매개변수 설정 (버전 및 빌드 넘버, 사용 스테이지 등 설정)

<img src="https://github.com/user-attachments/assets/e218ce62-ff8e-49a8-bd4d-5533177f6cf1" width="95%">

　

　
  
#### 🔹 스테이지 단위 빌드 파이프라인 구성

<img src="https://github.com/user-attachments/assets/b53cd1af-797e-4259-889b-0b50e7941df5" width="95%">

　

| 스테이지 | 역할 |
| :--- | :--- |
| **Prepare** | 빌드에 필요한 환경변수 설정 |
| **Update** | ‘UTIL_SVN_UPDATE’ Job을 통해 SVN에서 프로젝트 파일 다운로드 |
| **Build Setting** | 프로젝트 코드 내 빌드 설정 적용 함수를 호출하여, 빌드 설정에 매개변수를 적용 |
| **Asset Build** | 프로젝트 코드 내 에셋 번들 빌드 함수를 호출하여, 매개변수를 기반으로 에셋 번들 빌드를 진행 |
| **Unity Build** | 프로젝트 코드 내 유니티 빌드 함수 및 매개변수를 기반으로 ‘UTIL_UNITY_BUILD’ Job을 작동시켜서 유니티 빌드 진행<br>(빌드 타겟이 Android인 경우, 먼저 ‘UTIL_SDK_INSTALL’ Job을 통해 SDK 설치/업데이트) |
| **Xcode Build** | JSON 파일에 담긴 프로비저닝 프로파일 정보를 기반으로 ‘UTIL_XCODE_BUILD’ Job을 작동시켜서 Xcode 빌드 진행 |
| **App Protect** | ‘UTIL_APPSHIELD_APPLY’ Job을 통해, 빌드하여 생성된 앱 설치 파일에 Liapp을 적용 |
| **APK Export** | 빌드 타겟이 Android인 경우, ‘UTIL_APK_EXPORT’ Job을 통해, .aab 파일에서 .apk 파일을 추출 |
| **Build Archive** | 빌드 설정값을 기록 |
| **Appchive Upload** | 빌드 결과물을 앱 업로드 플랫폼에 자동으로 업로드 |

　

　
  
#### 🔹 스테이지 내 기능별 Job 분리

<img src="https://github.com/user-attachments/assets/c089ffbc-c7ef-491f-b907-c4c5a11b4971" width="95%">

　
 
| 연결 Job | 역할 |
| :--- | :--- |
| **UTIL_SVN_UPDATE** | SVN에서 프로젝트 파일 다운로드 |
| **UTIL_SDK_INSTALL** | Unity 설치 경로에 포함된 Android SDK 구성 요소들을 자동으로 최적화하고 업데이트 |
| **UTIL_UNITY_BUILD** | 유니티 빌드 |
| **UTIL_XCODE_BUILD** | Xcode 빌드 |
| **UTIL_APK_EXPORT** | .aab 파일에서 .apk 파일을 추출 |
| **UTIL_APPSHIELD_APPLY** | 빌드를 통해 생성된 앱 설치 파일에 Liapp을 적용 |
| **UTIL_AWS_S3** | 버전 파일 AWS S3에 업로드 |
| **UTIL_AWS_PURGE** | 아카마이 퍼지 |
| **UTIL_SPEAK_MESSAGE** | 빌드 파이프라인 종료 Notify |

　

　

#### 🔹 앱 업로드 플랫폼에 빌드 결과물 자동 배포

<img src="https://github.com/user-attachments/assets/125f29c2-8e23-470e-863b-97ff9605935d" width="95%">

　

　
 
### 🔹 SDK 업데이트

Hive SDK, AdKit, Liapp 등의 **SDK를 최신 환경에 맞게 버전 업데이트** 및 정상 작동 확인

　

### 🔹 신규 빌드 배포

<img src="https://github.com/user-attachments/assets/bff04c92-6fda-4b26-897d-f1454975facc" width="20%">
<img src="https://github.com/user-attachments/assets/8ebc320b-f545-4e97-9205-c57f388b1cdb" width="20%">

#### ⬆ Android/iOS 플랫폼 빌드 진행 및 스토어 업로드 :

플랫폼별 빌드 세팅/빌드 (Android : 키스토어, iOS : XCode, 프로비저닝 등)

신규 빌드 배포를 위해, **QA팀과 협업**하여 **신규 이슈 확인 및 대응**

이후 **사업부/서비스운영팀과 협업**하여 **신규 빌드 배포**
