# Hoisting

## 호이스팅

호이스팅은 단어적 뜻으로 보면 끌어올리다 라는 뜻이 있다.

> JavaScript 호이스팅은 인터프리터가 코드를 실행하기 전에 함수, 변수, 클래스 또는 임포트(import)의 선언문을 해당 범위의 맨 위로 끌어올리는 것처럼 보이는 현상 -MDN-

즉, 메모리 공간에 선언 전에 미리 할당하는 것을 의미한다.

## 변수와 함수의 호이스팅

```
console.log(myVar); // undefined
console.log(myLet); // ReferenceError: myLet is not defined

var myVar = 5;
let myLet = 10;
```

변수선언은 호이스팅에 의해 맨 위로 끌어올려지고,
var 같은 경우 선언되기 전에 사용을 하면 `ùndefined` 오류가 나는걸 볼 수 있다.

`let`과 `const`로 선언된 변수는 초기화되지 않은 상태에서 접근하면 ReferenceError를 발생 시킨다.

## 함수 표현식과 화살표 함수 호이스팅

```
console.log(add(1, 2)); // TypeError: add is not a function

var add = function(a, b) {
  return a + b;
};

var addArrow = (a, b) => a + b;
```

함수 표현식과 화살표 함수는 호이스팅되지 않는다.

함수 표현식이 변수에 할당되는 시점에만 존재하기 때문에, 선언 이전에 참조하려고 하면 ReferenceError가 발생하지 않지만, 실제로 함수를 호출하려면 변수에 할당된 후에만 가능합니다.

즉, 함수 표현식은 선언 이전에 사용할 수 없으며, 변수에 할당된 후에만 함수를 호출할 수 있습니다.

## 함수 선언 호이스팅

함수 선언은 호이스팅되며, 선언 이전에 호출될 수 있고, 이는 함수가 메모리에 할당되고 초기화되는 과정을 통해 가능하다.

```
sayHello(); // "Hello, World!"

function sayHello() {
  console.log("Hello, World!");
}
```

결론 : 이번 TIL 호이스팅을 통해 변수는 물론 함수 표현식과 함수 선언에 대한 호이스팅에 대한 이해도를 높일 수 있었습니다.
