<details>
  <summary><strong>자바에서 Static에 대해 정의와 특징, 주의사항 등을 설명해주세요.</strong></summary>

  클래스와 관련된 요소를 정의할 때 사용됩니다. 클래스 레벨에서 메서드나 변수를 선언하여, 객체를 생성하지 않고도 접근할 수 있도록 하는 것입니다. 

   ### 특징
  - 메모리 관리 효율: 정적 변수는 한 번만 메모리에 할당되므로 메모리 관리가 효율적입니다.
  - 공유 상태: 모든 객체가 동일한 정적 변수에 접근하고 값을 공유합니다.
  - 클래스와의 관계: static은 객체(instance)가 아니라 클래스에 종속됩니다.
  - 초기화 시점: 클래스가 처음 로드될 때 정적 변수와 정적 블록이 초기화됩니다.

  ### 주의사항
  - 정적 메서드 안에서는 **비정적 멤버(인스턴스 변수 및 메서드)**에 접근할 수 없습니다.
  - 정적 변수는 모든 객체가 공유하기 때문에, 값이 변경될 경우 모든 객체에 영향을 미칩니다.

</details>

<details>
  <summary><strong>정적 변수(Static Variables)에 대해 설명해주세요.</strong></summary>

  - 클래스 변수(Class Variable): static으로 선언된 변수는 클래스에 하나만 존재하며, 모든 객체가 공유합니다.
  - 객체마다 별도의 복사본을 가지는 인스턴스 변수와 달리, static 변수는 클래스 로드 시 메모리에 할당되며, 프로그램이 종료될 때까지 유지됩니다.
</details>

<details>
  <summary><strong>정적 메서드(Static Methods)에 대해 설명해주세요.</strong></summary>

  - 클래스 메서드(Class Method): static으로 선언된 메서드는 객체를 생성하지 않고 클래스 이름으로 호출할 수 있습니다.
  - 정적 메서드는 인스턴스 변수나 메서드에 접근할 수 없으며, 오직 정적 변수나 정적 메서드만 사용할 수 있습니다.
</details>

<details>
  <summary><strong>정적 블록(Static Block)에 대해 설명해주세요.</strong></summary>

  - 정적 블록은 클래스가 로드될 때 한 번만 실행되는 코드 블록입니다.
  - 주로 정적 변수의 초기화에 사용됩니다.
</details>

<details>
  <summary><strong>정적 클래스(Static Nested Class)에 대해 설명해주세요.</strong></summary>

  - 클래스 내에 선언된 클래스가 static으로 정의되면 정적 중첩 클래스가 됩니다.
  - 정적 중첩 클래스는 외부 클래스의 객체 없이도 생성 및 사용이 가능합니다.
</details>

<details>
  <summary><strong>Java에서의 전역 변수에 대해 설명해주세요.</strong></summary>

  Java에서는 전역 변수라는 개념이 명시적으로 존재하지 않습니다. 하지만 전역 변수와 유사한 동작을 구현할 수 있는 public static 변수를 활용하여 해당 변수를 모든 클래스에서 접근 가능하게 만드는 방법과 싱글톤 패턴을 활용한 방법 등이 존재합니다.

</details>