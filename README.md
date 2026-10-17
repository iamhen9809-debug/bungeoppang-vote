# 붕어빵 취향 투표 사이트 (Firebase 연결 완료)

- Firebase 프로젝트: bong-50241
- Firebase 익명 로그인과 Cloud Firestore가 활성화되어 있어야 합니다.
- Firestore 규칙은 함께 제공된 `firestore.rules` 내용과 동일해야 합니다. 사용자가 이미 게시한 규칙과 일치하도록 제작했습니다.
- GitHub Pages 등 정적 호스팅에 `index.html`과 `firebase-config.js` 두 파일을 **같은 폴더**에 업로드하면 됩니다.
- GitHub Pages에서는 Settings > Pages > Deploy from a branch > main / root 를 설정하세요.
- 사이트는 아직 공개되지 않았습니다. 배포 후 링크가 생성됩니다.
- 투표 완료 후 개인별 캐릭터는 익명 계정 UID에 따라 결정되며, 애니메이션은 CSS로 작동합니다.
- 서로 다른 사용자에게 우연히 같은 캐릭터가 나올 수 있습니다. 고유 이미지 보장은 아닙니다.
- 다른 브라우저/기기, 사이트 데이터 삭제로 익명 계정이 바뀌면 새 투표가 가능할 수 있습니다.
