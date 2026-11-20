# Promise와 async/await

## Promise와 async/await란?

**Promise**는 비동기 작업의 최종 성공 값이나 실패 이유를 나타내는 객체다.

**async/await**는 Promise 기반 비동기 코드를 순차적으로 읽고 작성하기 쉽게 해주는 문법이다.

---

## 왜 필요한가?

API 요청처럼 결과가 나중에 도착하는 작업은 즉시 최종 값을 얻을 수 없다.

Promise는 결과가 준비된 뒤 성공 값이나 실패 이유를 처리할 수 있게 하고, `async/await`는 이를 `.then()` 체인 대신 순차적인 코드 형태로 표현할 수 있게 한다.

---

## 어떻게 동작하는가?

Promise에는 세 가지 상태가 있다.

- **Pending**: 아직 이행되거나 거부되지 않은 상태
- **Fulfilled**: 성공 값이 확정된 상태
- **Rejected**: 실패 이유가 확정된 상태

`async`와 `await`의 역할은 다음과 같다.

- **async**: 함수를 호출하면 항상 Promise를 반환하도록 한다. 일반 값을 `return`하면 해당 값으로 이행되는 Promise가 반환된다.
- **await**: Promise의 결과를 기다리는 동안 현재 async 함수의 실행을 일시 중단한다. 이행되면 결과값을 받고 실행을 재개하며, 거부되면 그 위치에서 예외가 발생한다.

`await`는 JavaScript 실행 스레드 전체를 멈추지 않는다.

---

## 예시

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

- `run()`은 첫 번째 `await` 전까지 동기적으로 실행하므로 `B`가 먼저 출력된다.
- `await`에서 `run()`의 실행이 일시 중단되어 호출한 쪽의 `C`가 출력된다.
- 이후 `run()`이 재개되어 `D 10`을 출력하고, 반환한 Promise가 이행되면 `.then()` 콜백에서 `E 20`을 출력한다.

---

## 헷갈리기 쉬운 점

- `async` 함수가 일반 값을 `return`해도 **호출 결과는 Promise 객체**다.
- `await`를 사용하면 Promise 객체 자체가 아니라 **이행된 결과값**을 얻는다.
- `await`는 **현재 async 함수만 일시 중단**하며, 이미 이행된 Promise를 기다려도 이후 실행은 비동기적으로 재개된다.

---

## 면접 답변

> Promise는 비동기 작업의 최종 성공 값이나 실패 이유를 표현하는 객체입니다. async 함수는 항상 Promise를 반환하며, await는 Promise의 결과를 기다리는 동안 현재 async 함수의 실행을 일시 중단합니다. JavaScript 전체 실행이 멈추는 것은 아니고, Promise가 이행되면 결과값을 받아 실행을 재개하며 거부되면 예외가 발생합니다.

---

## 기억할 것

```text
Promise = 비동기 결과를 나타내는 객체
Pending → Fulfilled 또는 Rejected
async 함수 호출 → 항상 Promise 반환
await → 현재 async 함수만 일시 중단
이행 → 결과값으로 재개
거부 → await 위치에서 예외 발생
```

## 참고자료

- [MDN — Promise](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)
- [MDN — async function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [MDN — await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)
