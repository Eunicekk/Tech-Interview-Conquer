
<details>
  <summary><strong>Wrapper Class란 무엇인가요?</strong></summary>

  Wrapper Class는 Java의 기본 데이터 타입(primitive types)을 객체로 다룰 수 있도록 제공되는 클래스입니다. 기본 타입인 int, double 등의 값형 데이터를 Integer, Double 등으로 감싸 객체처럼 다룰 수 있게 합니다.
</details>


<details>
  <summary><strong>Boxing과 Unboxing이란?</strong></summary>

  Boxing은 기본 타입을 Wrapper 객체로 변환하는 과정이고, Unboxing은 그 반대입니다. 예를 들어, 
  ```java
  //Boxing
  int x = 5;
  Integer boxed = x;

  //Unboxing
  Integer y = 10;
  int unboxed = y;
  ```
  Java는 이를 자동으로 처리(Auto-boxing/unboxing)합니다.
</details>

<details>
  <summary><strong>Primitive Type과 Wrapper Class는 각각 언제 사용해야 하나요?</strong></summary>

  Primitive Type은 성능이 중요한 상황에서 사용됩니다. 간단한 수학 연산이나 반복적인 계산처럼 객체화가 필요 없는 경우가 대표적입니다. 예를 들어, 루프에서 int나 double을 사용하는 것이 적합합니다.  
  
  반면, Wrapper Class는 컬렉션(List, Set, Map)이나 제네릭에서 객체 타입만 사용할 수 있는 상황에서 사용됩니다. 또한, 기본 타입은 null 값을 표현할 수 없기 때문에, null 처리가 필요한 경우 Wrapper Class를 선택해야 합니다. 다만, Wrapper Class를 사용할 때는 Boxing과 Unboxing으로 인한 성능 저하를 고려해야 합니다.
</details>