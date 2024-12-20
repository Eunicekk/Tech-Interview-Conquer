<details>
  <summary><strong>Spring의 개념 및 장단점에 대해 설명해보세요.</strong></summary>

  ### 개념
  자바 기반 애플리케이션을 개발하기 위한 오픈 소스 프레임워크로, DI, AOP, 데이터 액세스, 트랜잭션 관리, MVC 아키텍처 등 다양한 기능을 제공하며 전통적인 Java EE보다 유연하고 간소화된 개발 환경 제공한다.

  ### 장점
  - 모듈화 : 필요한 기능만 선택적으로 사용할 수 있다.
  - 유연성 : 다양한 요구사항을 만족할 수 있는 기능을 제공한다.
  - 강력한 생태계 : Spring Data, Spring Security, Spring Cloud 등과 통합이 가능하다.

  ### 단점
  - 복잡한 설정 : XML 기반 설정이나 Java Config 작성에 많은 시간이 걸린다.
  - 초기 학습 곡선 : 설정과 사용법을 익히는 데 시간이 걸릴 수 있다.

</details>

<details>
  <summary><strong>Spring Boot의 개념 및 장단점에 대해 설명해보세요.</strong></summary>

  ### 개념
  Spring Framework를 기반으로 만들어진 서브 프레임워크로, Spring 애플리케이션 개발을 간소화하기 위해 설계되었으며 기본적인 설정을 자동으로 제공하고 애플리케이션을 빠르게 개발할 수 있도록 한다.

  ### 장점
  - 간소화된 설정 : 기본값 제공과 자동 설정(@SpringBootApplicaion)으로 복잡한 설정이 불필요하다.
  - 빠른 시작 : 내장된 서버(Tomcat, Jetty)와 자동 설정 덕분에 개발 시간 단축된다.
  - 운영 지원 : Actuator를 통해 헬스 체크, 메트릭, 애플리케이션 상태 모니터링을 제공한다.
  - 테스트 지원 : JUnit 및 Mockito와의 강력한 통합을 지원한다.

  ### 단점
  - 제어의 상실 : 자동 설정으로 인해 세부 조정이 어려울 수 있다.
  - 의존성 크기 증가 : 내장된 기능으로 인해 애플리케이션 크기가 커질 수 있다.

</details>

<details>
  <summary><strong>Spring과 Spring Boot의 차이와 어떤 상황에서 각 프레임워크가 더 적합한지 설명해보세요.</strong></summary>

  ### 차이
  1.  설정 방식
    - Spring : XML 또는 Java Config를 수동으로 설정.
    - Spring Boot : 대부분의 설정을 자동으로 처리.
  
  2.  초기 개발 속도
    - Spring : 복잡한 설정으로 인해 시작하는 데 시간이 오래 걸림.
    - Spring Boot : 내장된 기본 설정과 빠른 시작이 가능.

  3.  내장 웹 서버
    - Spring : 내장 웹 서버를 제공하지 않아 외부 서버(Tomcat 등)에 배포해야 함.
    - Spring Boot : Tomcat, Jetty, Undertow 같은 웹 서버를 내장하여 별도 설정 없이 애플리케이션 실행 가능.

  4.  의존성 관리
    - Spring : 의존성을 직접 설정해야 하며, 라이브러리 충돌 위험 있음.
    - Spring Boot : Starter Dependencies로 의존성 관리가 간단하고 충돌 위험 최소화.

  5.  배포 방식
    - Spring : WAR 파일을 생성하여 외부 서버에 배포.
    - Spring Boot : JAR 파일로 패키징하여 독립적으로 실행 가능.

  6.  운영 지원
    - Spring : 기본적으로 운영 관련 도구가 제공되지 않음.
    - Spring Boot : Actuator를 통해 헬스 체크, 메트릭, 애플리케이션 상태 모니터링 가능.

  7. REST 지원
    - Spring : REST API 개발 시 별도의 설정과 구현 필요.
    - Spring Boot : @RestController, @RequestBody와 같은 간편한 어노테이션 제공.

  8.  테스트 지원
    - Spring : 테스트 환경 구성 및 라이브러리 통합에 추가 작업 필요.
    - Spring Boot : JUnit, Mockito와 통합되어 테스트 작성이 간단하며, @SpringBootTest로 통합 테스트 지원.

  9.  대상 애플리케이션
    - Spring : 대규모, 복잡한 애플리케이션 개발에 적합.
    - Spring Boot : 소규모 또는 빠른 개발이 필요한 애플리케이션 개발에 적합.

  10. 학습 곡선
    - Spring : 초기 학습에 시간이 많이 걸릴 수 있음.
    - Spring Boot : 설정 자동화로 비교적 쉽게 익힐 수 있음.

  ### Spring이 적합한 경우
  1. 대규모, 복잡한 애플리케이션
    - 세부적인 설정과 제어가 필요한 경우.
    - 특정한 요구사항에 맞춘 아키텍처 설계가 필요한 경우.
  2. 기존 프로젝트
    - 이미 Spring 기반으로 작성된 레거시 프로젝트를 확장하거나 유지보수할 때.

  ### Spring Boot가 적합한 경우
  1. 빠른 개발이 필요한 경우
    - 초기 프로토타입이나 최소 기능 제품(MVP)을 빠르게 개발해야 할 때.
  2. 소규모 또는 단순한 프로젝트
    - 소규모 팀에서 간단한 웹 애플리케이션이나 마이크로서비스를 구축할 때.
  3. 클라우드 기반 환경
    - 컨테이너나 클라우드 배포가 필요한 애플리케이션 개발할 때.

</details>
