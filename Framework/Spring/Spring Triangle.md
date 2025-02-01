<details>
  <summary><strong>Spring 삼각형에 대해 설명해 주세요</strong></summary>

<br>

#### DI(Dependency Injection, 의존성 주입)
개발자가 직접 객체를 생성하거나 관리할 필요 없이 스프링 컨테이너가 객체 생성 및 주입을 대신 처리 결합도 낮춤

* Spring에서는 @Autowired등을 활용하여 의존성을 주입
* IoC(Inversion of Control / 제어의 역전) : 객체의 제어 권한(객체 생성 및 주입)을 개발자가 아닌 프레임워크가 담당

#### AOP(Aspect-Oriented Programming, 관점 지향 프로그래밍)
핵심 비즈니스 로직과 부가 기능(로깅, 트랜잭션 관리)를 분리하여 모듈화 향상

* Spring에서는 Pointcut, JoinPoint, Advice, Aspect 등을 활용하여 횡단 관심사를 적용
#### PSA(Portable Service Abstraction, 휴대 가능한 서비스 추상화)
다양한 기술 스택(데이터, 트랜잭션, 메시징)에 대한 일관된 추상화를 제공하여 코드 수정 최소화

* Spring에서는 JdbcTemplate, JpaTemplate 등 DB 기술에 관계없이 공통 인터페이스를 사용
</details>
