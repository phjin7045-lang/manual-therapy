# MANUAL THERAPY — 모바일 웹 시뮬레이션

## 포함 기능
- 반응형 한국어 UI
- 3D 환자/치료사 손 장면(Three.js / React Three Fiber)
- MediaPipe Hand Landmarker 웹캠 손바닥 추적
- 카메라 미사용 시 치료 화면 터치 조작
- 환자 문진, 신체 평가, 교육용 움직임 시뮬레이션, 결과 화면
- 만족도/신뢰도/위험도 표시
- 해부학 도감, 5개 사례 카테고리, 사례별 환자 데이터
- LocalStorage 진행/기록 저장, 레벨/경험치
- Recharts 결과 그래프

## 휴대폰만으로 게시하기 (PC 불필요)
1. 휴대폰에서 GitHub 앱 또는 브라우저로 github.com에 로그인합니다.
2. 새 Public 저장소를 만들고 이름을 `manual-therapy`로 지정합니다.
3. 이 ZIP을 휴대폰에서 압축 해제한 뒤 저장소의 `Add file` → `Upload files`로 프로젝트 파일을 업로드합니다.
4. 저장소의 `Settings` → `Pages` → `Build and deployment`에서 `GitHub Actions`가 아닌 `Deploy from a branch`를 선택합니다.
5. `main` 브랜치의 `/ (root)`를 선택해 저장합니다.
6. 단, Vite 프로젝트는 빌드가 필요하므로 가장 쉬운 방법은 Netlify의 GitHub 연동 또는 GitHub Actions로 빌드/배포하는 것입니다. Netlify에 GitHub 저장소를 연결하고 Build command를 `npm run build`, Publish directory를 `dist`로 설정합니다.
7. 배포된 `https://...` 주소를 스마트폰에서 열고 브라우저 메뉴의 '홈 화면에 추가'를 선택하면 앱처럼 사용할 수 있습니다.

## 개발/빌드
```bash
npm install
npm run dev
npm run build
```

## 웹캠 안내
- 카메라는 HTTPS 또는 localhost에서만 브라우저 보안 정책상 동작합니다.
- 브라우저가 카메라 권한을 요청하면 허용해야 합니다.
- 첫 실행 시 MediaPipe WASM과 hand_landmarker.task 모델 파일을 CDN에서 내려받습니다. 따라서 최초 손 인식에는 인터넷 연결이 필요합니다.
- 카메라가 거부되거나 미지원이면 시뮬레이션 화면의 터치 입력을 이용할 수 있습니다.
- 카메라 영상은 서버로 전송하거나 저장하지 않으며 브라우저 내 추론에만 사용됩니다.

## 현재 프로토타입 범위와 주의
이 버전은 휴대폰에서 실제 실행할 수 있는 MVP입니다. 3D 인체는 교육용 저폴리곤 프록시 모델이며, 해부학 도감은 텍스트 설명 중심입니다. 5개 스테이지 카테고리와 각기 다른 사례 데이터가 포함되어 있지만, 어깨 사례가 우선 플레이 흐름으로 연결되어 있습니다. 손 추적은 손바닥 중심의 위치 제어를 구현한 것이며, 의료용 정밀 측정이나 실제 도수치료 훈련 장비가 아닙니다. 점수/통증 변화는 게임용 가상 수치입니다.
