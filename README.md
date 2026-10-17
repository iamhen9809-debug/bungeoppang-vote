# 붕어빵 취향 투표 — 실제 공유형 사이트 배포 안내

## 먼저 알아둘 점
- 이 폴더는 Firebase 연결과 실시간 집계를 지원하도록 작성된 사이트 코드입니다.
- **아직 공개 사이트 URL은 발급되지 않았습니다.** Firebase 프로젝트를 직접 만들고 아래 설정을 한 뒤 GitHub Pages에 게시해야 합니다.
- 한 브라우저의 익명 Firebase 계정당 1회 투표를 보안 규칙으로 제한합니다. 단, 사용자가 다른 기기/브라우저를 쓰거나 사이트 데이터를 지우면 새 익명 계정으로 다시 투표할 수 있습니다. 엄격한 사람당 1회가 필요하면 Google 로그인 등 인증을 추가해야 합니다.

## A. Firebase 프로젝트 및 DB 만들기
1. https://console.firebase.google.com/ 접속 후 Google 계정으로 로그인합니다.
2. **프로젝트 추가**를 눌러 `bungeoppang-vote` 같은 프로젝트를 만듭니다.
3. 프로젝트 개요의 웹 앱 아이콘 `</>`를 눌러 웹 앱을 등록합니다.
4. Firebase가 보여주는 `firebaseConfig` 값을 복사합니다.
5. 왼쪽 **Build → Authentication → 시작하기 → Sign-in method**에서 **Anonymous(익명)** 로그인을 사용 설정합니다.
6. **Build → Firestore Database → 데이터베이스 만들기**를 누르고 운영할 위치를 선택합니다.
7. Firestore의 **Rules(규칙)** 탭에서 이 폴더의 `firestore.rules` 전체를 붙여넣고 **게시**합니다.
   - 테스트 모드 규칙을 그대로 두지 마세요.
8. 이 폴더의 `firebase-config.js`를 열어 `YOUR_...` 값을 실제 Firebase 웹 앱 설정값으로 교체합니다.
   - 파일 이름과 `export const firebaseConfig`는 그대로 둡니다.
   - `apiKey`는 웹 설정용 키이며 비밀 관리자 키가 아닙니다. 서비스 계정 키/비공개 서버 키는 절대 브라우저 파일에 넣지 마세요.

## B. GitHub Pages로 무료 배포
1. https://github.com/ 에서 계정을 만들거나 로그인합니다.
2. 새 저장소(repository)를 만듭니다. 예: `bungeoppang-vote`
3. `index.html`, `firebase-config.js`, `firestore.rules` 파일을 저장소 최상위(root)에 업로드합니다.
4. 저장소의 **Settings → Pages**로 이동합니다.
5. **Build and deployment → Deploy from a branch**를 선택합니다.
6. Branch를 `main`, 폴더를 `/(root)`로 선택하고 **Save**를 누릅니다.
7. 몇 분 기다린 뒤 같은 Pages 화면에 표시되는 공개 URL을 확인합니다. 보통 `https://사용자명.github.io/bungeoppang-vote/` 형태지만 실제 URL은 GitHub가 표시한 값을 사용하세요.
8. 사이트를 열어 익명 로그인이 되고, 투표 1건을 제출한 뒤 다른 브라우저에서 결과 숫자가 갱신되는지 시험합니다.

## C. 업데이트
파일을 수정한 뒤 같은 GitHub 저장소에 다시 업로드/커밋하면 Pages가 자동으로 업데이트됩니다.

## 보안 및 개인정보
- 이 사이트는 닉네임/전화번호를 수집하지 않고, 선택 항목과 서버 생성 시각만 저장합니다.
- 공개 투표 문서는 결과 집계를 위해 누구나 읽을 수 있습니다. 이름, 이메일, 전화번호, UID를 결과 문서에 넣지 마세요.
- 익명 인증은 편리하지만 강한 신원 확인이 아닙니다. 악의적인 반복 투표를 완전히 막지는 못합니다.
- 무료 요금제 한도/조건은 변경될 수 있습니다. Firebase 콘솔에서 현재 요금제와 사용량을 확인하세요.
- 실제 운영 전 두 브라우저로 테스트하고, Firebase Authentication과 Firestore Rules가 모두 설정됐는지 확인하세요.
