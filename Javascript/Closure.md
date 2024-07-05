# Closure

오늘은 클로저에 대한 정리를 해보려고 한다.

## 클로저 (closure)

클로저는 함수와 함수가 선언된 어휘적 환경의 조합으로 내부함수가 외부함수에 접근할 수 있는 것을 뜻합니다.

## 어휘적 환경(lexical environment)

클로저가 생성이 되었을때 유효 범위(스코프)에 있는 모든 지역 변수를 사용하는 환경인데

쉽게 말해 함수가 어디서 정의되었는지에 따라서 그 함수가 사용할 수 있는 변수들이 결정된다.

## 예제

```
function init() {
  let name = "Mozilla"; // name은 init에 의해 생성된 지역 변수이다.
  function displayName() {
    // displayName() 은 내부 함수이며, 클로저다.
    console.log(name); // 부모 함수에서 선언된 변수를 사용한다.
  }
  displayName();
}
init();
```

init 함수 내에 정의된 displayName 함수는 외부 함수인 init 내부에 선언된 변수에 접근할 수 있으며, 이를 통해 클로저를 형성합니다. 위 코드를 실행하면 콘솔에 "Mozilla"라는 문자열이 출력된다.

## 특징

- 캡슐화 : 특정 변수들을 외부에서 접근할 수 없도록 숨길 수 있습니다.

- 모듈화 : 클로저를 사용하여 모듈 패턴을 구현할 수 있습니다. 외부 함수 내에서 변수와 함수를 정의하고 외부에 노출시키는 내부 함수를 반환함으로써 모듈 패턴을 생성

참조 ) https://developer.mozilla.org/ko/docs/Web/JavaScript/Closures
