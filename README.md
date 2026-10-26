# Claude Next.js Starter

Next.js App Router 기반의 웹 스타터킷입니다. 헤더와 푸터가 있는 기본 레이아웃을 제공하므로 바로 페이지 개발을 시작할 수 있습니다.

## 기술 스택

- [Next.js](https://nextjs.org) 16 (App Router)
- React 19
- TypeScript
- Tailwind CSS 4
- [shadcn/ui](https://ui.shadcn.com) (base-nova 스타일)
- [lucide-react](https://lucide.dev) 아이콘
- [next-themes](https://github.com/pacocoursey/next-themes) 다크모드
- [sonner](https://sonner.emilkowal.ski) 토스트 알림
- [react-hook-form](https://react-hook-form.com) + [zod](https://zod.dev) 폼과 유효성 검사

## 시작하기

접속 후 **문서**(`/docs`)에서 사용법을, **예제**(`/examples`)에서 컴포넌트 동작을 확인할 수 있습니다.

```bash
npm install
npm run dev
```

브라우저에서 [http://localhost:3000](http://localhost:3000)을 열어 확인합니다.

## 폴더 구조

위 계층은 아래 계층만 import합니다. (`ui` ← `common` ← `layout` ← `app`)

```text
app/
  layout.tsx            # 루트 레이아웃 (테마, 헤더, 푸터, 토스트, 메타데이터)
  (marketing)/          # 홈, 소개, 문서, 예제 페이지 (URL에는 나타나지 않는 그룹)
  loading.tsx           # 로딩 화면
  error.tsx             # 오류 화면 (이 Next.js 버전은 reset이 아닌 retry 사용)
  global-error.tsx      # 루트 레이아웃 오류 화면
  not-found.tsx         # 404 화면
  sitemap.ts, robots.ts, opengraph-image.tsx   # SEO
  globals.css           # 전역 스타일과 테마 변수
components/
  ui/                   # shadcn/ui 컴포넌트 (버튼, 입력, 카드, 다이얼로그 등)
  common/               # 앱과 무관한 조합 컴포넌트 (EmptyState, ErrorState, FormField)
  layout/               # 헤더, 모바일 메뉴, 푸터, Container, Section, PageHeader, Breadcrumbs, ThemeToggle
  providers/            # ThemeProvider
config/
  site.ts               # 사이트 이름, 설명, URL, 메뉴 설정
lib/
  utils.ts              # cn 유틸리티
```

## 배포 전 확인

`config/site.ts`의 `url`은 개발용 주소(`http://localhost:3000`)입니다. sitemap, robots, 메타데이터에 쓰이므로 배포 전에 실제 주소로 바꿔야 합니다.

## 사이트 설정 변경

사이트 이름, 설명, 네비게이션 메뉴는 `config/site.ts`에서 수정합니다. 이 값은 헤더, 푸터, 메타데이터에 함께 반영됩니다.

```ts
export const navItems = [
  { title: "홈", href: "/" },
  { title: "소개", href: "/about" },
  { title: "문서", href: "/docs" },
  { title: "예제", href: "/examples" },
]
```

## shadcn/ui 컴포넌트 추가

이 프로젝트는 이미 `components.json`으로 설정되어 있으므로 `init`은 다시 실행하지 않아도 됩니다. 컴포넌트만 추가하면 됩니다.

```bash
npx shadcn@latest add card
npx shadcn@latest add dialog
```

추가된 파일은 `components/ui/`에 생성됩니다. 기존 파일을 덮어쓰지 않도록 주의하세요.

## 스크립트

| 명령어 | 설명 |
| --- | --- |
| `npm run dev` | 개발 서버 실행 |
| `npm run build` | 프로덕션 빌드 |
| `npm run start` | 빌드 결과 실행 |
| `npm run lint` | ESLint 검사 |
