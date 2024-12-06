<details>
  <summary><strong>Garbage Collection에 대해서 설명해 주세요</strong></summary>
  
<br>

  Garbage Collection은 프로그램이 동적으로 할당했던 메모리 영역 중 필요없는 부분을 자동으로 해제하는 기능으로 메모리 누수 방지 및 개발자의 실수, 부담을 줄이기 위해 사용됩니다.  
  하지만, 메모리 해제 타이밍을 알기 어려워 메모리 제어가 어렵고 개발자의 실수로 여전히 메모리 누수 발생 가능성이 있으며 성능 저하 가능성이 있습니다.  
  GC를 제공하는 언어에는 Java, Python, JavaScript 등이 있고 GC를 제공하지 않는 언어에는 C, C++ 등이 있습니다.  

  <br>

  * 개발자의 실수로 메모리 누수가 발생하는 경우 : 사용하지 않는 두 객체가 서로를 참조하는 경우
  * 성능이 낮아지는 이유 : GC 동작 중 Stop-The-World(다른 모든 동작이 정지)가 발생하기 때문
</details>

<details>
  <summary><strong>Stop-The-World에 대해서 설명해 주세요</strong></summary>
  
<br>

GC 실행 중 애플리케이션의 모든 스레드가 멈추는 현상으로 GC 성능 최적화의 주요 과제입니다

  <br>

  * 성능 최적화 예시 : G1 GC에서는 메모리를 작은 영역으로 분리, 스레드가 실행되는 동안 GC 작업을 병행
</details>

<details>
  <summary><strong>Mark - Sweep - Compact 과정에 대해서 설명해 주세요</strong></summary>
  
<br>

GC는 루트 집합을 기준으로 객체의 도달 가능성을 판단하고(Mark) 도달 불가능한 객체를 메모리에서 제거한 후(Sweep) 메모리 단편화 예방을 위해 메모리 공간을 압축(Compact)합니다.

  <br>

  * 루트 집합 : 지역 변수, 정적 변수, JVM 레지스터, JNI 참조 등
</details>

<details>
  <summary><strong>Generational Garbage Collection이란 무엇인가요</strong></summary>
  
<br>

객체의 생명 주기를 기준으로 Yong Generation과 Old Generation으로 나누어 GC를 효율적으로 수행하는 방식입니다.  
Young Generation에는 새로 생성된 객체가 처음 저장되는 Eden 영역과 Yong Generation에서 살아남은 객체가 이동하는 Survivor(S0, S1)영역이 존재합니다.  
여러 GC 과정(보통 15회) 중 Young Generation 영역에서 살아남은 객체는 Old Generation 영역으로 이동합니다.  
Yonug Generation에서 수행되는 GC는 Minor GC로 Eden 영역이 가득 차면 발생하는데 Eden 영역은 작기에 자주 발생하고 빠르게 처리됩니다.  
Old Generation에서 수행되는 GC는 Major GC로 Old Generation 영역이 가득 차면 발생하는데 Old Generation 영역은 크기에 가끔 발생하고 느리게 처리됩니다.  

  <br>

* Full GC : Heap 전체 영역에서 수행되는 GC로 Old Generation이 가득 차거나 System.gc() 요청 시 발생하는데 가장 느리게 처리됨으로 줄이는 것이 좋다
</details>

<details>
  <summary><strong>Permanent Generation 영역은 무엇인가요?</strong></summary>
  
<br>

Permanent Generation(Heap 영역) Java 7까지 클래스 메타데이터, 런타임 상수 풀이 저장되는 영역이었지만 고정 크기로 OutOfMemory Error 위험이 높았습니다.  
Java 8부터는 동적으로 확장 가능한 네이티브 메모리를 사용하는 Metaspace영역(Method 영역)에 클래스 메타데이터, 런타임 상수 풀을 저장하도록 바뀌었습니다.
</details>

<details>
  <summary><strong>Java 버전 별 GC 발전 과정에 대해서 설명해 주세요</strong></summary>
  
<br>

**Java 11까지는 필수 답변**

Java 8까지는 병렬로 GC 작업을 수행하는 Parallel GC가 기본으로 사용되었습니다.  
Java 9에서는 Stop-the-World 시간을 줄이고 메모리 회수 효율 극대화를 위해 Region 방식을 사용하는 G1 GC를 기본 GC로 사용했습니다.  
Java 11에서는 Stop-the-World를 밀리초 단위로 줄이고 초대형 Heap에서 사용하기 위해 동적으로 크기가 변하는 Region, 색상 태그, 참조 리맵핑을 사용하는 ZGC가 등장했고, 메모리 관리가 필요 없는 환경에 사용할 Epsilon GC가 등장했습니다.  
Java 15에서는 ZGC보다 일반적인 중간 크기의 Heap, 다양한 JVM에 사용하기 위한 고정 크기 Region을 사용하는 Shenandoah GC가 등장했습니다.  
Java 17에서는 빅데이터, 머신러닝과 같은 애플리케이션 지원을 위해 ZGC 메모리 크기 제한을 최대 16TB로 완화했고 Java 21에서는 ZGC 성능 개선을 위해 Generation 개념을 도입했습니다.  


  <br>
  
### Java 버전별 GC 참고

**Java 7 및 이전**

-   **GC 알고리즘**
    -   **Serial GC** : 단일 스레드 기반 GC, 성능이 안좋아 CPU 코어가 1개인 경우만 사용
    -   **Parallel GC** : GC 작업을 병렬로 수행해 성능 향상
    -   **CMS GC** : 애플리케이션 쓰레드와 GC 쓰레드가 동시에 실행, GC 과정이 복잡하고 메모리 파편화 문제 존재
    -   **G1(Garbage-First) GC** : Region 기반으로 메모리 역할(Eden, Survivor, Old)을 동적으로 부여하며 관리
        -   Heap을 고정 크기의 Region으로 나누어 관리, 메모리 공간이 더 작아짐
        -   공간이 작아졌으므로 Stop-the-World 시간을 줄일 수 있음
        -   Region 크기의 50%를 초과하는 큰 객체가 저장되는 Humongous 영역 등장
        -   가비지가 가장 많은 Region부터 우선 정리, 메모리 회수 효율 극대화
        -   메모리 압축을 동시에 진행하여 메모리 단편화를 줄임
        -   목표 지연 시간 설정이 가능 해 Stop-the-World 시간울 예측할 수 있음
-   **특징**
    -   Young Generation과 Old Generation의 일반적인 GC 구조 도입
    -   클래스 메타데이터와 런타임 상수 풀이 Permanent Genration(PermGen)에 저장
    -   메모리 단편화 문제를 해결하기 위해 Region 기반 G1 GC가 Java 7에서 등장
-   **발전 방향**
    -   메모리 누수 방지 및 프로그래머의 메모리 관리 부담을 줄이기 위해 GC 사용
    -   단일 스레드에서 성능 향상을 위해 병렬 스레드로 발전

**Java 8**

-   **GC 알고리즘**  
    -   **Parallel GC** : 기본 GC로 사용
-   **특징**
    -   PermGen을 제거하고 클래스 메타데이터와 런타임 상수 풀을 네이티브 메모리를 사용하는 Metaspace에 저장
-   **발전 방향**
    -   고정 크기로 OutOfMemoryError 위험이 높은 PermGen 대신에 동적으로 확장 가능한 Metaspace 사용

**Java 9**

-   **GC 알고리즘**  
    -   **G1 GC** : 기본 GC로 사용
-   **발전 방향**
    -   예측 가능하고 짧은 Stop-The-Wordl 시간, 대규모 데이터 처리 최적화, 메모리 단편화 감소를 이유로 G1 GC를 기본 GC로 채택

**Java 11**

-   **GC 알고리즘**  
    -   **ZGC**: 초저지연 GC
        -   Stop-the-World 시간을 밀리초 단위(10ms 이하)로 유지(초기 마킹, 최종 업데이트 단계에서만 발생)
        -   대부분의 GC 작업(객체 참조 마킹, 이동, 압축)을 애플리케이션 스레드와 동시에 수행
        -   Zpage(동적으로 크기가 변하는 Region)으로 메모리 관리
        -   객체 참조에 색상 태그를 사용하여 객체 상태 관리
            -   White : 마킹 되지 않은 객체
            -   Gray : 탐색 중인 객체
            -   Black : 마킹 완료된 객체
        -   참조 리맵핑 : 객체가 이동 중일 때도 애플리케이션이 올바르게 객체 참조 할 수 있도록 동적으로 업데이트(병행으로 수행)
        -   색상 태그와 참조 리맵핑을 위해 추가 메모리를 사용하고 동시성 GC 작업을 위해 CPU 사용량이 증가
    -   **Epsilon GC** : 메모리 회수를 하지 않는 GC
-   **발전 방향**
    -   금융, 게임 등 짧은 응답 시간이 필요한 시스템, 초대형 Heap을 위해 초저지연 ZGC 등장
    -   메모리 관리가 필요 없는 특정 테스트 환경에서 사용 가능한 Epsilon GC 등장

**Java 15**

-   **GC 알고리즘**  
    -   **Shenandoah GC** : 초저지연 GC
        -   Stop-the-World 시간을 밀리초 단위(10ms 이하)로 유지
        -   동시 압축(객체를 직접 업데이트)을 통해 메모리 단편화 문제 해결(애플리케이션 스레드와 병행)
        -   Heap을 고정 크기의 Region으로 나누어 관리, 가비지가 많은 Region부터 제거
-   **발전 방향**
    -   중간 크기의 Heap(일반적으로 초대형 Heap 불필요)에서 사용할 ZGC보다 단순한 GC가 필요하여 Shenandoah GC 등장
    -   Oracle JVM에서만 사용 가능한 ZGC와 달리 다양한 JVM(Open JDK)에서 사용할 GC가 필요하여 Shenandoah GC 등장

**Java 17**

-   **GC 알고리즘**
    -   **ZGC**
        -   최대 Heap크기 16TB 지원
-   **발전 방향**
    -   빅데이터, 머신러닝과 같은 애플리케이션 지원을 위해 메모리 크기 제한 완화

**Java** **21**

-   **GC 알고리즘**
    -   **Generational ZGC**  
        -   세대별 메모리 관리( Young Generation, Old Generation) 도입
-   **발전 방향**
    -   ZGC 성능을 더욱 개선하기 위해  Generational GC 가설(짧은 생명 주기의 객체가 대부분)을 활용
</details>
