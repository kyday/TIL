# useCallback

```
`메모이제이션`이란?

메모이제이션(memoization)은 동일한 계산을 반복해야 할 때, 이전에 계산한 값을 메모리에 저장함으로써 동일한 계산의 반복 수행을 제거하여 프로그램 실행 속도를 빠르게 하는 기술
```

```
const cachedFn = useCallback(fn, dependencies)
```

useCallback은 메모이제이션 기술 중 하나로, 함수를 메모이징하여 불필요한 재생성과 재렌더링을 방지하는 데 사용됩니다.

해당 함수가 의존하고 있는 값들이 바뀌지 않는다면 함수를 새로 생성하지 않고 기존 함수를 계속 반환한다.

## 매개변수

첫번째 인자 값에는 캐시하려는 함수 값이 들어간다. ( 다시 렌더링할 때마다 캐시하려는 함수 정의 )

두번째 인자 값에는 코드 내부에서 참조 값이 들어간다.

## 언제 써야할까?

#### 자식 컴포넌트로 함수 전달

```
function ProductPage({ productId, referrer, theme }) {
  // Tell React to cache your function between re-renders...
  const handleSubmit = useCallback((orderDetails) => {
    post('/product/' + productId + '/buy', {
      referrer,
      orderDetails,
    });
  }, [productId, referrer]); // ...so as long as these dependencies don't change...

  return (
    <div className={theme}>
      {/* ...ShippingForm will receive the same props and can skip re-rendering */}
      <ShippingForm onSubmit={handleSubmit} />
    </div>
  );
}

```

#### useEffect의 의존성으로 사용

```
useEffect(() => {
  fn(a, b);
}, [a, b]);
```

```
const memoizedCallback = useCallback(() => {
  doSomething(a, b);
}, [a, b]);

useEffect(() => {
  memoizedCallback();
}, [memoizedCallback]);

```

#### 커스텀 Hook 최적화

```
function useRouter() {
  const { dispatch } = useContext(RouterStateContext);

  const navigate = useCallback((url) => {
    dispatch({ type: 'navigate', url });
  }, [dispatch]);

  const goBack = useCallback(() => {
    dispatch({ type: 'back' });
  }, [dispatch]);

  return {
    navigate,
    goBack,
  };
}
```

## 놀라운 사실..

```
export function useCallback<T>(
  callback: T,
  deps: Array<mixed> | void | null,
): T {
  return useMemo(() => callback, deps);
}
```

useMemo는 아직 TIL에 기록은 안했지만

useCallback은 `함수`를 메모이제이션을 하고

useMemo는 `값`을 메모이제이션을 해서 사실 다르다고 생각을 하였는데

useCallback 내부 로직을 봤는데.. 세상에 useMemo를 그대로 사용하고 있다.

사실 useCallback을 사용을 해왔지만 너무나 놀라운 사실인거 같다.

참조) https://github.com/facebook/react/blob/4ce89a58dac5287a2c7fc454e86562297e97a6d9/packages/react-dom/src/server/ReactPartialRendererHooks.js#L446
