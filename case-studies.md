# 공개용 포트폴리오 케이스 스터디

이 문서는 공개 포트폴리오에 올릴 수 있는 버전의 초안이다. 사내명, 내부 URL, 실명, 실제 데이터는 모두 익명화한다.

## Case Study 1. 업무 보고 자동화 도구

### Summary

매주 반복되는 업무 보고서 작성과 커밋 이력 확인을 자동화한 Python CLI 도구입니다. Markdown outline을 보고서 본문으로 변환하고, 누락된 진행 상태와 날짜를 게시 전에 검증합니다.

### Background

팀 회의 전 개인 업무 내용을 정리해 wiki에 올리는 과정은 매주 반복되었습니다. 수동 작성은 시간이 걸릴 뿐 아니라, 날짜나 진행률이 빠지면 다시 확인해야 했습니다. 개발 중인 여러 프로젝트의 Git 커밋 이력과 실제 업무 내용을 대조하는 과정도 별도로 필요했습니다.

### Problem

- 매주 비슷한 형식의 보고서를 수동 작성
- 진행률, 완료 여부, 목표일 누락 가능성
- 커밋 이력과 실제 업무 항목의 분리
- wiki 동시 수정 시 덮어쓰기 위험

### Solution

보고서 원본을 Markdown outline으로 작성하고, Python CLI가 이를 wiki 형식으로 변환하도록 했습니다. 상태와 날짜가 부족한 항목은 게시 전 validation에서 잡아내고, API 게시 시 wiki version을 사용해 동시 수정 충돌을 방지하도록 설계했습니다. GitLab API를 별도 스크립트로 연결해 커밋 이력을 보고 후보 문장으로 정리할 수 있게 했습니다.

### Implementation

- Python `argparse` 기반 CLI
- outline parser와 status normalization
- 날짜/진행률/상태 validation
- wiki section body generator
- Redmine API publish flow
- GitLab project search와 commit summary flow
- API key는 환경변수로만 사용

### Result

- 보고서 원본과 최종 출력 형식을 분리했습니다.
- 누락 확인을 자동화해 게시 전 검토 품질을 높였습니다.
- 반복 보고 흐름을 향후 다른 프로젝트에도 적용 가능한 구조로 만들었습니다.

### What I Learned

자동화는 단순히 시간을 줄이는 일이 아니라, 반복 업무의 기준을 만드는 일이라는 것을 배웠습니다. 특히 게시 자동화처럼 실수 비용이 있는 작업은 preview, validation, confirm step을 분리하는 것이 중요했습니다.

### Before Publishing

- 내부 URL 제거
- 실제 프로젝트명 익명화
- 샘플 outline과 샘플 output 교체
- 스크린샷 준비

## Case Study 2. AI 시험지 생성/분석 도구

### Summary

영어 지문을 기반으로 시험지를 생성하고, 품질 검증과 DOCX 출력을 지원하는 AI-assisted 교육 도구입니다. 분석 플랫폼은 OCR provider와 report API를 분리해 확장 가능한 구조로 설계했습니다.

### Background

시험지 제작은 지문 분석, 문항 유형 선정, 문항 생성, 답안 생성, 문서 형식 맞춤, 품질 검토를 반복해야 하는 작업입니다. 생성형 AI를 사용하면 초안은 빠르게 만들 수 있지만, 문항 품질과 출력 형식, 정답 분포를 검증하는 과정이 필요했습니다.

### Problem

- AI 생성 결과의 품질이 매번 일정하지 않음
- DOCX 출력 형식과 실제 교재/시험지 스타일 차이
- 중복 문항, 빈 선택지, 정답 분포 편향 등 검증 필요
- 실제 시험지/학생 데이터는 테스트에 사용하기 어려움

### Solution

로컬 Codex CLI 기반 생성 workflow를 만들고, 생성 결과를 preview/edit/JSON 검토 단계로 분리했습니다. validation warning과 품질 점수를 제공해 사용자가 재생성하거나 수정할 수 있게 했고, 반복되는 패턴은 GitHub-backed pattern DB에 저장할 수 있게 했습니다. Analyzer는 FastAPI 기반으로 별도 구성해 OCR provider, report, pattern summary API를 분리했습니다.

### Implementation

- Node.js 기반 local server
- Codex CLI generation flow
- DOCX generation
- local Tesseract OCR support
- validation warning과 one-click retry
- GitHub contents API 기반 pattern DB
- FastAPI analyzer
- OCR provider abstraction
- mock provider와 synthetic fixture

### Result

- 지문 입력부터 학생용/답안용 DOCX 출력까지 이어지는 end-to-end workflow를 구성했습니다.
- AI 결과물을 검증 가능한 단계로 나누어 사용자가 품질을 확인할 수 있게 했습니다.
- 민감 데이터 없이도 테스트 가능한 mock/synthetic 구조를 만들었습니다.

### What I Learned

AI 기반 제품은 생성 자체보다 검증과 편집 흐름이 중요하다는 것을 배웠습니다. 사용자가 결과를 신뢰하려면 AI가 만든 답뿐 아니라, 왜 경고가 떴고 어떤 부분을 수정해야 하는지 볼 수 있어야 했습니다.

### Before Publishing

- 실제 학교/학생/저작권 자료 제거
- synthetic 지문과 출력 예시로 교체
- README 한글 인코딩 정리
- validation warning 화면 캡처

## Case Study 3. Privacy-first Baby Care App

### Summary

육아 기록, 가족 공유, 아이별 앨범, AI 후보 분류, 모니터링 확장성을 고려한 Flutter 앱입니다. 민감한 사진/영상과 육아 기록을 다루기 때문에 local-first, permission, uncertainty를 중심으로 설계했습니다.

### Background

육아 기록은 메모, 채팅, 사진, 가족 간 전달로 흩어지기 쉽습니다. 가족 공유 기능은 편리하지만 아이 사진과 영상은 민감한 정보이기 때문에 권한과 검토 흐름이 중요합니다. AI 분류나 수면 영상 분석 기능도 확정적 판단이 아니라 참고용 후보로 다뤄야 했습니다.

### Problem

- 육아 기록과 미디어가 여러 앱에 흩어짐
- 가족 구성원별 접근 권한이 불명확할 수 있음
- AI 사진/영상 분석 결과를 확정 판단처럼 보이게 하면 위험
- 향후 카메라/AI/provider 변경 가능성 필요

### Solution

Flutter 앱에서 care event, health record, family sharing, album classification, monitor role을 도메인 모델로 분리했습니다. AI 사진 분류는 후보 태그와 review state를 갖도록 모델링했고, 불확실한 수면/자세/음성 분석 결과는 confidence, `UNKNOWN`, `OCCLUDED` 같은 상태를 포함하도록 설계했습니다. WebRTC와 Cloudflare Worker 기반 시그널링 실험도 진행했습니다.

### Implementation

- Flutter/Riverpod app structure
- Drift/SQLite local repository
- family sharing policy model
- album classification domain
- mock photo classifier provider
- mock LLM report assistant
- camera provider abstraction
- WebRTC signaling experiment

### Result

- 육아 기록과 미디어 공유를 local-first domain model로 정리했습니다.
- AI 결과를 후보/검토/불확실성 중심으로 다루는 UX 원칙을 반영했습니다.
- provider 교체와 향후 backend 확장을 고려한 구조를 만들었습니다.

### What I Learned

민감한 도메인의 AI 기능은 "정답을 보여주는 것"보다 "불확실성을 안전하게 표현하는 것"이 중요했습니다. 기능 욕심보다 사용자 신뢰와 안전한 표현 경계를 먼저 잡는 것이 필요했습니다.

### Before Publishing

- demo baby data 생성
- 실제 아이 사진 제거
- 앱 스크린샷 준비
- MVP/실험/향후 기능 구분

## Case Study 4. Local-first Inventory App

### Summary

가정 내 식재료, 조리 음식, 생활용품의 위치와 유통기한을 local-first로 관리하는 Flutter 앱입니다. 보관 위치 트리, 검색, 유통기한 목록, 바코드 스캔, 제품명 조회 흐름을 구현했습니다.

### Background

냉장고와 수납장의 물건은 위치와 유통기한을 기억하기 어렵고, 같은 물건을 다시 사거나 유통기한이 지난 뒤 발견하는 일이 자주 생깁니다. 가족이 함께 쓰는 앱이라면 빠른 등록, 위치 검색, 알림, 향후 동기화 구조가 필요했습니다.

### Problem

- 물건의 위치와 유통기한이 기억에 의존
- 등록이 불편하면 앱 사용이 유지되기 어려움
- 로컬 우선 사용성과 향후 sync 확장성의 균형 필요
- OCR/음성/알림 같은 기능 확장 가능성 필요

### Solution

Flutter/Riverpod/Drift 기반 local-first 앱을 구현했습니다. 물품 CRUD, storage unit/location tree, 검색, 유통기한 임박 목록을 MVP로 두고, 바코드 스캔과 Open Food Facts 조회를 추가했습니다. Drift/SQLite를 source of truth로 두고 향후 sync-ready data model로 확장 가능성을 열어두었습니다.

### Implementation

- Flutter/Riverpod app
- go_router navigation
- Drift/SQLite persistence
- inventory repository
- location picker sheet
- barcode scanner
- Open Food Facts lookup
- expiry notification structure

### Result

- 재고/위치/유통기한을 한 흐름으로 관리하는 앱 구조를 만들었습니다.
- local-first DB 기반으로 오프라인 중심 사용성을 확보했습니다.
- OCR, 음성 입력, sync, 알림으로 확장 가능한 설계를 유지했습니다.

### What I Learned

생활형 앱은 기능 수보다 입력 마찰을 줄이는 것이 중요했습니다. 사용자가 빠르게 등록하고 나중에 쉽게 찾을 수 있도록 데이터 모델과 화면 흐름을 함께 설계해야 했습니다.

### Before Publishing

- demo inventory 구성
- 앱 화면 캡처
- post-MVP 기능과 현재 구현 기능 분리
- 공개 가능한 GitHub README 정리
