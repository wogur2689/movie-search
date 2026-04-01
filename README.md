# Movie Search

TMDB API를 활용해 인기 영화와 검색 결과를 보여주는 Vue 기반 웹 애플리케이션입니다.  
영화관 분위기의 다크 UI를 적용하고, 컴포넌트 분리 중심으로 구조화해 재사용성과 유지보수성을 높였습니다.

## 프로젝트 소개

- **프로젝트명**: Movie Search
- **개발 목적**: 외부 API 연동, 상태 관리, 컴포넌트 설계 역량을 보여주기 위한 개인 포트폴리오 프로젝트
- **핵심 포인트**
  - TMDB API 연동 (인기 영화 조회 / 검색)
  - 로딩/에러/빈 결과 상태 처리
  - 재사용 가능한 Vue 컴포넌트 설계
  - 반응형 레이아웃 및 커스텀 UI 구현

## 데모 기능

- 인기 영화 목록 표시
- 영화 제목 기반 검색
- 포스터/제목/평점/개봉연도 렌더링
- API 키 누락 및 요청 실패 시 사용자 친화적 메시지 표시

## 기술 스택

- **Frontend**: Vue 3 (Composition API), Vite
- **Language**: JavaScript, HTML, CSS
- **API**: [TMDB API](https://www.themoviedb.org/documentation/api)

## 컴포넌트 구조

```text
src/
├─ App.vue
└─ components/
   ├─ HeroHeader.vue
   ├─ MovieSearchForm.vue
   ├─ MovieGrid.vue
   └─ MovieCard.vue
```

- `App.vue`: 데이터 요청, 상태 관리, 화면 조합
- `HeroHeader.vue`: 상단 타이틀/소개 영역
- `MovieSearchForm.vue`: 검색 입력/제출 UI
- `MovieGrid.vue`: 영화 목록 그리드
- `MovieCard.vue`: 개별 영화 카드 렌더링

## 실행 방법

### 1) 의존성 설치

```sh
npm install
```

### 2) 환경 변수 설정

1. [TMDB API 설정 페이지](https://www.themoviedb.org/settings/api)에서 API 키를 발급합니다.
2. 프로젝트 루트에 `.env` 파일을 생성합니다. (`.env.example` 참고)
3. 아래 값을 입력합니다.

```sh
VITE_TMDB_API_KEY=your_tmdb_api_key_here
```

### 3) 개발 서버 실행

```sh
npm run dev
```

### 4) 프로덕션 빌드

```sh
npm run build
```

## 트러블슈팅

- **API 키 오류**
  - `.env` 파일명과 `VITE_TMDB_API_KEY` 키 이름이 정확한지 확인
  - 서버 실행 중에 `.env`를 수정했다면 개발 서버 재시작
- **데이터가 안 보일 때**
  - 브라우저 개발자도구 Network 탭에서 TMDB 요청 상태 코드 확인

## 개선 예정 사항

- 장르 ID를 실제 장르명으로 매핑
- 무한 스크롤 또는 페이지네이션
- 영화 상세 모달/상세 페이지
- 즐겨찾기 기능(LocalStorage)

## 포트폴리오 어필 포인트

- API 연동부터 예외 처리까지 사용자 경험을 고려해 구현
- 단일 파일에 몰아넣지 않고 컴포넌트 단위로 책임을 분리
- 기본 템플릿 스타일을 프로젝트 요구사항에 맞게 재구성해 PC/모바일 대응
