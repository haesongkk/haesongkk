# 신해성 | Game Client Developer

## Education

| 기간 | 기관 | 내용 |
|---|---|---|
| 2019.03 – 2019.08 | 덕성여자대학교 | 정보통계학과 |
| 2023.03 – 2023.11 | 게임인재원 5기 | 프로그래밍 파트 |
| 2025.03 – 현재 | 서울과학기술대학교 | 컴퓨터공학과 4학년 재학 중 (2027.02 졸업 예정) |

## Tech Stack

**Graphics / Engine**  
C++ · DirectX11 · HLSL · Direct2D · OpenGL · GLSL · Win32 API

**AI / 3D Pipeline**  
Python · PyTorch · OpenCV · MediaPipe · 3D Mesh Processing

**Game Development**  
Unity · C# · Java · Swing/AWT

## Projects

### 1. PolyPort

**Direct2D 기반 자체 2D 엔진 + 퍼즐 플랫폼 게임**

<img src="https://raw.githubusercontent.com/haesongkk/PolyPort/main/screenshot.gif" width="720"/>

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
- 디버그 뷰 구현

#### 회고

타일맵 툴을 만들 때 처음에는 이미지와 좌표 정보만 저장했는데, 런타임에서 타일별로 어떤 오브젝트를 생성할지도 지정해야 한다는 점을 뒤늦게 파악하고 데이터 구조를 재설계했습니다. 또 개발자 관점에서 설계한 툴 UX가 기획자의 요구와 달라 여러 차례 수정을 거쳤는데, 내가 당연히 좋다고 생각한 설계가 사용자 관점에서는 그렇지 않을 수 있다는 걸 직접 경험했습니다. 리소스 로딩 지연 문제는 시연 직전에 게임 시작 시 전체 맵 데이터를 일괄 로딩하는 방식으로 임시 대응했지만, 근본적인 해결은 비동기 로딩이어야 한다는 점을 인지하면서 마무리됐습니다.

> 게임인재원 내부 시상 수상

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

#### 회고

파이프라인 중 객체 최종 배치 파트가 예상 외로 가장 어려웠습니다. 관련 논문을 직접 찾아 읽으며 접근법을 수립했고, 그 과정에서 Differentiable Rendering을 학습해 적용했습니다. 다만 학습을 진행할수록 배치 결과가 오히려 나빠지는 발산 문제는 아직 해결하지 못했습니다. 좌표축 변환 코드를 AI로 생성해 쓰던 중 반복적으로 오류가 발생한 것도 인상 깊었는데, 시각화(디버깅) 결과 자체의 신뢰도도 불분명한 상황에서 계산이 잘못된 건지 시각화가 잘못된 건지조차 구분이 안 됐습니다. 결국 직접 원인을 추적해 해결했고, AI 도구를 맹신하지 않고 직접 검증하는 과정이 필요하다는 점을 체감했습니다.

---

### 3. 3DModelViewer

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

---

### 4. MotionCapture

**Video Pose Estimation + 3D Character Rendering**

<img src="https://raw.githubusercontent.com/haesongkk/MotionCapture/main/screenshot.gif" width="720"/>

- **기간**: 약 1주
- **형태**: 개인 프로젝트
- **기술 스택**: Python, OpenCV, MediaPipe, PyOpenGL, GLSL, pygltflib, GLB
- **Repository**: https://github.com/haesongkk/MotionCapture

#### 구현 내용

- OpenCV 기반 입력 영상 프레임 처리
- MediaPipe Pose를 활용한 인체 관절 추정
- 프레임 간 관절 좌표 보정을 통한 움직임 완화
- MediaPipe 관절 방향과 Mixamo 리깅 본 구조 매핑
- GLB 모델의 Mesh, Texture, Joint, Weight, Node Hierarchy, Inverse Bind Matrix 로드
- OpenGL VAO/VBO/EBO 구성
- GLSL Vertex Shader 기반 스키닝 연산
- 프레임별 관절 방향 갱신을 통한 3D 캐릭터 포즈 적용

---

### 5. SE_Tetris_Team1

**Java 기반 테트리스 + P2P 네트워크 배틀**

<img src="https://raw.githubusercontent.com/haesongkk/SE_Tetris_Team1/main/screenshot.gif" width="720"/>

- **기간**: 1학기
- **팀 구성**: 개발 4명
- **기술 스택**: Java 17, Swing/AWT, Gradle, JUnit Jupiter, Jacoco, SpotBugs, Checkstyle, Gson
- **Repository**: https://github.com/haesongkk/SE_Tetris_Team1

#### 담당 역할

팀장으로서 개발 범위 분담과 통합 흐름을 관리했습니다.  
P2P 네트워크 배틀과 배틀 씬을 구현했으며, 게임오버/스코어보드 씬과 담당 파트 테스트 코드를 작성했습니다.

#### 담당 구현

- P2P 네트워크 배틀 구현
- 게임오버 씬 구현
- 스코어보드 씬 구현
- 담당 구현 파트 테스트 코드 작성

#### 회고

P2P 통신 구현 과정에서 일시정지 플래그가 양측에서 반복 토글되는 동기화 문제를 겪었고, 실시간 상태 동기화의 복잡성을 직접 다루며 해결했습니다. 스코어보드·게임오버 씬에 애니메이션을 많이 넣었더니 심각하게 버벅이는 문제도 있었는데, Java GC가 알아서 처리해줄 것이라 생각했던 Timer 객체가 명시적으로 해제되지 않아 누적된 것이 원인이었습니다. `cancel()` 처리를 추가하자 버벅임이 바로 사라졌고, 언어가 메모리를 관리해준다고 해서 리소스 해제를 신경 쓰지 않아도 된다는 건 아니라는 걸 배웠습니다.

---

### 6. 2D-RUNNER-GAME

**Unity 기반 2D 리듬 러너 게임**

<img src="https://raw.githubusercontent.com/haesongkk/2D-RUNNER-GAME/main/screenshot.gif" width="720"/>

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

---

### 7. Survive38s

**Windows Console API 기반 2D 생존 게임**

<img src="https://raw.githubusercontent.com/haesongkk/Survive38s/main/screenshot.gif" width="720"/>

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

#### 회고

생에 첫 프로젝트로, 2단 점프 구현 과정에서 프레임 의존적 이동과 중력 처리 문제를 직접 겪으며 게임 루프와 물리 업데이트의 기초를 익혔습니다.

## Contact

- Email: haesoooong@gmail.com
- GitHub: https://github.com/haesongkk