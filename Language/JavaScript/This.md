<details>
  
<summary>
  <strong>this에 대해 설명하세요.</strong>
</summary>

<br>

### this
- this는 실행 컨텍스트에 따라 달라지는 특수한 객체로, **함수가 호출되는 방식**에 따라 값이 결정됩니다.

### this의 주요 규칙

#### 1. 전역 컨텍스트 (Global Context)
- 브라우저 환경: window
- Node.js 환경: globalThis

#### 2. 객체의 메서드 호출
- 해당 메서드를 호출한 객체를 가리킨다.

```javascript
const obj = {
  name: "JavaScript",
  getName() {
    console.log(this.name);
  }
};

obj.getName(); // "JavaScript"
```

#### 3. 생성자 함수 (new 키워드 사용)
- 새롭게 생성된 인스턴스를 가리킨다.

```javascript
function Person(name) {
  this.name = name;
}
const me = new Person("Alice");
console.log(me.name); // "Alice"
```

#### 4. call, apply, bind를 사용한 명시적 지정
- call과 apply는 즉시 실행하고, bind는 새로운 함수를 반환한다.

```javascript
function sayHello() {
  console.log(this.name);
}

const user = { name: "Bob" };

sayHello.call(user);  // "Bob"
sayHello.apply(user); // "Bob"

const boundFunc = sayHello.bind(user);
boundFunc(); // "Bob"
```

#### 5. 화살표 함수 (=>)
- this를 바인딩하지 않고, 상위 스코프의 this를 사용한다.

```javascript
const obj = {
  name: "JavaScript",
  getName: function() {
    const arrowFunc = () => {
      console.log(this.name);
    };
    arrowFunc();
  }
};
obj.getName(); // "JavaScript"
```

#### 6. 이벤트 핸들러에서 this
- 기본적으로 this는 이벤트를 바인딩한 요소를 가리킨다.
- 화살표 함수를 사용하면 this가 상위 스코프를 참조한다.

```javascript
document.querySelector("button").addEventListener("click", function() {
  console.log(this); // 클릭된 버튼 요소
});

document.querySelector("button").addEventListener("click", () => {
  console.log(this); // 상위 스코프 (전역 객체)
});
```

#### 7. setTimeout과 setInterval에서의 this
- 일반 함수 사용 시 this는 전역 객체로 사용된다.
- 화살표 함수 사용 시 this는 상위 스코프를 유지한다.

```javascript
const obj = {
  name: "Timer",
  logName: function() {
    setTimeout(function() {
      console.log(this.name); // undefined (전역 객체)
    }, 1000);

    setTimeout(() => {
      console.log(this.name); // "Timer" (상위 스코프 유지)
    }, 1000);
  }
};
obj.logName();
```

#### 👉 핵심 포인트
- this는 실행 컨텍스트에 따라 달라진다.
- 화살표 함수는 this를 바인딩하지 않고, 상위 스코프의 this를 따른다.
- 명시적 바인딩 (call, apply, bind)을 통해 원하는 객체를 this로 지정할 수 있다.

<br>
</details>
