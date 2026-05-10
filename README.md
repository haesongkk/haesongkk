# 신해성 | Rendering / Game Client / Graphics-Oriented Developer

게임 클라이언트와 그래픽스 시스템을 중심으로 공부하고 있는 개발자입니다.  
상용 엔진의 기능을 사용하는 것에 그치지 않고, 렌더링 파이프라인, 리소스 로딩, 게임 루프, 씬 관리, 충돌 처리, 데이터 기반 제작 구조처럼 게임이 실제로 동작하는 내부 구조를 직접 구현하며 학습해 왔습니다.

DirectX11 기반 3D 렌더링 실습과 Direct2D 기반 자체 2D 엔진 프로젝트를 진행했고, 최근에는 단일 이미지로부터 객체를 분리하고 3D Mesh를 생성한 뒤 3D 공간에 배치하는 Image-to-World 파이프라인을 개발하고 있습니다.

관심 분야는 실시간 렌더링, 그래픽스 파이프라인, 게임 엔진 구조, 3D 데이터 처리, 렌더링 기반 최적화입니다.

## Tech Stack

**Graphics / Engine**  
C++ · DirectX11 · HLSL · Direct2D · Win32 API

**AI / 3D Pipeline**  
Python · PyTorch · OpenCV · 3D Mesh Processing

**Game Development**  
Unity · C# · Java · Swing/AWT

## Main Projects

### 1. 3DModelViewer

**DirectX11 기반 3D 렌더링 학습 프로젝트**

<img src="https://raw.githubusercontent.com/haesongkk/3DModelViewer/main/Screenshots/%EC%95%A0%EB%8B%88%EB%A9%94%EC%9D%B4%EC%85%98.gif" width="720"/>

- **기간**: 약 2개월
- **형태**: 개인 학습 프로젝트
- **기술 스택**: C++17, Win32 API, Direct3D 11, HLSL, DirectXTK, ImGui, Assimp
- **Repository**: https://github.com/haesongkk/3DModelViewer

#### 구현 내용

- Direct3D 11 기반 렌더타겟 출력
- 텍스처 매핑 및 기본 음영 처리
- 노멀 매핑 적용
- FBX 모델 로드
- 애니메이션 데이터 로드
- ImGui 기반 디버깅/테스트 UI 구성
- HLSL 셰이더 작성

#### 학습 포인트

이 프로젝트에서는 3D 모델을 단순히 불러오는 것보다, 렌더링 리소스가 어떤 순서로 준비되고 GPU 파이프라인을 거쳐 화면에 출력되는지를 이해하는 데 집중했습니다.  
렌더타겟, 셰이더, 텍스처, 노멀 맵, 외부 모델 데이터, 애니메이션 데이터가 각각 렌더링 과정에서 어떤 역할을 하는지 직접 확인했습니다.

---

### 2. Image-to-World

**단일 이미지 기반 3D 월드 생성 파이프라인**

| Input | Output |
|---|---|
| <img src="https://raw.githubusercontent.com/haesongkk/Image-to-World/main/doc/260505/raw_image.jpg" width="360"/> | <img src="https://raw.githubusercontent.com/haesongkk/Image-to-World/main/doc/260505/screenshot.png" width="360"/> |


- **기간**: 반 학기 / 진행 중
- **형태**: 개인 프로젝트
- **기술 스택**: Python, PyTorch, OpenCV, 3D Mesh Processing, Differentiable Rendering
- **Repository**: https://github.com/haesongkk/Image-to-World

#### 구현 내용

- 이미지 배경 제거
- 객체 태그 추출
- 객체별 마스크 추출
- 객체별 3D Mesh 생성
- Remesh를 통한 폴리곤 수 감소
- Depth Map 추정
- 카메라 파라미터 및 자세 추정 기반 Point Cloud 생성
- 객체 초기 배치
- Differential Rendering 기반 Transform 최적화 실험

#### 학습 포인트

이 프로젝트는 하나의 모델만 사용하는 방식이 아니라, 이미지 이해, 객체 분리, 3D 생성, Depth 추정, 공간 배치, 렌더링 기반 보정을 하나의 파이프라인으로 연결하는 방식으로 접근했습니다.  
각 단계의 입출력 형식, 좌표계, Mesh 품질, Depth 정확도, 객체 배치 오차가 최종 결과에 어떤 영향을 주는지 확인하고 있습니다.

현재는 Remesh 이후 Texture Baking, 객체 배치 정밀도 개선, 가려진 객체 복원, 배경 복원, Differential Rendering 안정화를 중심으로 개선하고 있습니다.

---

### 3. PolyPort

**Direct2D 기반 자체 2D 엔진 + 퍼즐 플랫폼 게임**

- **기간**: 약 3주
- **팀 구성**: 개발 3명, 기획 2명, 아트 2명
- **기술 스택**: C++, Direct2D, DirectWrite, WIC, Win32/MFC, nlohmann/json, FMOD
- **Repository**: https://github.com/haesongkk/PolyPort

#### 담당 역할

타일맵 제작 툴과 JSON 기반 스테이지 로딩 구조를 구현했습니다.  
또한 포트 상호작용, 플레이어 리스폰, 컷씬, 사운드 재생을 담당하여 데이터 기반 제작 흐름과 실제 게임플레이가 연결되도록 구성했습니다.

#### 담당 구현

- 타일맵 제작 툴 구현
- 툴에서 제작한 맵 데이터를 JSON으로 저장/로드하는 구조 구현
- 런타임에서 JSON 데이터를 기반으로 타일맵과 스테이지 오브젝트 생성
- FMOD 기반 사운드 재생 적용
- 포트 오브젝트 상호작용 구현
- 플레이어 사망 후 리스폰 처리
- 컷씬 흐름 및 관련 연출 구현

#### 학습 포인트

이 프로젝트에서는 게임 기능을 코드에 직접 고정하지 않고, 외부 데이터와 툴을 통해 스테이지를 구성하는 방식을 경험했습니다.  
특히 타일맵 툴과 JSON 로딩 구조를 구현하면서, 게임 엔진에서 툴과 런타임이 어떻게 연결되는지 이해할 수 있었습니다.

---

### 4. SE_Tetris_Team1

**Java 기반 테트리스 + P2P 네트워크 배틀**

- **기간**: 1학기
- **팀 구성**: 개발 4명
- **기술 스택**: Java 17, Swing/AWT, Gradle, JUnit Jupiter, Jacoco, SpotBugs, Checkstyle, Gson
- **Repository**: https://github.com/haesongkk/SE_Tetris_Team1

#### 담당 역할

팀장으로서 개발 범위 분담과 통합 흐름을 관리했습니다.  
P2P 네트워크 배틀과 배틀 씬을 구현했으며, 게임오버/스코어보드 씬과 담당 파트 테스트 코드를 작성했습니다.

#### 담당 구현

- P2P 네트워크 배틀 구현
- P2P 배틀 씬 구현
- 게임오버 씬 구현
- 스코어보드 씬 구현
- 담당 구현 파트 테스트 코드 작성

#### 학습 포인트

이 프로젝트에서는 기능 구현뿐 아니라 팀 프로젝트에서 요구사항을 나누고, 각 파트의 구조를 맞추고, 테스트와 정적 분석 도구를 활용하는 과정을 경험했습니다.  
특히 P2P 네트워크 배틀을 구현하면서 게임 상태 전달, 배틀 씬 흐름, 결과 화면까지 하나의 플레이 경험으로 연결하는 데 집중했습니다.

---

### 5. 2D-RUNNER-GAME

**Unity 기반 2D 리듬 러너 게임**

- **기간**: 약 1주
- **형태**: 개인 프로젝트
- **기술 스택**: Unity, C#, JSON
- **Repository**: https://github.com/haesongkk/2D-RUNNER-GAME

#### 구현 내용

- Space 키 하나로 상/하 레인 전환
- JSON 기반 노트 타이밍 데이터 로딩
- 시간 기반 노트 및 장애물 생성
- 보스 등장 및 후반부 패턴 강화
- 체력/점수 UI
- 무한 스크롤 배경
- 노트 타이밍 제작 보조 도구 구현

#### 학습 포인트

이 프로젝트에서는 입력은 단순하게 유지하되, 음악 시간표와 오브젝트 생성 타이밍을 통해 게임의 리듬감을 만드는 데 집중했습니다.  
노트 데이터를 JSON으로 분리하고, 시간에 따라 오브젝트를 생성하도록 구성하면서 데이터 기반 게임 진행 구조를 경험했습니다.

---

### 6. Survive38s

**Windows Console API 기반 2D 생존 게임**

- **기간**: 약 1주
- **형태**: 개인 프로젝트
- **기술 스택**: C++, Windows Console API, GetAsyncKeyState, Windows Multimedia API
- **Repository**: https://github.com/haesongkk/Survive38s

#### 구현 내용

- 38초 생존 게임 구조
- 플레이어 이동 및 2단 점프
- 시간 기반 장애물 생성
- 충돌 판정 및 무적 시간
- enum과 함수 포인터 배열 기반 씬 관리
- 고정 업데이트와 프레임 렌더링 분리
- 콘솔 더블 버퍼링 렌더링
- Windows API 기반 입력 및 사운드 처리

#### 학습 포인트

이 프로젝트에서는 상용 엔진 없이 게임이 프레임 단위로 동작하는 가장 기본적인 구조를 직접 구현했습니다.  
게임 루프, DeltaTime, 고정 업데이트, 입력 상태 구분, 더블 버퍼링, 씬 전환을 직접 다루면서 이후 엔진 구조를 이해하기 위한 기반을 만들었습니다.

---

## Project Focus

| Area | Projects |
|---|---|
| Real-Time Rendering / Graphics | 3DModelViewer, Image-to-World |
| Game Engine Architecture | PolyPort, Survive38s |
| Data-Driven Tooling | PolyPort, 2D-RUNNER-GAME |
| Game Client Programming | PolyPort, 2D-RUNNER-GAME, Survive38s |
| Networking / Team Project | SE_Tetris_Team1 |
| AI + 3D Pipeline | Image-to-World |

---

## Current Direction

렌더링과 게임 엔진 구조를 중심으로 더 깊게 공부하고 있습니다.  
현재는 DirectX11 기반 렌더링 실습을 바탕으로 PBR, IBL, Shadow Mapping, Post Processing, Render Queue, Culling, GPU Resource Management 등을 다음 학습 목표로 두고 있습니다.

장기적으로는 그래픽스 파이프라인과 엔진 내부 구조를 이해하고, 실시간 렌더링 품질과 성능을 함께 개선할 수 있는 개발자가 되는 것을 목표로 하고 있습니다.
