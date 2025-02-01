<details>
  <summary><strong> API의 개념과 특징을 설명해주세요. </strong></summary>

  ### 개념
  API(Application Programming Interface)는 소프트웨어 간의 소통을 가능하게 하는 인터페이스로, 한 소프트웨어가 다른 소프트웨어의 기능을 사용할 수 있도록 정의된 규칙과 프로토콜의 집합이다. 이를 통해 서로 다른 시스템, 앱, 또는 서비스 간의 데이터 교환과 상호작용이 가능해진다.

  ### 특징
  1. 데이터 교환 : 서로 다른 애플리케이션 간에 데이터를 요청하거나 전송할 수 있다.
  2. 표준화된 규칙 : 특정 방식으로 요청(request)하면 정해진 방식으로 응답(response)을 반환한다.
  3. 재사용 가능성 : API를 활용하면 기존의 기능이나 데이터를 쉽게 재사용할 수 있어 새로운 서비스를 구축하는 데 시간과 노력을 절약할 수 있다.

</details>

<details>
  <summary><strong> API의 주요 유형을 설명하고 각각의 특징을 설명해주세요. </strong></summary>

  1. Open API
    
    - 누구나 사용할 수 있도록 공개된 API.
    - ex. Twitter API, Google Maps API.
     
  3. Private API 
    
    - 내부 시스템에서만 사용하도록 제한된 API.
    - ex. 회사 내부의 서비스 간 통신 API.
    
  4. Partner API
    
    - 특정 파트너와의 협업을 위해 제한적으로 제공되는 API.
    - ex. 배송사와 전자상거래 플랫폼 간 통합 API.
    
  5. Composite API
    
    - 여러 API 호출을 하나의 요청으로 결합하여 처리.
    - 복잡한 워크플로우를 간소화.

</details>

<details>
  <summary><strong> API 보안을 강화하기 위한 방법들에 대해 설명해주세요. </strong></summary>


  1. 인증(Authentication) : OAuth, API 키, JWT를 사용하여 사용자나 클라이언트를 인증.
  2. 권한 부여(Authorization) : 사용자별로 접근 가능한 리소스를 제한.
  3. 데이터 암호화 :  HTTPS를 통해 데이터를 전송하여 중간 공격(man-in-the-middle)을 방지.
  4. 속도 제한 :  요청 속도를 제한하여 DDoS 공격 방지.
  5. 로그 및 모니터링 :  API 사용 로그를 분석하고 비정상적 사용을 탐지.

</details>
