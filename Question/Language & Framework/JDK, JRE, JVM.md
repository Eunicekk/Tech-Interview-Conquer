# JDK, JRE, JVM

---

## 면접 질문 예시

> "JDK, JRE, JVM의 차이점과 각각의 역할에 대해 설명해 주실 수 있나요? 또한, 이들 구성 요소가 Java 애플리케이션의 개발과 실행 과정에서 어떻게 상호작용하는지도 말씀해 주세요."

---

<details>
  <summary><h2> 평가 요소 및 평가 요소 별 모범 답안</h2></summary>

  ### 1. JDK의 정의 및 역할
  - 포함내용
    - 정의: JDK(Java Development Kit)는 Java 애플리케이션 개발에 필요한 컴파일러(javac), 디버거(jdb), 각종 도구와 라이브러리를 포함한 개발 도구 모음입니다.
    - 역할:
      - 소스 코드 컴파일 → 바이트코드(.class) 생성  
      - 애플리케이션 패키징 및 배포용 도구 제공  
      - `javac`, `jar`, `javadoc` 등 개발 관련 핵심 유틸리티 포함  
      
  - <details>
    <summary>모범 답안 예시 : </summary>
    
      > "JDK는 Java 애플리케이션을 개발하기 위한 키트로, 소스 코드를 컴파일하는 `javac`를 비롯해 디버깅, 문서 생성, 패키징 도구를 포함합니다. 개발자가 코드를 작성하고, 컴파일하여 실행 가능한 바이트코드를 생성하는 데 필수적인 도구 모음입니다."
    </details>

  ### 2. JRE의 정의 및 역할
  - 포함내용
    - 정의: JRE(Java Runtime Environment)는 Java 애플리케이션을 실행하기 위한 환경으로, JVM과 표준 라이브러리(클래스 라이브러리)를 포함합니다.
    - 역할: 
      - 바이트코드를 해석/실행할 JVM 제공  
      - `rt.jar` 등 표준 클래스 라이브러리 로딩  
      - 개발 도구 없이 순수 실행 환경만 제공 

  - <details>
    <summary>모범 답안 예시 : </summary>

      > "JRE는 이미 컴파일된 바이트코드를 실행하기 위한 환경으로, JVM 실행 엔진과 표준 클래스 라이브러리를 포함합니다. 개발 도구는 없고, 단지 애플리케이션을 실행하는 데 필요한 런타임 구성 요소만 들어 있습니다."
    </details>

  ### 3. JVM의 정의 및 역할
  - 포함내용
    - 정의: JVM(Java Virtual Machine)은 바이트코드를 플랫폼에 독립적으로 해석·실행하는 가상 머신입니다.
    - 역할:  
      - 바이트코드 로드, 검증, 해석(또는 JIT 컴파일)  
      - 메모리 관리(Heap, Stack, Method 영역)  
      - 가비지 컬렉션, 클래스 로딩, 보안 관리

  - <details>
    <summary>모범 답안 예시 : </summary>

      > "JVM은 바이트코드를 읽어들이고, 검증한 뒤에 인터프리트하거나 JIT(Just‑In‑Time) 컴파일러를 통해 네이티브 코드로 변환해 실행하는 가상 머신입니다. 또한, 힙 메모리 관리와 가비지 컬렉션, 클래스 로딩 및 보안 검사 기능을 담당합니다."
    </details>

  ### 4. JDK, JRE, JVM의 관계 및 차이점
  - 포함내용
    - 관계:
      - JDK ⊃ JRE ⊃ JVM  
      - JDK에는 개발 도구 + JRE가 포함, JRE에는 JVM + 라이브러리가 포함  
    - 차이점 요약:
      - JDK: 개발용 전체 패키지  
      - JRE: 실행용 런타임 환경  
      - JVM: 바이트코드 실행 엔진  

  - <details>
    <summary>모범 답안 예시 : </summary>

      > "JDK는 개발 도구와 JRE를 모두 포함하는 상위 패키지이며, JRE는 JVM과 표준 라이브러리를 포함하는 실행 환경입니다. JVM은 바이트코드를 실제 머신 코드로 실행하는 엔진 역할을 합니다. 즉, JDK → JRE → JVM 순으로 역할과 포함 관계가 구성됩니다."
    </details>

  ### 5. 심화 지식
  - 포함내용
    - JDK 배포판 예시: Oracle JDK, OpenJDK, Amazon Corretto 등 주요 배포판 차이 및 라이선스 고려사항.
      - Oracle JDK :
        - Oracle이 제공하는 상업용 배포판으로, Oracle 라이선스를 따릅니다. 과거에는 무료로 사용 가능했으나, 최근 버전(11 이상)부터는 상업적 사용 시 라이선스 비용이 발생합니다.
        - 장점: Oracle의 테스트·검증된 빌드, 긴 LTS(Long‑Term Support) 지원.
      - OpenJDK : 
        - 오픈 소스 프로젝트로, GPLv2 + Classpath Exception 라이선스를 사용합니다. Oracle JDK와 기본적으로 동일한 코드 베이스를 공유하며, 커뮤니티와 여러 벤더가 빌드를 제공합니다.
        - 장점: 무료로 상업적 사용 가능, 활발한 커뮤니티 업데이트.
      - Amazon Corretto, Azul Zulu, AdoptOpenJDK 등 :
        - 각 벤더가 OpenJDK 소스를 기반으로 빌드·테스트·패키징하여 배포합니다.
        - 장점: 벤더별로 제공하는 보안 패치 주기, 운영 환경 지원(예: Amazon Corretto의 AWS 통합 최적화).
      - 선택 시 고려사항: 지원 기간(LTS 여부), 보안 패치 주기, 라이선스 비용, 벤더의 신뢰도 및 운영 환경과의 통합성.
    - 모듈 시스템(Java 9+): `jlink`를 이용해 애플리케이션에 필요한 모듈만 포함한 커스텀 JRE 생성 가능.
      - 도입 배경 : 대규모 애플리케이션에서 클래스패스(classpath) 복잡성, 충돌(JAR hell), 불필요한 코드 포함 문제를 해결하기 위해 도입되었습니다.
    - 클래스 로더 구조: Bootstrap, Extension, Application ClassLoader의 역할과 위계.
      - Bootstrap ClassLoader :
        - JVM 내부에 구현된 최상위 로더로, rt.jar 같은 핵심 Java 플랫폼 클래스(java.lang., java.util. 등)를 로드.
      - Extension (Platform) ClassLoader :
        - JDK 확장 기능을 제공하는 jre/lib/ext 디렉토리나 java.home/lib/ext 등에 배치된 JAR를 로드.
      - Application (System) ClassLoader :
        - CLASSPATH에 지정된 애플리케이션 클래스 및 서드파티 라이브러리를 로드.
      - 부모 위임(Parent Delegation) 모델 :
        - 하위 로더가 클래스를 로드 요청받으면, 먼저 부모 로더에게 요청을 위임하고, 부모가 없거나 찾지 못할 경우에만 자신이 직접 로드합니다.
        - 장점: 보안성 향상, 동일 클래스 중복 로드 방지.
    - JIT 컴파일러 및 AOT: HotSpot의 C1/C2 컴파일러, GraalVM AOT 컴파일 등 성능 최적화 기법.
      - JIT(Just‑In‑Time) 컴파일러 :
        - C1 (Client) 컴파일러 :
          - 짧은 지연 시간(문턱값이 낮은)으로 경량 최적화를 수행
          - 주로 GUI 애플리케이션 같이 빠른 스타트업이 중요한 경우에 사용
        - C2 (Server) 컴파일러 :
          - 더 많은 최적화를 수행하지만, 컴파일 비용(시간)이 크므로 주로 서버 애플리케이션에서 장기 실행 시 성능 극대화 목적 사용
      - GraalVM AOT(일부) 컴파일 :
        - 애플리케이션을 네이티브 바이너리로 사전 컴파일(Ahead‑Of‑Time)하여, JVM 없이도 실행 가능
        - 장점: 즉시 실행(Start‑up) 속도 극대화, 메모리 풋프린트 감소
        - 단점: 일부 동적 기능(리플렉션 등)을 제한적으로 지원

  - <details>
    <summary>모범 답안 예시 : </summary>
    
      > "심화적으로는, Java 9 이후 모듈 시스템을 통해 `jlink`로 애플리케이션 전용 런타임 이미지를 만들 수 있습니다. 또한, JVM 내에는 Bootstrap, Extension, Application ClassLoader가 계층적으로 동작하며, HotSpot의 C1/C2 JIT 컴파일러와 GraalVM의 AOT 컴파일 기능을 통해 실행 성능을 크게 향상시킬 수 있습니다."
    </details>
</details>