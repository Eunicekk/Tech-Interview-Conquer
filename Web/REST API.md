<details>
  <summary><strong>REST API란 무엇인가요?</strong></summary>

<br>

  ### REST API(Representational State Transfer Application Programming Interface)
  REST API는 웹 서비스에서 데이터를 교환하고 시스템 간 통신을 하는 아키텍처 스타일 중 하나입니다.  
  REST API의 기본원칙에는 URL을 통한 자원 식별, HTTP 메서드를 활용한 작업 정의, 상태 무저장, 다양한 형식(JSON, XML 등)의 자원 표현 등이 있습니다.
  REST API는 URI를 통한 자원 식별로 가독성이 높고, HTTP 메서드를 활용하여 표준적이며 상태를 저장하지 않기에 클라이언트와 서버가 독립적으로 확장 가능하다는 장점이 있습니다.  
  반면, 상태를 유지해야 하는 경우와 복잡한 관계형 데이터를 사용해야하는 경우에는 부적합하며 매 요청마다 인증 및 상태 정보 제공을 해야하는 오버헤드가 있다는 단점이 있습니다.

<br>

#### RESP API 특징 
- URI을 통한 자원 식별  
`https://example.com/users/5` -> 5번 유저에 접근
- HTTP 메서드를 활용한 작업 정의
  * GET : 조회
  * POST : 생성
  * PUT : 전체 수정
  * PATCH : 일부 수정
  * DELETE : 삭제
- 상태 무저장(Stateless)
  * 서버가 클라이언트의 상태를 저장하지 않음, 모든 요청은 독립적
  * 요청 시 필요한 모든 정보를 포함해야 함(인증 토큰 등)
- 다양한 형식의 자원 표현
  * 클라이언트 Accept 헤더를 사용해 원하는 형식을 지정하고 서버는 요청에 맞는 형식으로 데이터 반환
JSON 예시
```json
{
  "id": 5,
  "name": "Alice"
}
```
- 캐싱 가능
  * HTTP 캐싱 헤더를 사용하여 클라이언트가 같은 요청의 데이터는 캐싱해두고 재사용
- 계층화
  * 클라이언트와 서버가 독립적이므로 중간 계층(로드 밸런서, 프록시 등)을 사용할 수 있음
  * 클라이언트는 통신하고 있는 대상이 서버인지 중간 계층인지 알지 못함
- 인터페이스의 일관성
  * 자원을 URI로 표현, HTTP 메서드로 작업 정의, 일관된 응답 형식, HTTP 상태 코드 등 일관적인 방법을 사용

<br>


#### RESP API 예시  
`DELETE https://example.com/users/5` -> ID가 5인 사용자를 삭제
<br>

</details>
