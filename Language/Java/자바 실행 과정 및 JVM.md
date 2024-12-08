<details>
  <summary><strong>자바 프로그램이 실행되기까지의 전반적인 과정을 설명해주세요.</strong></summary>
  
<br>

자바 소스 코드(.java)를 작성하신 후 javac 명령어로 컴파일하면 .class라는 바이트코드 파일이 생성됩니다. 프로그램 실행 시 JVM은 이 바이트코드를 클래스 로더를 통해 메모리에 로딩하고, 링크 과정을 거친 뒤 실행 엔진을 통해 해석하거나 JIT 컴파일을 하여 실제 기계어 수준으로 실행합니다. 이러한 과정 덕분에 자바 프로그램은 운영체제나 하드웨어에 의존하지 않고 동일한 바이트코드로 다양한 환경에서 동작할 수 있습니다.

<br>
</details>

<details>
  <summary><strong>JVM(Java Virtual Machine)은 무엇이며 왜 필요한지를 포함해서 설명해주세요.</strong></summary>
  
<br>

JVM은 자바 바이트코드를 해석하고 실행하는 가상 머신으로, 운영체제나 하드웨어 환경에 관계없이 동일한 결과를 낼 수 있도록 해줍니다.
이를 통해 한 번 작성한 코드를 다양한 플랫폼에서 실행할 수 있는 자바의 "Write Once, Run Anywhere" 개념을 구현할 수 있습니다.
JVM은 크게 클래스 로더(Class Loader), 실행 엔진(Execution Engine), 메모리 영역(Runtime Data Area)으로 구성됩니다.
클래스 로더는 .class 파일을 메모리에 로딩 및 링크하고, 실행 엔진은 바이트코드를 실제 기계어로 변환하거나 인터프리팅하여 실행하며, 메모리 영역은 클래스 정보, 객체, 메서드 호출 스택 등 프로그램 실행에 필요한 데이터를 관리합니다.

  <br>

</details>

<details>
  <summary><strong>JVM 메모리 영역(Runtime Data Area)에 대해서 설명해주세요.</strong></summary>
  
<br>

JVM 메모리 영역에는 메서드 영역(Method Area), 힙(Heap), 스택(Stack), PC(Program Counter) 레지스터, 네이티브 메서드 스택(Native Method Stack) 등이 있습니다.
메서드 영역에는 클래스 정보, 메서드 메타데이터, 상수 등이 저장되고, 힙은 객체와 배열을 저장하며, 스택은 메서드 호출 시 생성되는 스택 프레임을 담습니다.
PC 레지스터는 현재 실행 중인 명령어 주소를 나타내고, 네이티브 메서드 스택은 자바 외부의 네이티브 코드를 실행할 때 사용됩니다.
  <br>

</details>
