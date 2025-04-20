# Spring Boot vs Spring Framework

---

## 면접 질문 예시

> "Spring Boot가 Spring Framework 대비 어떤 장점을 제공하는지 설명해 주실 수 있나요? 특히 초기 설정, 의존성 관리, 자동 구성, 내장 서버, 개발·배포 생산성 측면에서 비교해 보세요."

---

<details>
  <summary><h2> 평가 요소 및 평가 요소 별 모범 답안</h2></summary>

  ### 1. 자동 구성(Auto‑Configuration)  
  - 포함내용
    - `@EnableAutoConfiguration` / `spring.factories` 기반의 자동 빈 등록 원리  
    - `ConditionalOnMissingBean`, `ConditionalOnClass` 등의 조건부 설정
      - Spring Boot는 `@Conditional` 어노테이션 계열을 사용해, 특정 빈이 없거나(classpath에 특정 라이브러리가 있는지) 설정 속성이 정의돼 있는 경우에만 자동 구성을 적용합니다. 예를 들어, `@ConditionalOnClass(DataSource.class)`는 H2나 MySQL 드라이버가 있을 때만 `DataSource` 빈을 생성하도록 합니다.
      
  - <details>
    <summary>모범 답안 예시 : </summary>
    
      > "Spring Boot는 `@EnableAutoConfiguration`을 통해 classpath, bean 정의, 설정 속성을 기반으로 필요한 빈들을 자동으로 등록합니다. 예를 들어 H2 데이터베이스 드라이버가 classpath에 있으면 자동으로 `DataSource`를 설정하고, 수동 설정이 없으면 기본 메모리 DB를 구성합니다. 이를 통해 개발자는 반복적인 XML이나 JavaConfig 설정을 줄일 수 있습니다."
    </details>

  ### 2. 스타터 의존성(Starter Dependencies)  
  - 포함내용
    - `spring-boot-starter-*` 의 개념과 의존성 관리 편의  
    - BOM(Bill Of Materials)을 통한 버전 일관성 확보
      - Spring Boot는 `spring-boot-dependencies`라는 BOM을 제공하여, `dependencyManagement`에 한 번만 선언하면 스타터가 의존하는 모든 라이브러리의 호환되는 버전을 자동으로 맞춰 줍니다. 이를 통해 수십 개의 버전을 일일이 관리할 필요 없이, 충돌 없이 일관된 빌드를 유지할 수 있습니다.


  - <details>
    <summary>모범 답안 예시 : </summary>

      > "Spring Boot는 `spring-boot-starter-web`, `spring-boot-starter-data-jpa` 등 스타터 의존성을 제공해 관련 라이브러리를 한 번에 가져오고, 내부적으로 BOM을 사용해 호환되는 버전을 자동 관리합니다. 덕분에 pom.xml에서 수십 개 라이브러리 버전을 일일이 맞출 필요가 없습니다."
    </details>

  ### 3. 내장 웹 서버(Embedded Server)  
  - 포함내용
    - Tomcat, Jetty, Undertow 등의 내장 서버 지원  
    - `java -jar` 만으로 실행 가능한 fat‑jar 형태

  - <details>
    <summary>모범 답안 예시 : </summary>

      > "Spring Boot 애플리케이션은 기본으로 Tomcat을 내장하고, 별도 서버 설치 없이 `java -jar app.jar` 만으로 실행됩니다. 프로덕션에서는 외부 WAS 없이 독립 실행이 가능해 배포·테스트가 간편합니다."
    </details>

  ### 4. 개발·배포 생산성 향상  
  - 포함내용
    - 최소 설정(no XML), `@SpringBootApplication` 하나로 시작  
    - Spring Initializr, DevTools를 통한 빠른 개발 경험   

  - <details>
    <summary>모범 답안 예시 : </summary>

      > "기존 Spring에서는 애플리케이션 컨텍스트, 웹 설정, 데이터 소스 등을 모두 수동으로 구성해야 했지만, Spring Boot는 `@SpringBootApplication` 하나로 설정이 끝나고, Spring Initializr로 프로젝트 골격을 즉시 생성할 수 있습니다. DevTools를 사용하면 코드 변경 시 자동 재시작으로 빠른 피드백을 받을 수 있어 개발 속도가 매우 향상됩니다."
    </details>

  ### 5. 운영 및 모니터링 편의성  
  - 포함내용 (필수): 
    - Spring Boot Actuator: health, metrics, env, trace 등 엔드포인트 제공
      - Actuator를 추가하면 `/actuator/health`, `/actuator/metrics`, `/actuator/env`, `/actuator/httptrace`, `/actuator/beans` 등 다양한 관리·모니터링 API가 자동 생성됩니다. 이들은 애플리케이션 상태, JVM 메트릭, 환경 변수, HTTP 요청 추적 등을 실시간으로 파악할 수 있게 해 주며, `management.endpoints.web.exposure.include` 설정으로 노출할 엔드포인트를 세밀하게 제어할 수 있습니다.
    - 외부 모니터링 시스템(Prometheus, ELK)과의 통합  

  - <details>
    <summary>모범 답안 예시 :</summary>
    
      > "Actuator 모듈을 추가하면 `/actuator/health`, `/actuator/metrics` 같은 REST 엔드포인트가 자동 생성됩니다. 이를 통해 애플리케이션 상태를 손쉽게 모니터링하고, Prometheus나 Grafana 등과 연동해 실시간 성능 지표를 수집·시각화할 수 있습니다."
    </details>

  ### 6. 심화 지식
  - 포함내용
    - Thin vs Fat JAR: 최소 런타임만 포함한 thin‑jar 전략 vs 모든 의존성 포함하는 fat‑jar 전략  
      - Fat JAR: 애플리케이션과 모든 의존성을 하나의 JAR로 패키징하여 배포 및 실행이 간편하지만, 파일 크기가 크고 빌드 시간이 길어질 수 있습니다.  
      - Thin JAR: 애플리케이션 코드만 포함하고 런타임 시 의존성을 외부 레포지토리에서 가져오게 구성하여 배포 크기를 줄이고, CI 캐싱을 활용해 빌드 속도를 개선할 수 있습니다.
    - 클라우드 네이티브 지원: Spring Cloud 통합, Kubernetes 설정 자동화(Spring Cloud Kubernetes)  
      - Spring Boot는 Spring Cloud 프로젝트와 긴밀히 통합되어 서비스 디스커버리(Eureka), 구성 관리(Config Server), 분산 트레이싱(Zipkin), 회로 차단기(Resilience4j) 등을 손쉽게 도입할 수 있습니다. `spring-cloud-starter-kubernetes` 사용 시, Kubernetes ConfigMap·Secret을 자동으로 로드하고, 클러스터 내부 서비스 레지스트리에 등록하여 Pod 간 통신을 자동화합니다.
    - 커스텀 자동 구성: `@Conditional` 애노테이션 활용, 사용자 정의 auto‑configuration 작성 방법
      - 사용자 정의 자동 구성을 만들려면, `@Configuration` 클래스에 `@Conditional` 어노테이션을 달고 `spring.factories`에 등록합니다.
        ```
          properties
          org.springframework.boot.autoconfigure.EnableAutoConfiguration=\
          com.example.MyCustomAutoConfiguration
        ```
      - 위와 같이 작성 하면, Spring Boot의 자동 구성 메커니즘에 따라 특정 조건에서만 나만의 빈 설정을 적용할 수 있습니다.
    - 보안 및 프로파일 관리: `spring.profiles.active`, 외부 설정(yaml, config server) 활용법 
      - 프로파일: spring.profiles.active를 이용해 application-dev.yml, application-prod.yml 등 환경별 설정을 분리 관리합니다.
      - 외부 설정: Spring Cloud Config Server나 Vault를 연동해 중앙 집중형 설정 관리가 가능합니다. 환경 변수, 커맨드라인 인수, Config Server 우선 순위 등을 활용해 배포 환경별로 민감 정보나 설정을 동적으로 주입할 수 있습니다.

  - <details>
    <summary>모범 답안 예시 : </summary>
    
      > "추가적으로, 개발 환경과 프로덕션 환경 설정을 분리하기 위해 `application-{profile}.yml`을 사용하고, Spring Cloud Config Server로 중앙 관리할 수 있습니다. 또한, 클라우드 네이티브 애플리케이션을 위해 Spring Boot는 Spring Cloud와 긴밀히 통합되어 서비스 디스커버리, 분산 트레이싱, 설정 관리 등을 자동화합니다. 더 나아가, 필요에 따라 `@ConditionalOnMissingBean` 등을 이용해 사용자 정의 자동 구성 기능을 구현할 수도 있습니다."
    </details>
</details>