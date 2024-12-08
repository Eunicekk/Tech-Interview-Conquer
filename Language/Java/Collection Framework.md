<details>
  <summary><strong>Collection Framework에 대해 설명해주세요.</strong></summary>
  
<br>

  Collection Framework는 데이터 그룹을 저장하는 클래스들을 표준화한 설계입니다.
  
  컬렉션 프레임워크는 자바의 인터페이스를 사용하여 구현되며, 객체지향적이고 재사용성이 높은 코드를 작성할 수 있도록 도와줍니다.
  
  또한, 일관된 API, 프로그래밍 속도 및 품질향상, 가변적인 공간을 제공합니다. 

</details>

<details>
  <summary><strong>List, Queue, Set, Map에 대해 설명해주세요.</strong></summary>
  
<br>

  * List : Collection 인터페이스를 상속받으며, 순서가 있는 데이터의 집합을 다루는 인터페이스이며, 데이터 중복이 허용됩니다.
  * Queue : FIFO(First In First Out) 구조를 가진 인터페이스입니다.
  * Set : 순서가 없는 데이터의 집합을 다루는 인터페이스이며, 데이터 중복이 허용되지않습니다.
  * Map : Key와 Vaule의 쌍으로 이루어진 데이터의 집합을 다루는 인터페이스이며, 순서가 있고 Key 중복이 허용되지만, Value 중복은 허용되지않습니다.

</details>

<details>
  <summary><strong>ArrayList와 LinkedList에 대해 비교 설명해주세요</strong></summary>
  
<br>

  * ArrayList는 배열을 이용하여 만든 리스트로써, 특정 원소 조회가 많은 경우 사용합니다. 또한 단방향 포인터 구조이기 때문에 인덱스 조회가 가능합니다.
  * LinkedList는 노드와 포인트를 이용하여 만든 리스트로써, 삽입/삭제가 많은 경우 사용합니다. 또한 양방향 포인터 구조입니다.

</details>

<details>
  <summary><strong>HashMap과 TreeMap에 대해 비교 설명해주세요</strong></summary>
  
<br>

  * HashMap은 키와 값을 가지며, 순서가 없고, 키 중복을 허용하지않지만, 값 중복은 허용하지않습니다.
    또한 동기화를 보장하지않아 멀티스레드 환경에서 안전하지않아서 멀티스레드에서는 ConcurrentHashMap 사용을 권장합니다.
  * TreeMap은 키를 기준으로 정렬이 되어 저장되는 Map으로 이진트리를 기반으로 합니다.

</details>

<details>
  <summary><strong>HashSet과 TreeSet에 대해 비교 설명해주세요</strong></summary>
  
<br>

  * HashSet은 가장 빠른 임의 접근 속도를 가집니다.
  * TreeSet은 중복이 허용되지않고, 순서가 없지만, 정렬이 되어있습니다. 또한 이진트리를 기반으로 한 Set 컬렉션입니다.

</details>
