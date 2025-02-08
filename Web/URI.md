<details>
  
  <summary><strong>URI의 정의는 무엇인가요?</strong></summary>

  * URI는 인터넷에 있는 많은 자원들을 구분하기 위한 문자열로, 흔히 웹 사이트의 주소로 정의됩니다. URI를 활용하면 원하는 웹사이트에 접근하거나 자원들을 식별 가능하다.
</details>

<details>
  
  <summary><strong>URI의 구조 6가지에 대해서 설명해주세요.</strong></summary>

  ### URI의 구조
  * scheme:[//authority]path[?query][#fragment]

  ### 스키마
  * 사용자와 자원사이의 통신 규칙을 나타낸다 (e.g. https)

  ### 호스트
  * IP 혹은 도메인으로 자원의 주소를 나타낸다. (e.g. naver.com)

  ### 포트
  * 포트번호이며, 하나의 컴퓨터 안에 여러 개의 서버가 있을때 어떤 서버와 통신할지 나타낸다. 웹 서버는 80번 포트를 사용한다는 무언의 규칙이 존재해 생략 가능하다. (e.g. :80)

  ### 경로 (URL Path)
  * 자원의 경로를 나타낸다. (e.g. /webtoon)

  ### 쿼리 스트링 (Qurey String)
  * 주소 뒤에 덧붙여 추가적인 정보를 서버 측으로 전달하는 방식으로 사용자가 어떤 자원을 원하는지 알려준다. (e.g. list?titleId=812354&tab=thu)

  ### 프래그먼트 (Fragment)	
  * 특정 페이지 내 위치 지정 (e.g #section2)
</details>

<details>
  
  <summary><strong>URL과 URN을 URI릍 통해서 설명해주세요.</strong></summary>

  ### URL (Uniform Resource Locator)
  * 자원의 "위치"를 나타냅니다. 특정 자원에 접근하기 위한 방법(프로토콜)과 경로를 포함합니다. (e.g. ftp://ftp.example.com/file.txt (FTP 파일))
  * 특징 :
    1. 인터넷 상에서 특정 자원의 "위치"를 가리킴
    2. 웹 브라우저에서 직접 접근 가능
    3. 스키마(프로토콜) 필수 (예: https://, ftp://)
    4. 쿼리 스트링, 포트, 프래그먼트 등이 추가될 수 있음

  ### URN (Uniform Resource Name)
  * 자원의 "이름"을 나타냅니다. 특정 위치와 무관하게 자원을 식별하는 고유한 이름을 제공하며, 보편적으로 변하지 않습니다. (e.g. urn:isbn:0451450523 (책 ISBN))
  * 특징 : 
    1. 자원의 고유한 이름을 제공 (위치와 무관)
    2. 특정한 네임스페이스(namespace)를 사용
    3. 웹 브라우저에서 직접 접근 불가 (위치 정보 없음)
    4. 예: ISBN(책 번호), RFC 문서, UUID 등

  ### URI와 URL,URN과의 관계
  * URI는 자원을 식별하는 모든 문자열을 포함하며, 그중 URL은 "위치", URN은 "이름"에 초점을 맞춘 개념입니다.
  * 모든 URL과 URN은 URI에 속하지만, 모든 URI가 반드시 URL 또는 URN인 것은 아닙니다.
    * URI: 자원을 식별하는 모든 문자열
    * URL: 위치 기반의 식별자 (어디 있는지)
    * URN: 이름 기반의 식별자 (무엇인지)

</details>