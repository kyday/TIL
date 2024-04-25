# Event Loop

이벤트 루프에 대해서 알아보려고 한다.

우선 자바스크립트는 단일 쓰레드로 동작을 한다. 단일 쓰레드는 하나의 작업밖에 하지 못한다.

A -> B -> C 를 하나씩 처리한다. 하지만 비동기 작업을 처리하기 위해 "이벤트 루프"라는 것을 사용한다.

## 내부 동작 과정

![과정1](https://blog.kakaocdn.net/dn/ZPhwH/btsd15BHBgX/EDe61wsY0PBpFAk37PnqT1/img.png)

Heap : 자바스크립트 객체 (변수나 함수)들이 저장되는 곳

Call Stack : 자바스크립트에서 수행해야 할 명령어들을 순차적으로 한줄한줄 처리한다 (LIFO)

Web APIs(웹 브라우저에서 구현된 API 모음) : 비동기적인 작업을 수행한다.

Callback Queue : 비동기 작업이 완료되면 해당 작업의 콜백 함수가 콜백 큐에 추가 된다.

\*\* <b>이벤트 루프</b>는 호출 스택이 비어있는지 확인하고, 비어있으면 콜백 큐에서 콜백 함수를 콜 스택으로 이동시키는 과정이다.

## Callback Queue 종류

![과정2](https://blog.kakaocdn.net/dn/zl8dR/btsaipa7J1Z/ZPFXZZikQbb2s8b1cv6jNk/img.gif)

Callback Queue는 두 가지 종류의 Queue가 있는데
마이크로 태스트 큐(Micro task Queue에서)와 매크로 태스트 큐((Macrotask) task Queue에서)이다.

microtask queue에 있는 작업들이 우선적으로 처리되고, 그 다음에는 (Macrotask) task queue에 있는 작업들이 처리된다.

\*\* micro task Queue : Promise나 async/await, process.nextTick

\*\* task Queue : setTimeout, setInterval

---

AnimationFrame Queue : 웹 브라우저에서 애니메이션을 만들 때 사용되는 프레임들의 대한 큐이다.

requestAnimationFrame() : 매 프레임마다 호출되어 다음 프레임에 호출할 애니메이션을 지정하고, 이를 실행하는 데 사용

\*\* 프레임 : 애니메이션에서 사용되는 정지된 이미지이고 여러 프레임이 연속적으로 나타나면서 시간의 흐름에 따라 변화하는 이미지들로 구성

TMI : 오늘은 사이드프로젝트 오류를 고치느라.. TIL을 좀 늦게 작성하였다. 😂
