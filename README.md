# unseo's frontend-deep-dive

> 프론트엔드 개발자가 “개념 → 원리 → 실전 적용”까지 한 번에 정리 할 수 있도록 구성한 딥다이브 문서 레포입니다.
> 각 문서는 단순 요약이 아니라 **재현 가능한 예시/검증 방법/트러블슈팅**까지 포함하는 것을 목표로 합니다.
> 한번 적고 잊어버리는 1회성 CS가 아닌 무조건 내 머릿속에 박히게끔하는 것이 이 레포의 목표입니다.

---

## 이 레포에서 얻을 수 있는 것
- 프론트엔드 전반(언어 코어, 런타임, 네트워크, UI 렌더링, 프레임워크, 상태관리, 빌드/패키징, 성능, 테스트, 보안, 배포 등)의 **핵심 개념 정리**
- 면접/실무에서 "왜?"를 설명할 수 있는 **근거 중심의 문서 축적**
- 헷갈리기 쉬운 포인트를 **“내 기준”으로 일관되게 정리한 개인 레퍼런스**
- 한땀한땀 내가 직접 적으면서 내 뇌리속에 박히게해 **제대로된 frontend cs deep dive 를 가능하게 하는 것**

---
## 사용 방법 (추천 순서)
1) 소개/규칙
- [`00-소개/레포-운영규칙.md`](./00-소개/레포-운영규칙.md)  
- [`00-소개/문서-작성규칙.md`](./00-소개/문서-작성규칙.md)  
- [`00-소개/참고자료-관리규칙.md`](./00-소개/참고자료-관리규칙.md)

2) 기본 토대(프로젝트 세팅/협업)  
- [`01-프로젝트-세팅/로컬-개발환경.md`](./01-프로젝트-세팅/로컬-개발환경.md)  
- [`02-git-협업/git-기초.md`](./02-git-협업/git-기초.md)

3) 코어 → 런타임 → 네트워크 → UI 렌더링 → 프레임워크  
- `03` → `04` → `05` → `06` → `07`

4) 실전(상태관리/빌드/성능/안정성/디버깅/테스트/접근성/보안/배포/아키텍처)  
- `08` → `09` → `10` → `11` → `12` → `13` → `14` → `15` → `16` → `17`

> 이 레포가 “문서 전용”인지 “예제 프로젝트 포함”인지에 따라 실행 방법이 달라질 수 있어,
> 실제 명령/환경은 위 문서에서 기준을 확정합니다.

---

## 진행도
- [ ] 00-소개/레포-운영규칙.md
- [ ] 00-소개/문서-작성규칙.md
- [ ] 00-소개/참고자료-관리규칙.md
- [ ] 01-프로젝트-세팅/로컬-개발환경.md
  
---

## 문서 네비게이션 (클릭)
아래는 레포 구조를 그대로 “클릭 가능한 링크”로 구성한 문서 맵입니다.

<details>
<summary><strong>00-소개</strong></summary>

- [`레포-운영규칙.md`](./00-소개/레포-운영규칙.md)
- [`문서-작성규칙.md`](./00-소개/문서-작성규칙.md)
- [`참고자료-관리규칙.md`](./00-소개/참고자료-관리규칙.md)

</details>

<details>
<summary><strong>01-프로젝트-세팅</strong></summary>

- [`로컬-개발환경.md`](./01-프로젝트-세팅/로컬-개발환경.md)
- [`에디터-린터-포맷터.md`](./01-프로젝트-세팅/에디터-린터-포맷터.md)
- [`타입스크립트-초기세팅.md`](./01-프로젝트-세팅/타입스크립트-초기세팅.md)
- [`환경변수-설정.md`](./01-프로젝트-세팅/환경변수-설정.md)
- [`디렉토리-구조-전략.md`](./01-프로젝트-세팅/디렉토리-구조-전략.md)
- [`코드스타일-가이드.md`](./01-프로젝트-세팅/코드스타일-가이드.md)

</details>

<details>
<summary><strong>02-git-협업</strong></summary>

- [`git-기초.md`](./02-git-협업/git-기초.md)
- [`브랜치-전략.md`](./02-git-협업/브랜치-전략.md)
- [`커밋-컨벤션.md`](./02-git-협업/커밋-컨벤션.md)
- [`코드리뷰-체크포인트.md`](./02-git-협업/코드리뷰-체크포인트.md)
- [`충돌-해결-전략.md`](./02-git-협업/충돌-해결-전략.md)
- [`릴리즈-태깅-전략.md`](./02-git-협업/릴리즈-태깅-전략.md)

</details>

<details>
<summary><strong>03-언어-코어</strong></summary>

**javascript**
- [`실행컨텍스트-스코프-클로저.md`](./03-언어-코어/javascript/실행컨텍스트-스코프-클로저.md)
- [`this-바인딩.md`](./03-언어-코어/javascript/this-바인딩.md)
- [`프로토타입-클래스.md`](./03-언어-코어/javascript/프로토타입-클래스.md)
- [`이벤트루프-태스크-마이크로태스크.md`](./03-언어-코어/javascript/이벤트루프-태스크-마이크로태스크.md)
- [`promise-async-await.md`](./03-언어-코어/javascript/promise-async-await.md)
- [`메모리-gc.md`](./03-언어-코어/javascript/메모리-gc.md)
- [`모듈-패턴-기초.md`](./03-언어-코어/javascript/모듈-패턴-기초.md)

**typescript**
- [`타입시스템-핵심.md`](./03-언어-코어/typescript/타입시스템-핵심.md)
- [`narrowing-타입가드.md`](./03-언어-코어/typescript/narrowing-타입가드.md)
- [`제네릭-유틸리티타입.md`](./03-언어-코어/typescript/제네릭-유틸리티타입.md)
- [`타입-설계-패턴.md`](./03-언어-코어/typescript/타입-설계-패턴.md)
- [`tsconfig-깊게.md`](./03-언어-코어/typescript/tsconfig-깊게.md)
- [`dts-타입선언-기초.md`](./03-언어-코어/typescript/dts-타입선언-기초.md)

</details>

<details>
<summary><strong>04-런타임-플랫폼</strong></summary>

**browser**
- [`url에서-렌더링까지.md`](./04-런타임-플랫폼/browser/url에서-렌더링까지.md)
- [`dom-bom.md`](./04-런타임-플랫폼/browser/dom-bom.md)
- [`이벤트-전파-캡처-버블링.md`](./04-런타임-플랫폼/browser/이벤트-전파-캡처-버블링.md)
- [`스토리지-쿠키-세션-차이.md`](./04-런타임-플랫폼/browser/스토리지-쿠키-세션-차이.md)
- [`브라우저-캐시.md`](./04-런타임-플랫폼/browser/브라우저-캐시.md)
- [`렌더링-파이프라인-개요.md`](./04-런타임-플랫폼/browser/렌더링-파이프라인-개요.md)

**nodejs**
- [`nodejs-이벤트루프.md`](./04-런타임-플랫폼/nodejs/nodejs-이벤트루프.md)
- [`프로세스-환경변수.md`](./04-런타임-플랫폼/nodejs/프로세스-환경변수.md)
- [`파일시스템-네트워킹-기초.md`](./04-런타임-플랫폼/nodejs/파일시스템-네트워킹-기초.md)
- [`node-모듈해석-esm-cjs.md`](./04-런타임-플랫폼/nodejs/node-모듈해석-esm-cjs.md)

</details>

<details>
<summary><strong>05-네트워크</strong></summary>

- [`http-기초.md`](./05-네트워크/http-기초.md)
- [`메서드-상태코드.md`](./05-네트워크/메서드-상태코드.md)
- [`헤더-정리.md`](./05-네트워크/헤더-정리.md)
- [`cors-프리플라이트.md`](./05-네트워크/cors-프리플라이트.md)
- [`쿠키-정책-samesite-secure-httponly.md`](./05-네트워크/쿠키-정책-samesite-secure-httponly.md)
- [`http-캐시-cache-control-etag.md`](./05-네트워크/http-캐시-cache-control-etag.md)
- [`https-tls-개념.md`](./05-네트워크/https-tls-개념.md)
- [`http2-http3-개요.md`](./05-네트워크/http2-http3-개요.md)
- [`websocket-sse.md`](./05-네트워크/websocket-sse.md)

</details>

<details>
<summary><strong>06-ui-렌더링</strong></summary>

**css**
- [`css-우선순위-상속.md`](./06-ui-렌더링/css/css-우선순위-상속.md)
- [`레이아웃-flex-grid.md`](./06-ui-렌더링/css/레이아웃-flex-grid.md)
- [`스태킹컨텍스트-zindex.md`](./06-ui-렌더링/css/스태킹컨텍스트-zindex.md)
- [`반응형-기초.md`](./06-ui-렌더링/css/반응형-기초.md)

**rendering**
- [`리플로우-리페인트-컴포지팅.md`](./06-ui-렌더링/rendering/리플로우-리페인트-컴포지팅.md)
- [`크리티컬-렌더링-패스.md`](./06-ui-렌더링/rendering/크리티컬-렌더링-패스.md)

**motion**
- [`transition-vs-animation.md`](./06-ui-렌더링/motion/transition-vs-animation.md)
- [`애니메이션-성능-원칙.md`](./06-ui-렌더링/motion/애니메이션-성능-원칙.md)

</details>

<details>
<summary><strong>07-프레임워크</strong></summary>

**react**
- [`vdom-리컨실리에이션-개요.md`](./07-프레임워크/react/vdom-리컨실리에이션-개요.md)
- [`리렌더-원인과-최적화.md`](./07-프레임워크/react/리렌더-원인과-최적화.md)
- [`hooks-동작모델.md`](./07-프레임워크/react/hooks-동작모델.md)
- [`컴포넌트-설계-원칙.md`](./07-프레임워크/react/컴포넌트-설계-원칙.md)
- [`에러바운더리.md`](./07-프레임워크/react/에러바운더리.md)

**vue**
- [`반응성-원리-개요.md`](./07-프레임워크/vue/반응성-원리-개요.md)
- [`렌더링-업데이트-모델.md`](./07-프레임워크/vue/렌더링-업데이트-모델.md)
- [`컴포넌트-설계-원칙.md`](./07-프레임워크/vue/컴포넌트-설계-원칙.md)

**공통**
- [`react-vue-비교-포인트.md`](./07-프레임워크/공통/react-vue-비교-포인트.md)

</details>

<details>
<summary><strong>08-상태-관리</strong></summary>

- [`상태관리-기초-정의.md`](./08-상태-관리/상태관리-기초-정의.md)
- [`로컬상태-전역상태-구분.md`](./08-상태-관리/로컬상태-전역상태-구분.md)
- [`react-context-패턴.md`](./08-상태-관리/react-context-패턴.md)
- [`redux-zustand-등-비교.md`](./08-상태-관리/redux-zustand-등-비교.md)
- [`server-state-개념-캐시.md`](./08-상태-관리/server-state-개념-캐시.md)
- [`react-query-패턴.md`](./08-상태-관리/react-query-패턴.md)

</details>

<details>
<summary><strong>09-모듈-빌드-패키징</strong></summary>

**modules**
- [`esm-vs-cjs.md`](./09-모듈-빌드-패키징/modules/esm-vs-cjs.md)
- [`import-export-해석규칙.md`](./09-모듈-빌드-패키징/modules/import-export-해석규칙.md)
- [`tree-shaking-조건.md`](./09-모듈-빌드-패키징/modules/tree-shaking-조건.md)
- [`code-splitting-전략.md`](./09-모듈-빌드-패키징/modules/code-splitting-전략.md)

**bundlers**
- [`번들러-원리-의존성그래프.md`](./09-모듈-빌드-패키징/bundlers/번들러-원리-의존성그래프.md)
- [`vite-webpack-rollup-esbuild-비교.md`](./09-모듈-빌드-패키징/bundlers/vite-webpack-rollup-esbuild-비교.md)
- [`번들-분석-방법.md`](./09-모듈-빌드-패키징/bundlers/번들-분석-방법.md)

**transpilers**
- [`transpile-개념.md`](./09-모듈-빌드-패키징/transpilers/transpile-개념.md)
- [`babel-tsc-swc-역할.md`](./09-모듈-빌드-패키징/transpilers/babel-tsc-swc-역할.md)
- [`sourcemap-원리-디버깅연계.md`](./09-모듈-빌드-패키징/transpilers/sourcemap-원리-디버깅연계.md)

**package-manager**
- [`npm-packagejson-lockfile.md`](./09-모듈-빌드-패키징/package-manager/npm-packagejson-lockfile.md)
- [`semver-의존성해결.md`](./09-모듈-빌드-패키징/package-manager/semver-의존성해결.md)
- [`pnpm-yarn-npm-비교.md`](./09-모듈-빌드-패키징/package-manager/pnpm-yarn-npm-비교.md)
- [`workspace-기초.md`](./09-모듈-빌드-패키징/package-manager/workspace-기초.md)
- [`공급망-보안-audit.md`](./09-모듈-빌드-패키징/package-manager/공급망-보안-audit.md)

</details>

<details>
<summary><strong>10-성능-최적화</strong></summary>

- [`core-web-vitals-개요.md`](./10-성능-최적화/core-web-vitals-개요.md)
- [`렌더링-최적화-실전.md`](./10-성능-최적화/렌더링-최적화-실전.md)
- [`번들-최적화-실전.md`](./10-성능-최적화/번들-최적화-실전.md)
- [`이미지-폰트-최적화.md`](./10-성능-최적화/이미지-폰트-최적화.md)
- [`캐시-전략-정리.md`](./10-성능-최적화/캐시-전략-정리.md)
- [`네트워크-성능-기본.md`](./10-성능-최적화/네트워크-성능-기본.md)

</details>

<details>
<summary><strong>11-안정성-예외처리</strong></summary>

- [`예외처리-원칙.md`](./11-안정성-예외처리/예외처리-원칙.md)
- [`async-에러-전파.md`](./11-안정성-예외처리/async-에러-전파.md)
- [`재시도-타임아웃-백오프.md`](./11-안정성-예외처리/재시도-타임아웃-백오프.md)
- [`에러-표준화-에러코드.md`](./11-안정성-예외처리/에러-표준화-에러코드.md)

</details>

<details>
<summary><strong>12-디버깅-모니터링-트러블슈팅</strong></summary>

- [`디버깅-devtools-기본.md`](./12-디버깅-모니터링-트러블슈팅/디버깅-devtools-기본.md)
- [`로그-전략.md`](./12-디버깅-모니터링-트러블슈팅/로그-전략.md)
- [`sourcemap-실전-활용.md`](./12-디버깅-모니터링-트러블슈팅/sourcemap-실전-활용.md)
- [`에러-모니터링-개념-sentry.md`](./12-디버깅-모니터링-트러블슈팅/에러-모니터링-개념-sentry.md)
- [`트러블슈팅-플레이북.md`](./12-디버깅-모니터링-트러블슈팅/트러블슈팅-플레이북.md)

</details>

<details>
<summary><strong>13-테스트</strong></summary>

- [`테스트-전략-피라미드.md`](./13-테스트/테스트-전략-피라미드.md)
- [`단위-통합-e2e-구분.md`](./13-테스트/단위-통합-e2e-구분.md)
- [`jest-vitest-정리.md`](./13-테스트/jest-vitest-정리.md)
- [`react-testing-library-패턴.md`](./13-테스트/react-testing-library-패턴.md)
- [`playwright-cypress-정리.md`](./13-테스트/playwright-cypress-정리.md)
- [`msw-mocking-전략.md`](./13-테스트/msw-mocking-전략.md)
- [`flaky-test-대응.md`](./13-테스트/flaky-test-대응.md)

</details>

<details>
<summary><strong>14-접근성-표준</strong></summary>

- [`웹접근성-wcag-개요.md`](./14-접근성-표준/웹접근성-wcag-개요.md)
- [`시맨틱-html.md`](./14-접근성-표준/시맨틱-html.md)
- [`aria-기초.md`](./14-접근성-표준/aria-기초.md)
- [`키보드-포커스-탐색.md`](./14-접근성-표준/키보드-포커스-탐색.md)
- [`폼-접근성.md`](./14-접근성-표준/폼-접근성.md)
- [`크로스브라우징-호환성.md`](./14-접근성-표준/크로스브라우징-호환성.md)
- [`웹표준-체크포인트.md`](./14-접근성-표준/웹표준-체크포인트.md)

</details>

<details>
<summary><strong>15-보안</strong></summary>

- [`xss.md`](./15-보안/xss.md)
- [`csrf.md`](./15-보안/csrf.md)
- [`csp.md`](./15-보안/csp.md)
- [`oauth-oidc-jwt-개요.md`](./15-보안/oauth-oidc-jwt-개요.md)
- [`안전한-쿠키-스토리지.md`](./15-보안/안전한-쿠키-스토리지.md)
- [`공급망-보안-실전.md`](./15-보안/공급망-보안-실전.md)

</details>

<details>
<summary><strong>16-ci-cd-배포</strong></summary>

- [`ci-기본-파이프라인.md`](./16-ci-cd-배포/ci-기본-파이프라인.md)
- [`github-actions-기초.md`](./16-ci-cd-배포/github-actions-기초.md)
- [`빌드-아티팩트-캐시.md`](./16-ci-cd-배포/빌드-아티팩트-캐시.md)
- [`배포-전략-bluegreen-canary.md`](./16-ci-cd-배포/배포-전략-bluegreen-canary.md)
- [`환경별-설정-dev-stg-prod.md`](./16-ci-cd-배포/환경별-설정-dev-stg-prod.md)
- [`롤백-전략.md`](./16-ci-cd-배포/롤백-전략.md)

</details>

<details>
<summary><strong>17-아키텍처-설계</strong></summary>

- [`관심사-분리.md`](./17-아키텍처-설계/관심사-분리.md)
- [`레이어드-구조.md`](./17-아키텍처-설계/레이어드-구조.md)
- [`상태-데이터패칭-레이어.md`](./17-아키텍처-설계/상태-데이터패칭-레이어.md)
- [`api-모듈-설계.md`](./17-아키텍처-설계/api-모듈-설계.md)
- [`에러-로딩-캐시-설계.md`](./17-아키텍처-설계/에러-로딩-캐시-설계.md)
- [`폴더구조-전략(선택).md`](./17-아키텍처-설계/폴더구조-전략%28선택%29.md)

</details>

<details>
<summary><strong>appendix</strong></summary>

- [`용어집.md`](./appendix/용어집.md)
- [`참고자료.md`](./appendix/참고자료.md)

</details>