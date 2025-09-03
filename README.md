# 로블록스 맵 제작 템플릿

## 목차

- [시작하기](#시작하기)
- [Git 사용 가이드라인](#git-사용-가이드라인)
- [코드 구조 및 스타일 가이드](#코드-구조-및-스타일-가이드)

## 시작하기

새 프로젝트를 시작할 때 다음 단계를 따라주세요:

1. 이 저장소를 템플릿으로 사용하여 새 프로젝트를 생성합니다.
2. 로컬 환경에 프로젝트를 클론합니다.
3. 필요한 확장 프로그램을 설치합니다:
   - **Rojo**: Roblox Studio와 외부 코드 에디터를 연결하는 플러그인
   - **Visual Studio Code**: 권장 IDE
   - **StyLua**: Lua 코드 포맷터

## Git 사용 가이드라인

우리 팀은 다음과 같은 브랜치 전략을 사용합니다:

### 주요 브랜치

- **main**: 초기 커밋과 완성된 버전만 커밋됩니다.
- **develop**: 초기 커밋 이후 완성된 기능들이 커밋됩니다.

### 기능 개발 브랜치

- **feature**: develop 브랜치에서 파생됩니다.
- 명명 규칙: `feature/기능-이름` (예: `feature/ui-refactor`)
- 커밋 메시지:
  - 개발 중: 의미 있는 구현 단위마다 적절한 메시지로 커밋
  - 기능 완성 시: `feat: 기능 설명` 형식으로 커밋 (예: `feat: UI Refactored`)
- 기능 완성 후: develop 브랜치로 병합

## 코드 구조 및 스타일 가이드

### 파일 구조

```
src/
├── client/
│   ├── common/
│   ├── 미니게임1/
│   └── 미니게임2/
├── server/
│   ├── common/
│   ├── 미니게임1/
│   └── 미니게임2/
└── shared/
```

- **client**: 클라이언트 측 스크립트를 기능별 폴더로 구분하여 저장
- **server**: 서버 측 스크립트를 기능별 폴더로 구분하여 저장
- **shared**: ReplicatedStorage와 연결, 서버와 클라이언트 모두에서 접근 필요한 스크립트만 기능별 폴더로 구분하여 저장

### 네이밍 규칙

- **Rojo 폴더**: 소문자로 시작 (예: `client`, `server`)
- **스크립트 파일**: PascalCase (예: `PlayerManager.luau`)
  - 예외: `init.luau` 또는 `init.client.luau`, `init.server.luau` 는 소문자 유지
- **변수**: camelCase (예: `playerHealth`, `isGameOver`)
- **함수**: 동사로 시작하는 camelCase (예: `calculateDamage()`)
- **클래스**: 명사 형태의 PascalCase (예: `Player`, `RankSystem`)
- **상수**: SCREAMING_SNAKE_CASE (예: `MAX_PLAYERS`)

### 코드 구조

스크립트 내 요소 배치 순서:

1. GetService 호출
2. require 문
3. 클래스 정의
4. 상수
5. 변수
6. 로컬 함수
7. 글로벌 함수

### 함수 작성 가이드라인

- 함수는 가능한 한 작고 단일 책임을 가지도록 작성합니다.
- 복잡한 로직은 여러 작은 함수로 분리하여 가독성을 높입니다.

### 주석 작성

- 코드의 '왜'를 설명하는 주석을 작성합니다.
- 복잡한 알고리즘에 대해서는 상세한 설명을 추가합니다.
