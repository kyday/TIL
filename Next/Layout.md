# Layout

## Next Layout

버전 13에서 Next.js는 공유 레이아웃, 중첩 라우팅, 로딩 상태, 오류 처리 등을 지원하는 React Server Components를 기반으로 구축된 새로운 앱 라우터를 도입하였는데 그 중에 layout은 세그먼트 및 해당 하위 항목에 대한 공유 UI를 할 수 있다.

## 어떻게 사용할까?

```
export default function DashboardLayout({
  children,
}: {
  children: React.ReactNode
}) {
  return <section>{children}</section>
}
```

- app/layout.js 루트 레이아웃이 있고
  루트 레이아웃은 Server Component 로 사용해야한다.

- 폴더 하위에 layout.jsx or layout.tsx를 만든다.

- Layout을 사용할때는 children값이 필수이다.

## 문제 해결

공통 layout을 만들고 싶어서 props로 받았다가 빌드가 안되는 현상이 있었다.

공식문서에서 알고보니.. Pages 와 달리 Layout 구성 요소 는 prop을 받지 않는다고 나와 있었다.

그래서 다음과 같은 방법으로 params를 사용하라고 나와있어서 해결을 하였다.

## params (optional) 사용법

```
export default function ShopLayout({
  children,
  params,
}: {
  children: React.ReactNode
  params: {
    tag: string
    item: string
  }
}) {
  // URL -> /shop/shoes/nike-air-max-97
  // `params` -> { tag: 'shoes', item: 'nike-air-max-97' }
  return <section>{children}</section>
}
```

- 레이아웃 컴포넌트는 params라는 프로퍼티를 받을 수 있다. (동적 경로(dynamic route)에서 추출한 파라미터 값이 포함)

참고) https://nextjs.org/docs/app/api-reference/file-conventions/layout
