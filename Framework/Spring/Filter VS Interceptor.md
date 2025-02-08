<details>
  <summary><strong>Filter란 무엇이며, 언제 어떤 방식으로 동작하나요?</strong></summary>

  Filter는 디스패처 서블릿에 요청이 전달되기 전과 후에 URL 패턴에 맞는 모든 요청에 대해 부가 작업을 수행하는 기능입니다.  
  디스패처 서블릿은 스프링의 프론트 컨트롤러로 가장 앞단에 위치하므로, Filter는 스프링 범위 밖에서 웹 컨테이너(예: 톰캣)에 의해 관리되고 실행됩니다.
</details>

<details>
  <summary><strong>Interceptor란 무엇이며, Filter와는 어떻게 다르게 동작하나요?</strong></summary>

  Interceptor는 스프링이 제공하는 기술로, 디스패처 서블릿이 컨트롤러를 호출하기 전과 후에 요청과 응답을 참조하거나 가공할 수 있는 기능을 제공합니다.  
  Filter와 달리 Interceptor는 스프링 컨텍스트 내에서 관리되며, 디스패처 서블릿이 핸들러 매핑을 통해 컨트롤러를 찾은 후 실행체인에 포함되어 순차적으로 실행됩니다.  
  Interceptor는 스프링의 예외 처리와 연계되어 세부적인 보안, 인증, API 호출 로깅, 데이터 가공 등의 작업에 활용됩니다.
</details>

<details>
  <summary><strong>Filter와 Interceptor의 주요 용도 및 기능 차이에 대해 설명하세요.</strong></summary>

  - **Filter:**  
    - 공통적인 보안, 인증/인가 작업 수행  
    - 모든 요청에 대한 로깅 또는 감사를 위한 처리  
    - 이미지/데이터 압축, 문자열 인코딩과 같이 스프링과 분리되어 처리되어야 하는 기능  
    - Request/Response 객체의 직접적인 조작이 가능함
  - **Interceptor:**  
    - 컨트롤러에 전달되는 데이터의 세부 가공 및 보안, 인증/인가와 같은 공통 작업 수행  
    - API 호출에 대한 로깅 또는 감사  
    - 스프링 예외 처리와 연계되어 작동하며, Controller의 실행 전후에 처리되어야 하는 작업에 주로 사용됨  
    - Request/Response 객체의 조작은 Filter보다 제한적임
</details>

