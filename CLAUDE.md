# iRMS 위협정보 App

위협정보 앱. 현재는 공통 AppLayout에 "아직 서비스 하지 않습니다." 메시지만 출력하는 placeholder.

## 책임

- 추후 위협정보 기능 구현 예정

## 고유 규칙

- 독립 실행 시 Vite dev server 포트 3011 사용
- 게이트웨이 경로: `/threat/`

## 앱·기능 권한 (필수)

- 페이지 진입은 `useAppAccess("/threat")`, **API 를 부르는 메뉴·버튼은 모두 `useFeatures("/threat").can(<기능 키>)` 로 숨긴다**
- 역할(`user.role === ...`)로 직접 분기하지 않는다 — 직위·팀 제한은 관리자가 admin 앱 → 앱 상세 → 기능 권한에서 정한다
- 기능 키는 `src/features.ts` 에 두고 BE 서비스 `src/features.py` 와 같은 값을 쓴다. 새 기능이면 BE 에 먼저 추가한다
- FE 는 숨기기만 한다. 실제 차단은 BE `feature_dependency` 가 JWT·API 키 모두 같은 규칙으로 한다 (403). 상세: `common/docs/auth.md` "useFeatures"
