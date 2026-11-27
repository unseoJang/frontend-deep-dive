# 비동기 에러 처리와 Promise 체이닝

## Why — 왜 필요한가?

- **Promise 체이닝**은 비동기 작업의 결과를 다음 작업으로 전달하기 위해 필요하다.
- **비동기 에러 처리**는 체이닝 도중 발생한 실패를 처리하기 위해 필요하다.

## How — 어떻게 동작하는가?

- **Promise 체이닝**: `.then()`, `.catch()` 등을 연결하여 비동기 작업의 결과와 오류를 다음 단계로 전달한다.
- **.then()**: Promise가 이행되면 성공 콜백을 실행하고 **새로운 Promise**를 반환한다. 콜백의 반환값이나 발생한 오류가 새 Promise의 결과에 영향을 준다.
- **.catch()**: Promise의 거부를 처리하는 콜백을 등록한다. 콜백에서 일반 값을 반환하면 `.catch()`가 반환한 새 Promise는 **Fulfilled** 상태가 된다.
- **return**: 콜백에서 `return 10`처럼 일반 값을 반환하면 새 Promise가 그 값으로 이행된다.
- **throw**: 예외를 발생시킨다. Promise 콜백 내부에서 던지면 해당 콜백이 반환하는 새 Promise는 **Rejected** 상태가 된다.

## Example — 실행 예제

```js
Promise.reject('error')
  .catch(() => {
    return 10;
  })
  .then((value) => {
    console.log(value);
  });
```

**실행 결과**

```text
10
```

```text
Rejected('error')
→ .catch()에서 return 10
→ 새로운 Promise가 Fulfilled(10)
→ 다음 .then()에서 10 출력
```

## 헷갈리기 쉬운 점

- `.catch()`가 `return 10`을 하면 처음 Promise의 **Rejected 상태가 바뀌는 것이 아니라**, `.catch()`가 반환한 **새로운 Promise**가 `Fulfilled(10)`이 된다.
- `return 10`은 다음 성공 콜백으로 값을 전달하지만, `throw new Error()`는 다음 Promise를 거부 상태로 만든다.
- 위 예제의 `'error'`는 `.catch()`가 전달받은 거부 이유이지만, 코드에서 출력하지 않았으므로 콘솔에는 `10`만 출력된다.

## 면접 답변

> Promise 체이닝은 비동기 작업의 결과를 다음 작업으로 전달하는 과정입니다. 체이닝 중 오류가 발생하면 `.catch()`를 통해 거부를 처리할 수 있습니다. `.catch()`에서 정상 값을 반환하면 새로운 Promise가 Fulfilled 상태가 되어 다음 `.then()`의 성공 콜백을 실행할 수 있습니다. 반면 `throw`로 예외를 다시 발생시키면 새로운 Promise가 Rejected 상태가 되어 오류가 다음 체인으로 전파됩니다.

## 참고자료

- [MDN — Using promises](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
- [MDN — Promise.prototype.then()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/then)
- [MDN — Promise.prototype.catch()](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise/catch)
