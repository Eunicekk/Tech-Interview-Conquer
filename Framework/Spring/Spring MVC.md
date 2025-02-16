<details>
  <summary><strong>Spring MVC란 무엇인가요?</strong></summary>

 Spring MVC는 Spring 프레임워크의 웹 애플리케이션 개발을 위한 모듈로, Model-View-Controller 디자인 패턴을 기반으로 합니다.  
 - **Model**: 데이터를 처리하고, 애플리케이션의 비즈니스 로직을 캡슐화합니다.  
 - **View**: 사용자 인터페이스를 담당하며, JSP, Thymeleaf 등으로 구현됩니다.  
 - **Controller**: 사용자의 요청을 처리하고, 필요한 데이터를 Model에서 가져와 View에 전달합니다.  

 Spring MVC는 요청과 응답 흐름을 체계적으로 관리하여 애플리케이션 개발을 단순화합니다.
</details>

<details>
  <summary><strong>Spring MVC의 요청 흐름(Request Flow)은 어떻게 동작하나요?</strong></summary>

  1. DispatcherServlet: 사용자의 모든 요청은 DispatcherServlet이 먼저 받습니다.
  2. HandlerMapping: 요청 URL에 매핑된 컨트롤러를 찾습니다.
  3. Controller: 요청을 처리하고 Model에 데이터를 담아 View 이름을 반환합니다.
  4. ViewResolver: 반환된 View 이름을 실제 View(JSP, Thymeleaf 등)로 변환합니다.
  5. View: 최종적으로 사용자에게 응답을 렌더링합니다. 
 
 이 구조는 관심사의 분리를 통해 코드를 더욱 모듈화하고 유지보수를 용이하게 만듭니다.
</details>

<details>
  <summary><strong>스프링 디스패처 서블릿(DispatcherServlet)이란 무엇이며, 어떤 역할을 하나요?</strong></summary>

  스프링 디스패처 서블릿은 스프링 MVC의 프론트 컨트롤러로, 모든 HTTP 요청을 중앙에서 받아 처리하는 역할을 합니다.

  - 주요 역할:
    - 클라이언트의 요청을 적절한 컨트롤러(핸들러)로 전달
    - 핸들러가 반환한 모델 데이터를 기반으로 뷰를 선택 및 렌더링
    - 핸들러 매핑, 핸들러 어댑터, 뷰 리졸버 등의 컴포넌트를 연계하여 요청 처리 흐름을 제어
  - 장점:
    - 모든 요청을 하나의 진입점에서 관리함으로써 유지보수가 용이
    - 일관된 예외 처리, 데이터 바인딩, 요청/응답 처리 등의 기능 제공
</details>

<details>
  <summary><strong>스프링 MVC에서 DispatcherServlet이 가지는 장점은 무엇인가요?</strong></summary>

  - 중앙 집중화된 요청 처리: 모든 요청을 하나의 진입점에서 처리함으로써, 요청 흐름을 쉽게 관리할 수 있습니다.
  - 유연한 확장성: 핸들러 매핑, 핸들러 어댑터, 뷰 리졸버 등 다양한 컴포넌트를 사용자가 커스터마이징하거나 확장할 수 있습니다.
  - 일관된 예외 처리 및 데이터 바인딩: 전역 예외 처리, 데이터 바인딩, 폼 처리 등 공통 기능을 중앙에서 관리하여 개발 효율성을 높입니다.
  - 모듈화된 설계: 프론트 컨트롤러 패턴을 적용하여, 비즈니스 로직과 뷰 로직을 명확히 분리할 수 있습니다.
</details>