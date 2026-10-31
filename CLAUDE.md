# CLAUDE.md — 회의비 증빙 자동 검수 Agent: 프론트엔드 (7조)

이 레포는 **담당자 화면(프론트엔드)**이다. 백엔드·검수 로직·메일 연동·결정 문서는 비공개 레포 `upstage-cnu-7team/meeting-fee-review-agent-back`에 있다(2026-10-31 분리).
새 세션은 이 파일 → `docs/frontend-api.md`(API 약속, 공개용 사본) 순서로 본다. **이 레포는 공개라 내부 운영 정보(메일 경로, 계정, 주소)는 넣지 않는다.**

## 스택·실행
- Vite + React 19 + TypeScript + TanStack Query + react-router
- `npm install && npm run dev` → http://localhost:5173 (`/api`는 `vite.config.ts`에서 localhost:8000 백엔드로 프록시)
- 배포: Vercel(`main`에 push하면 자동). `/api/*`는 `vercel.json`에서 백엔드 공개 주소로 넘긴다.

## 약속
- API 모양은 `docs/frontend-api.md`가 기준이다(정본은 백엔드 레포, 바뀌면 그쪽이 먼저 바뀐다).
- 조건 이름·개수를 하드코딩하지 않는다. `checks[]`를 그대로 그린다(F00 양식 확인, `evidence.alternatives` 두 방식 계산 포함).
- 학번·카드번호는 서버가 마스킹해서 준다. 콘솔에 응답 본문을 남기지 않는다.
