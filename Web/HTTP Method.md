<details>
  <summary><strong> HTTP 메서드에 대해 아는 대로 말해보세요</strong></summary>

  클라이언트는 서버에 **HTTP 메서드**를 통해 리소스에 수행하길 원하는 행동을 냅니다

  1) **GET**
     * 행동 : 서버에서 리소스를 가져옴
     * URL 쿼리 파라미터로 데이터 전달, 바디로 데이터 전달 비권장
     * 캐싱 O, 멱등성 O, 안정성 O
  2) **POST**
     * 행동 : 서버에서 리소스를 생성, 서버에 리소스를 전송
     * 요청 바디에 데이터 전달
     * 캐싱 X, 멱등성 X, 안정성 X
  3) **PUT**
     * 행동 : 서버의 리소스를 완전히 업데이트, 기존 리소스가 없으면 생성
     * 요청 바디에 리소스 전체를 담아 전송
     * 캐싱 X, 멱등성 O, 안정성 X
  4) **PATCH**
     * 행동 : 서버의 리소스의 일부를 업데이
     * 요청 바디에 리소스 일부를 담아 전송
     * 캐싱 X, 멱등성 X, 안정성 X
  5) **DELETE**
     * 행동 : 서버에서 특정 리소스를 삭제
     * URL 쿼리 파라미터로 데이터 전달, 바디로 데이터 전달 비권장
     * 캐싱 X, 멱등성 O, 안정성 X
  6) **OPTIONS**
     * 행동 : 특정 리소스 또는 서버 전체가 어떤 메서드, 기능을 지원하는지에 대한 정보 요청
     * CORS 환경에서 허용 메서드 헤더 확인을 위해 사용
     * 캐싱 X, 멱등성 O, 안정성 O
    
  <br>

  - **캐싱** : 리소스의 복사본을 저장하다가 요청 시 복사본을 제공
  - **멱등성** : 동일한 요청을 여러 번 호출해도 결과가 동일
  - **안정성** : 서버의 상태를 변경하지 않음

</details>
