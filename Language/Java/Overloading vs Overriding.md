<details>
  <summary><strong>메서드 오버로딩과 오버라이딩의 차이는 무엇인가요?</strong></summary>

  - **오버로딩(Overloading)**: 같은 클래스 내에서 메서드 이름은 같지만 매개변수 타입이나 개수, 순서를 다르게 하여 여러 메서드를 정의하는 것. 컴파일 타임에 어떤 메서드가 호출될지 결정(정적 바인딩).  
  - **오버라이딩(Overriding)**: 상위 클래스에서 정의한 메서드를 하위 클래스에서 재정의하는 것. 런타임에 어떤 메서드가 호출될지 결정(동적 바인딩)하며 다형성을 구현.
</details>

<details>
  <summary><strong>오버라이딩 시 제약은 무엇인가요?</strong></summary>

  - 접근 제어자는 상위 클래스보다 더 좁은 범위를 가질 수 없음.  
  - 던질 수 있는 예외 범위는 상위 메서드보다 넓어질 수 없음(동일하거나 더 구체적이어야 함).  
  - 반환 타입은 상위 메서드와 동일하거나 하위 타입으로 변경 가능.
</details>

<details>
  <summary><strong>오버로딩 시 메서드 호출을 결정하는 기준은 무엇인가요?</strong></summary>

  컴파일 시점에 메서드의 시그니처(메서드명, 매개변수 타입, 개수, 순서)에 따라 어떤 메서드를 호출할지 정적 바인딩으로 결정합니다.  
</details>

<details>
  <summary><strong>오버라이딩된 메서드 호출 시 어떤 원리에 따라 호출되는지 설명해주세요.</strong></summary>

  런타임 시점에 객체의 실제 타입에 따라 어떤 메서드가 호출될지 동적 바인딩을 통해 결정합니다. 이를 통해 다형성이 구현됩니다.
</details>

<details>
  <summary><strong>오버라이딩 시 `@Override` 어노테이션을 사용하는 이유는 무엇인가요?</strong></summary>

  `@Override`는 해당 메서드가 상위 클래스나 인터페이스의 메서드를 재정의한 것임을 명시적으로 알려줍니다. 이를 통해 오타나 시그니처 불일치로 인한 문제를 컴파일 시점에 방지하고, 코드 가독성과 유지보수성을 높입니다.
</details>

<details>
  <summary><strong>생성자를 오버로딩할 수 있나요? 오버라이딩은 가능한가요?</strong></summary>

  - 생성자 오버로딩은 가능합니다. 매개변수를 다르게 하여 여러 생성자를 정의할 수 있습니다.  
  - 하지만 생성자는 상속되지 않기 때문에 오버라이딩 개념을 적용할 수 없습니다.
</details>