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