<details>
  <summary><strong> RESTFul API에 대해 설명하고, REST의 기본 원칙 6가지에 대해 설명해주세요. </strong></summary>
  
  ## RESTful API
  - REST(Representational State Transfer) 원칙을 따르는 API
  - 시스템 간의 효율적인 통신을 가능하게 하며, 개발자의 생산성을 향상시킨다.

<br>
<br>

  **원칙 1) 클라이언트-서버**
  - 클라이언트(프론트엔드)와 서버(백엔드)를 분리하여 각각 독립적으로 동작할 수 있도록 한다.
  - 클라이언트는 요청을 보내고, 서버는 데이터를 처리하여 응답을 반환한다.

<br>
<br>

  **원칙 2) 무상태성(Stateless)** 
  - 모든 요청은 독립적이며, 필요한 데이터는 요청 시마다 포함해야한다. ex) HTTP 요청마다 `Authorization`헤더를 포함하여 인증
  - 서버는 클라이언트의 상태를 저장하지 않는다. 

<br>
<br>

  **원칙 3) 캐시 가능(Cachealbe)**
  - API 응답이 캐시 가능해야한다.
  - 동일한 요청에 대한 응답을 재사용할 수 있도록하여 성능을 향상시킨다. ex) HTTP의 `Cache-Control`헤더를 활용

<br>
<br>

  **원칙 4) 계층화 시스템(Layered System)**
  - API 아키텍처는 여러 계층(Layer)로 구성될 수 있다.
  - 클라이언트는 직접 연결된 계층만 알면 된다.

<br>
<br>

  **원칙 5) 인터페이스 일관성(Uniform Interface)**
  - 다음과 같은 일관된 인터페이스를 제공해야 한다.
    - 리소스 기반 URL : https://api.example.com/users/123
    - 표준 HTTP 메서드 사용 : GET/POST/PUT/PATCH/DELETE
    - 표준 응답 코드 사용 : 200 OK / 200 Created / 400 Bad Request 등

<br>
<br>

  **원칙 6) 코드 온 디맨드(Code on Demand, 선택사항)**
  - 필요할 경우 서버에서 실행 가능한 코드를 클라이언트로 전송하여 실행할 수도 있다. ex)JavaScript 코드로 전달하여 동작 변경

</details>
