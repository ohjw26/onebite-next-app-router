# onebite-next-app-router

한입 코딩(이정환님)의 *한 입 크기로 잘라먹는 Next.js* 강의 중 **App Router** 파트 학습용 저장소입니다.

도서 검색 애플리케이션을 예제로 Next.js 15의 App Router 기반 라우팅, 데이터 페칭, 캐싱, 스트리밍, Server Actions, 병렬/인터셉팅 라우트, SEO 등을 다룹니다.

## 기술 스택

- **Next.js** 15.5.14 (App Router)
- **React** 19
- **TypeScript** 5
- **CSS Modules**
- **ESLint** 9 (`eslint-config-next`)

## 구성

이 레포는 강의 진도에 맞춰 섹션별 독립 프로젝트로 구성되어 있습니다.

```
.
├── section03/   # App Router 입문 (Page Router 마이그레이션)
└── section04/   # App Router 고급 (Server Actions, 병렬/인터셉팅 라우트)
```

각 섹션은 별개의 Next.js 프로젝트이므로 개별적으로 의존성을 설치하고 실행합니다.

### section03 — App Router 입문

```bash
cd section03
npm install
npm run dev
```

- 라우트 그룹 `(with-searchbar)`
- 동적 라우팅 `book/[id]`
- 서버/클라이언트 컴포넌트 구분
- 페이지 캐싱, 스트리밍, 에러 처리
- 도서 검색 페이지
- `legacy_src/`: Page Router → App Router 마이그레이션 비교용으로 보존

### section04 — App Router 고급

```bash
cd section04
npm install
npm run dev
```

- Server Actions (`actions/`)
- 병렬 라우트 (`parallel/`)
- 인터셉팅 라우트 + 모달 패턴 (`@modal`)
- `not-found.tsx` 커스터마이징
- 이미지 최적화, SEO 메타데이터
- Vercel 배포

## 디렉토리 구조 (공통 패턴)

```
src/
├── app/
│   ├── layout.tsx              # 루트 레이아웃
│   ├── (with-searchbar)/       # 검색바를 공유하는 라우트 그룹
│   │   ├── layout.tsx
│   │   ├── page.tsx            # 홈
│   │   └── search/page.tsx     # 검색 결과
│   ├── book/[id]/page.tsx      # 도서 상세 (동적 라우팅)
│   └── globals.css
├── components/                 # 공용 컴포넌트
├── mock/                       # 목 데이터 (백엔드 미사용 시)
└── types.ts
```

section04에는 추가로 `actions/`, `util/`, `@modal`, `parallel/`이 들어갑니다.

## 학습 포인트

- **라우팅**: App Router 파일 시스템 라우팅, 라우트 그룹, 동적/병렬/인터셉팅 라우트
- **렌더링**: Server Components / Client Components 구분, Streaming, Suspense
- **데이터 페칭**: 서버 컴포넌트에서의 `fetch`, 캐싱 전략 (`force-cache`, `no-store`, revalidate)
- **상호작용**: Server Actions, Form 처리
- **최적화**: `next/image`, `next/font`, SEO 메타데이터
- **배포**: Vercel

## 관련 레포

- **Page Router 파트**: [onebite-next-page-router](https://github.com/ohjw26/onebite-next-page-router) — 강의 전반부 Page Router 학습 (section02)
- **백엔드 API 서버**: [onebite-next-server](https://github.com/ohjw26/onebite-next-server) — 강의에서 제공한 NestJS + Prisma 기반 도서 API 서버
