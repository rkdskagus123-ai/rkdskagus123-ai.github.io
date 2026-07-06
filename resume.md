# 강남현

AI 업무 자동화 / 운영 도구 / 백엔드 개발자

- Email: `rkdskagus123@gmail.com`
- Phone: `PDF 이력서에 기재`
- GitHub: [GitHub profile](https://github.com/namhyunkang)
- Portfolio: [Web portfolio](https://namhyunkang.github.io/)

## Summary

C/C++, RTOS, Linux 기반 장비 SW 개발 경험을 바탕으로 Python, FastAPI, AI workflow를 활용해 반복 업무와 운영 흐름을 도구화하는 개발자입니다. Redmine/GitLab 주간보고 자동화로 기록/작성까지 1시간 이상 걸리던 흐름을 10분 미만의 리뷰 중심 작업으로 줄였고, 장비 운영 Web UI와 실시간 센서 데이터 도구를 구현하며 실행 전 검증과 재현 가능한 workflow를 함께 남기는 방식으로 개발합니다.

## Skills

- Automation/Backend: Python, FastAPI, REST API, SQLite, Celery, Docker, Redmine API, GitLab API, GitHub Contents API
- AI Workflow: Codex CLI, OCR provider abstraction, Tesseract OCR, validation workflow, prompt/workflow design
- Mobile/Frontend: Flutter, Riverpod, go_router, Drift/SQLite, JavaScript, Vite
- Embedded/Device: C, C++, RTOS, Linux, sensor data processing, NXP Wi-Fi, TR-069
- Tools: Git, GitHub, GitLab, PowerShell, Visual Studio, Eclipse, Android Studio

## Experience

### (주)벤탑스 / SW 개발

2024.08 - 재직중

- C++/RTOS 기반 TOF 센서 및 FND 제어 로직을 구현하고, 거리 측정 상태 표시와 통신/예외 처리 흐름을 개선했습니다.
- 기존 Windows 프로그램 중심의 장비 설정 흐름을 Python/FastAPI/JavaScript 기반 Web UI와 REST API로 확장해 OS 의존성을 낮췄습니다.
- C# Windows 애플리케이션에서 460,800 baud, 1ms 주기의 센서 데이터를 CSV 저장, 실시간 모니터링, 그래프 저장으로 확인하는 구조를 구현했습니다.
- 저사양 PC와 CPU 환경 차이에 따른 버벅임과 실행 순서 이슈를 줄이기 위해 수신/파싱/UI 갱신 흐름을 분리했습니다.
- 장비 설정 변경, 상태 모니터링, 로그 확인, FTP/CLI 제어 등 운영 기능을 Web UI로 제공해 장비 진단과 유지보수 흐름을 단순화했습니다.
- Python CLI로 Redmine/GitLab 주간보고 자동화 도구를 구현해 기록/작성까지 1시간 이상 걸리던 업무를 10분 미만의 리뷰 중심 workflow로 줄였습니다.
- Claude/Codex 기반 코드 리뷰, 보안 리스크 점검, 문서화 흐름을 업무에 적용해 반복 점검을 구조화했습니다.

### (주)이노피아테크 / SW 개발

2021.04 - 2023.09

- Linux 기반 STB 환경에서 Java/C++ 기반 TR-069 서비스 모듈을 구현해 원격 설정 및 파라미터 관리 기능을 구성했습니다.
- 기존 Java 코드를 객체지향 구조로 재정리해 유지보수성과 확장성을 개선했습니다.
- 내부 애플리케이션의 통신 구조와 설치/운영 흐름을 정리하고, 다른 프로젝트에도 적용 가능한 구조로 재사용성을 높였습니다.

### (주)포스로직 / SW 개발

2020.05 - 2020.09

- C++ 기반 집합, 삼각형, 폴리곤, 타원 등 기하 정보 처리 로직을 구현했습니다.
- Sphere-Sphere Volume, Polygon Intersection 등 기하 연산 계산 로직을 구현했습니다.

### 유니쎌(주) / 연구원

2018.05 - 2019.01

- 내부 프로젝트의 기능 개발과 유지보수에 참여했습니다.
- 운영 중 발생한 구조/기능 이슈를 확인하고 보완 작업을 수행했습니다.

## Projects

### Redmine/GitLab 주간보고 자동화

Python CLI로 업무 outline을 Redmine wiki 주간보고 형식으로 변환하고, 상태/진행률/날짜 누락 검증과 GitLab 커밋 후보 요약을 지원하는 자동화 도구를 구현했습니다. 기존에는 기록과 보고 작성까지 1시간 이상 걸리던 흐름을 자동 생성 후 10분 미만 리뷰로 줄였고, API key는 환경변수로만 사용하며 게시 전 preview/validation/confirm 흐름을 분리했습니다.

Tech: Python, Redmine API, GitLab API, Markdown/CommonMark, PowerShell

### Exam Maker / Exam AI Analyzer

개인 프로젝트로 로컬 Codex CLI 기반 시험지 생성 도구와 FastAPI 기반 분석 플랫폼을 구현했습니다. 지문 입력, 문항 생성, 품질 검증, DOCX 출력, 답안 생성 workflow를 구성하고, validation warning 기반 재시도 흐름을 추가했습니다. Analyzer에서는 OCR provider, 분석 리포트, pattern summary API를 분리하고 mock provider와 synthetic fixture 기반 테스트 구조를 만들었습니다.

Tech: Node.js, JavaScript, Python, FastAPI, Pydantic, SQLite, Tesseract OCR, DOCX generation, Docker

### Smart Baby

개인 프로젝트로 Flutter/Riverpod/Drift 기반 육아 기록 앱을 구현했습니다. 수유, 수면, 기저귀, 투약, 성장 기록과 아이별 앨범, 가족 공유 권한 모델을 설계했으며, AI 사진 분류와 수면 영상 분석 기능은 후보/검토/불확실성 중심으로 모델링했습니다.

Tech: Flutter, Dart, Riverpod, Drift/SQLite, PocketBase, WebRTC, Cloudflare Worker, ML Kit

### Jungdon / My Refrigerator

개인 프로젝트로 Flutter/Riverpod/Drift 기반 local-first 재고 관리 앱을 구현했습니다. 물품 CRUD, 보관 위치 트리, 검색, 유통기한 임박 목록, 바코드 스캔 및 Open Food Facts 제품명 조회 기능을 구성했습니다.

Tech: Flutter, Dart, Riverpod, go_router, Drift/SQLite, mobile_scanner, HTTP API

## Education

- 단국대학교(경기), 모바일시스템공학 졸업
- Simon Fraser University, 기계공학 수학
- West Vancouver Secondary School 졸업

## Certification / Language

- 정보처리기사, 2017.05
- TOEIC 945, 2023.07
