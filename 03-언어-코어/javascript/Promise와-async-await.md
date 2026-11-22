# Promise와 async/await

## Why — 왜 필요한가?

- **Promise**는 비동기 작업의 최종 성공 값이나 실패 이유를 나중에 받을 수 있도록 표현하는 객체다.
- **async/await**는 Promise 기반 비동기 코드를 순차적으로 읽고 작성하기 쉽게 해준다.

## How — 어떻게 동작하는가?

- **Promise**: 비동기 작업의 결과를 나타내며, 세 가지 상태를 가진다.
  - **Pending**: 대기 상태 (아직 결과가 확정되지 않음)
  - **Fulfilled**: 성공 결과 확정
  - **Rejected**: 실패 이유 확정
- **async**: 함수를 호출하면 항상 Promise를 반환한다. 일반 값을 반환해도 그 값으로 이행되는 Promise가 반환된다.
- **await**: Promise의 결과를 기다리는 동안 **현재 async 함수의 실행을 일시 중단**한다. Promise가 이행되면 결과값을 받아 실행을 재개하고, 거부되면 `await` 위치에서 예외가 발생한다.

## Example — 실행 예제

```js
console.log('A');

async function run() {
  console.log('B');

  const value = await Promise.resolve(10);

  console.log('D', value);
  return value * 2;
}

const result = run();

console.log('C');

result.then((value) => {
  console.log('E', value);
});
```

**실행 결과**

```text
A
B
C
D 10
E 20
```

- `run()`은 `await`를 만나기 전까지 동기적으로 실행하므로 `B`가 출력된다.
- `await`에서 `run()`이 일시 중단되고, 호출한 쪽의 코드가 계속 실행되어 `C`가 출력된다.
- 이후 `run()`이 비동기적으로 재개되어 `D 10`을 출력하고, 반환한 Promise가 이행되면 `.then()` 콜백에서 `E 20`을 출력한다.

## 헷갈리기 쉬운 점

- `async` 함수에서 `return 10`을 작성해도 **함수 호출 결과는 Promise 객체**다.
- `await`로 얻는 값은 Promise 객체가 아니라 **Promise의 이행 결과값**이다.
- `await`는 JavaScript 전체를 멈추는 것이 아니라 **현재 async 함수의 실행만 일시 중단**한다.

## 면접 답변

> Promise는 비동기 작업의 최종 성공 값이나 실패 이유를 표현하는 객체입니다. async는 항상 Promise를 반환하는 함수를 선언하는 데 사용하며, await는 Promise의 결과가 확정될 때까지 현재 async 함수의 실행을 일시 중단합니다. 이때 JavaScript 전체가 멈추는 것은 아니며 다른 코드는 계속 실행될 수 있습니다. Promise가 이행되면 결과값을 받아 이후 코드가 비동기적으로 재개됩니다. 거부되면 await 위치에서 예외가 발생합니다.

## 참고자료

- [MDN — Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [MDN — async function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [MDN — await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)
