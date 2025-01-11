
<details>
  <summary><strong>equals와 hashCode 메서드를 함께 재정의해야 하는 이유는 무엇인가요?</strong></summary>

  equals와 hashCode 메서드는 자바에서 객체의 논리적 동등성을 비교하는 데 중요한 역할을 합니다.  
  특히, HashSet, HashMap 같은 컬렉션은 내부적으로 해싱을 사용해 객체를 관리합니다.  
  hashCode는 객체의 해시코드를 반환하며, 동일한 해시코드를 가진 객체만 equals 메서드로 추가적인 비교를 합니다.  
  만약 equals만 재정의하고 hashCode를 재정의하지 않으면, 같은 논리적 동등성을 가진 객체라도 해시코드가 다르게 계산되어, 중복 객체가 컬렉션에 추가되는 문제가 발생합니다.  
  따라서, 두 메서드는 항상 함께 재정의하여 논리적 동등성을 일관되게 유지해야 합니다.

</details>

<details>
  <summary><strong>Object 클래스의 기본 equals 메서드는 어떤 동작을 하나요? 이를 재정의하면 어떻게 동작을 변경할 수 있나요?</strong></summary>

  Object 클래스의 기본 equals 메서드는 두 객체의 참조값(주소값)을 비교합니다.  
  즉, this == obj와 같은 동작을 수행하여, 같은 메모리 주소를 가리키는 객체만 동일하다고 판단합니다.
  그러나, 객체의 상태나 값을 기준으로 동등성을 판단하려면 equals 메서드를 재정의해야 합니다.
  예를 들어, Person 클래스에서 id라는 필드를 기준으로 동등성을 판단하려면 다음과 같이 equals를 재정의합니다.
  ```java
  @Override
  public boolean equals(Object obj) {
      if (obj instanceof Person) {
          return this.id == ((Person) obj).id;
      }
      return false;
  }
  ```
  이렇게 하면, 서로 다른 객체라도 id가 같으면 equals 메서드는 true를 반환합니다.
</details>

<details>
  <summary><strong>hashCode 메서드를 재정의할 때 고려해야 할 중요한 원칙은 무엇인가요?</strong></summary>

  1. **같은 객체라면 동일한 해시코드를 반환해야 합니다.**  
    즉, equals가 true를 반환하는 두 객체는 반드시 같은 hashCode를 반환해야 합니다.  
    이를 위반하면, 해시 기반 컬렉션에서 예기치 않은 동작이 발생할 수 있습니다.
  2. **서로 다른 객체는 가능하면 다른 해시코드를 반환해야 합니다.**  
    서로 다른 객체의 해시코드가 같을 수는 있지만, 이를 최소화하면 성능에 유리합니다. 
  3. **불변성을 유지해야 합니다.**  
    hashCode는 객체의 상태가 변하지 않는 한 항상 동일한 값을 반환해야 합니다.  
    이를 위해 불변 필드만을 사용해 해시코드를 생성하는 것이 좋습니다.
</details>