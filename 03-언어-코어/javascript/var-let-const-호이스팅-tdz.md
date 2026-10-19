# var · let · const · 호이스팅 · TDZ

## 학습 목표

이 문서를 읽고 다음을 설명할 수 있어야 한다.

- `var`, `let`, `const`의 스코프·재선언·재할당 차이
- 호이스팅을 “코드가 위로 이동한다”가 아닌 바인딩 준비와 초기화 시점으로 설명하는 방법
- `let`과 `const`에서 TDZ가 발생하는 이유

## 먼저 답해보기

자료를 읽기 전에 각 질문에 1~2문장으로 답한다.

1. `var`, `let`, `const`는 어떤 스코프를 가지는가?
2. `var`와 `let`은 선언 전에 접근했을 때 어떻게 다른가?
3. TDZ는 언제 시작하고 언제 끝나는가?

## var / let / const 차이

| 구분 | 스코프 | 같은 스코프 재선언 | 재할당 |
|---|---|---:|---:|
| `var` | 함수 스코프 | 가능 | 가능 |
| `let` | 블록 스코프 | 불가능 | 가능 |
| `const` | 블록 스코프 | 불가능 | 불가능 |

```js
function example() {
  if (true) {
    var functionScoped = 1;
    let blockScoped = 2;
    const alsoBlockScoped = 3;
  }

  console.log(functionScoped); // 1
  // console.log(blockScoped); // ReferenceError
  // console.log(alsoBlockScoped); // ReferenceError
}

example();
```

`var`는 함수 전체에서 접근할 수 있지만, `let`과 `const`는 선언된 블록 안에서만 접근할 수 있다.

## 호이스팅이란?

호이스팅(Hoisting)은 변수나 함수의 선언이 코드 실행 전에 먼저 처리되는 것처럼 보이는 현상을 설명하는 용어다.

정확히는 선언이 물리적으로 코드 위로 이동하는 것이 아니다. 실행 전에 코드 종류와 선언 종류에 따라 바인딩이 준비되고, 선언문이 실행될 때 초기화·할당이 진행되는 과정을 관찰한 것이다.

`var`, `let`, `const` 모두 실행 전에 바인딩과 관련된 처리가 있지만 초기화 시점이 다르다.

## var의 호이스팅

```js
console.log(a); // undefined

var a = 10;
```

`var`는 실행 준비 단계에서 바인딩이 만들어지고 `undefined`로 초기화된다. 하지만 `10`을 할당하는 작업은 원래 코드 위치에서 실행된다.

```text
실행 준비
→ a 바인딩 생성
→ a를 undefined로 초기화

실행
→ console.log(a): undefined
→ a = 10
```

다음처럼 생각하면 된다.

```js
var a;          // 바인딩 생성과 undefined 초기화
console.log(a); // undefined
a = 10;         // 원래 위치에서 할당
```

## let / const의 호이스팅

```js
console.log(b); // ReferenceError

let b = 20;
```

`let`과 `const`도 실행 전에 바인딩이 준비되지만, 선언문이 실행되기 전까지 초기화되지 않는다. 초기화 전에 접근하면 `ReferenceError`가 발생한다.

```text
실행 준비
→ b 바인딩 생성
→ 아직 초기화하지 않음

실행
→ console.log(b): ReferenceError
→ let b = 20에서 초기화
```

`let`과 `const`가 호이스팅되지 않는다고 설명하면 이 차이를 설명할 수 없다. 두 선언도 바인딩은 준비되지만, 초기화 전 접근이 금지된다는 점이 핵심이다.

## TDZ

TDZ(Temporal Dead Zone)는 `let`, `const`가 속한 스코프의 시작 지점부터 선언문이 실행되어 초기화되기 전까지의 접근 불가능한 구간이다.

```js
{
  // TDZ 시작
  console.log(value); // ReferenceError

  let value = 10;
  // 선언문 실행과 함께 초기화: TDZ 종료

  console.log(value); // 10
}
```

TDZ의 경계는 다음과 같다.

```text
블록 스코프 시작
↓
TDZ: 바인딩은 있지만 초기화되지 않음
↓
let / const 선언문 실행 및 초기화
↓
접근 가능
```

### `var`와 비교하기

```js
console.log(a); // undefined
console.log(b); // ReferenceError

var a = 10;
let b = 20;
```

| 선언 | 실행 전 바인딩 | 선언 전 접근 |
|---|---|---|
| `var` | `undefined`로 초기화 | `undefined` |
| `let` | 생성됐지만 미초기화 | `ReferenceError` |
| `const` | 생성됐지만 미초기화 | `ReferenceError` |

## 재선언과 재할당

```js
var count = 1;
var count = 2; // 가능
count = 3;     // 가능

let total = 1;
// let total = 2; // SyntaxError: 같은 스코프 재선언 불가
total = 2;        // 가능

const limit = 1;
// const limit = 2; // SyntaxError: 같은 스코프 재선언 불가
// limit = 2;       // TypeError: 재할당 불가
```

`const`가 가리키는 바인딩을 재할당할 수 없다는 뜻이지, 객체 내부를 변경할 수 없다는 뜻은 아니다.

```js
const user = { name: "A" };
user.name = "B"; // 가능: 객체 내부 변경
// user = {};    // 불가능: 바인딩 재할당
```

## 헷갈리기 쉬운 점

### `var`만 호이스팅되는 것이 아니다

```text
var
→ 바인딩 생성
→ undefined로 초기화
→ 선언 전 접근 시 undefined

let / const
→ 바인딩 생성
→ 선언문 전까지 초기화하지 않음
→ TDZ에서 접근하면 ReferenceError
```

### 호이스팅된다고 값까지 먼저 할당되는 것은 아니다

```js
console.log(a); // undefined
var a = 10;
```

`a`의 바인딩과 `undefined` 초기화는 먼저 준비되지만, `10`을 할당하는 문장은 원래 위치에서 실행된다.

### TDZ는 선언문 다음에 시작하지 않는다

TDZ는 선언문이 있는 줄부터가 아니라 해당 바인딩이 속한 스코프의 시작부터 시작한다. 선언문이 실행되어 초기화되면 종료된다.

### `typeof`도 TDZ를 피하지 못한다

```js
console.log(typeof missing); // "undefined": 존재하지 않는 식별자
console.log(typeof value);   // ReferenceError: TDZ의 value
let value = 1;
```

존재하지 않는 식별자와 TDZ에 있는 식별자는 다른 경우다.

## 직접 검증하기

1. 각 예제를 브라우저 Console에 따로 실행한다.
2. 선언 전 접근 결과가 `undefined`인지 `ReferenceError`인지 기록한다.
3. `let`과 `const`가 선언된 블록 안팎에서 접근 가능한지 확인한다.
4. DevTools의 Scope 패널에서 블록 스코프 바인딩을 확인한다.
5. 결과를 `바인딩 생성 → 초기화 → 할당` 순서로 설명한다.

## 면접 답변

> `var`는 함수 스코프이며 같은 스코프에서 재선언과 재할당이 가능합니다. `let`과 `const`는 블록 스코프이고 같은 스코프에서 재선언할 수 없으며, `let`은 재할당이 가능하지만 `const`는 불가능합니다. 호이스팅은 선언이 실행 전에 처리되는 것처럼 보이는 현상이며, 정확히는 실행 전에 바인딩이 준비되고 선언 종류에 따라 초기화 시점이 달라지는 것입니다. `var`는 `undefined`로 초기화되지만 `let`과 `const`는 선언문 전까지 초기화되지 않아 TDZ가 생기며, 그 구간에서 접근하면 `ReferenceError`가 발생합니다.

## 기억할 것

```text
var
= 함수 스코프
= 재선언 O / 재할당 O
= 호이스팅 + undefined 초기화

let
= 블록 스코프
= 재선언 X / 재할당 O
= 호이스팅 + TDZ

const
= 블록 스코프
= 재선언 X / 재할당 X
= 호이스팅 + TDZ
```

## 완료 체크리스트

- [ ] `var`, `let`, `const`의 스코프 차이를 설명할 수 있다.
- [ ] 재선언과 재할당의 차이를 구분할 수 있다.
- [ ] 호이스팅을 바인딩 준비와 초기화 시점으로 설명할 수 있다.
- [ ] `var`의 선언 전 접근 결과가 `undefined`인 이유를 설명할 수 있다.
- [ ] TDZ의 시작·종료 시점과 `ReferenceError` 발생 이유를 설명할 수 있다.
- [ ] 자료 없이 면접 답변을 30초 안에 말할 수 있다.

## 참고자료

- ECMAScript — Lexical Declarations
  https://tc39.es/ecma262/multipage/ecmascript-language-statements-and-declarations.html
  - 사용 이유: 렉시컬 선언과 초기화 규칙 확인
  - 확인일: 2026-10-19
- MDN — Hoisting
  https://developer.mozilla.org/en-US/docs/Glossary/Hoisting
  - 사용 이유: 호이스팅 용어와 선언별 동작 확인
  - 확인일: 2026-10-19
- MDN — `let`
  https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let
  - 사용 이유: 블록 스코프와 TDZ의 관찰 가능한 동작 확인
  - 확인일: 2026-10-19

마지막 업데이트: 2026-10-19
