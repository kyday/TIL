# Promise

자바스크립트에서 Promise는 비동기 작업을 처리할때 사용되는 객체입니다.

## Promise 인자

두 개의 콜백 함수로 `resolve`, `reject` 인자로 받습니다.

`resolve` 비동기 작업이 성공적으로 완료되었을 때 알려주는 객체

`reject`비동기 작업이 실패했을 때 알려주는 객체

```
let promise = new Promise(function(resolve, reject) {
  // 비동기 작업을 수행합니다.

  if (/* 작업이 성공적으로 완료되었다면 */) {
    resolve("작업이 성공적으로 완료되었습니다!");
  } else {
    reject(Error("작업이 실패했습니다."));
  }
});
```

## Promise 객체 처리

```
promise
    .then((value) => { // 성공했을 때 실행될 코드
    	console.log("Data: ", value);
    })
    .catch((error) => { // 실패했을 때 실행될 코드
     	console.error(error); 출력된다
    })
    .finally(() => { // 성공하든 실패하든 무조건 실행될 코드

    })

```

`.then(handleSuccess)` 은 첫 번째 인수는 프라미스가 이행되었을 때 실행되는 함수이고, 여기서 실행 결과를 받는다.

`.then(handleSuccess,handleError)`의 두 번째 인수는 프라미스가 거부되었을 때 실행되는 함수이고, 여기서 에러를 받는다.

```
promise.then(
  function(result) { /* 결과(result)를 다룹니다 */ },
  function(error) { /* 에러(error)를 다룹니다 */ }
);
```

`.catch((f))` 실패 상태가 되면 실패한 이유(실패 처리의 결과 값)를 catch()로 받을 수 있습니다.

```
const promise1 = new Promise((resolve, reject) => {
  throw new Error('Uh-oh!');
});

promise1.catch((error) => {
  console.error(error);
});
```
