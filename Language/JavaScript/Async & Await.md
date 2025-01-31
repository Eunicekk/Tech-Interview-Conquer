<details>
  
<summary>
  <strong>Async / Await에 대해 설명하세요.</strong>
</summary>

<br>

### Async / Await
- async/await는 비동기 코드를 보다 간결하고 직관적으로 작성할 수 있도록 도와주는 문법입니다.
- 내부적으로는 Promise를 기반으로 동작하지만, then()을 여러 번 중첩해서 쓰는 콜백 지옥을 해결할 수 있습니다.

#### Async 키워드
- async 키워드가 붙은 함수는 항상 Promise를 반환합니다.
- 내부에서 return한 값은 자동으로 Promise.resolve()로 감싸집니다.

#### Await 키워드
- await 키워드는 Promise가 처리될 때까지 기다린 후 결과를 반환합니다.
- await는 반드시 async 함수 안에서만 사용할 수 있습니다.

### Async / Await의 특징
**1. 비동기 코드를 동기 코드처럼 작성 가능**
- await을 사용하면 Promise가 처리될 때까지 기다린 후 다음 코드가 실행됨
- then() 체이닝 없이 깔끔한 코드 작성 가능
  
**2. Promise 기반으로 동작**
- async 함수는 자동으로 Promise를 반환하며, 내부에서 return한 값도 Promise.resolve()로 감싸짐
  
**3. try/catch를 통한 에러 핸들링**
- 기존의 Promise.catch() 대신 try/catch 문을 사용하여 에러 처리가 가능함

**4. await는 async 함수 내에서만 사용 가능**
- 일반 함수에서 await을 단독으로 사용할 수 없음 (최상위에서는 가능, ex: ES2022 top-level await)

#### Async / Await의 장점
- 가독성 향상
- 직관적인 에러 처리 (try/catch 사용 가능)
- 쉬운 디버깅
- 체이닝 없이 간결한 코드 작성 가능

<br>
</details>

<details>
  
<summary>
  <strong>Promise와 Async/Await을 비교하고 설명하세요.</strong>
</summary>

<br>

### Promis vs Async / Await
| 비교 항목    | Promise (then/catch) | async/await |
|-------------|--------------------|-------------|
| **가독성**  | `then()` 체이닝이 길어지면 가독성이 떨어짐 | 동기 코드처럼 작성 가능 |
| **에러 처리** | `.catch()` 사용 | `try/catch` 사용 가능 |
| **디버깅**  | 콜백 체이닝이 많으면 스택 트레이스 추적이 어려움 | 일반 동기 코드처럼 디버깅 가능 |
| **코드 구조** | 콜백이 중첩될 가능성이 있음 | 단순한 코드 작성 가능 |
| **실행 흐름** | `then()`을 통해 다음 작업 실행 | `await`을 만나면 해당 `Promise`가 처리될 때까지 기다림 |
| **병렬 실행** | `Promise.all()` 사용 | `Promise.all()`로 해결 가능하지만, 기본적으로 직렬 실행됨 |
| **사용 위치** | 어디서나 사용 가능 | `await`은 `async` 함수 내에서만 사용 가능 |

- 간단한 비동기 로직을 작성할 때에는 `async/await`을 사용하는 것이 가독성에 좋음
- 여러 개의 비동기 작업을 동시에 실행할 때에는 `Promise.all()`을 사용하는 것이 좋음

<br>
</details>
