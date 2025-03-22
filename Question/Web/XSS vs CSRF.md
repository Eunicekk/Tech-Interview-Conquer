# 크로스사이트 스크립팅(XSS)과 크로스사이트 요청 위조(CSRF)

---

## 면접 질문 예시

> "크로스사이트 스크립팅(XSS)과 크로스사이트 요청 위조(CSRF) 공격의 원리와, 이를 방지하기 위한 방법에 대해 설명해 주세요.”

---

<details>
  <summary><h2> 평가 요소 및 모범 답안</h2></summary>

  ### 1. 크로스사이트 스크립팅(XSS) 공격
  - 포함내용
    * XSS 공격 원리
      - XSS(Cross-Site Scripting)는 공격자가 악성 JavaScript를 웹 페이지에 삽입하여, 사용자의 브라우저에서 실행되도록 하는 공격입니다.
      - 이를 통해 세션 탈취, 키로깅, 피싱, 악성 코드 실행 등의 피해가 발생할 수 있습니다.
   
  ### 2. XSS 공격 방지 방법
  - 포함내용
    - 입력값 검증(Input Validation): 사용자가 입력하는 모든 데이터를 철저하게 검사
    - 출력 인코딩(Output Encoding): HTML, JavaScript, URL 등을 안전하게 변환
    - 콘텐츠 보안 정책(CSP, Content Security Policy): 신뢰할 수 있는 스크립트만 실행하도록 제한
    - HttpOnly 쿠키 설정: JavaScript에서 접근할 수 없도록 설정하여 쿠키 탈취 방지
   
  ### 3. 크로스사이트 요청 위조(CSRF) 공격
  - 포함내용
    * XSS 공격 원리
      - CSRF(Cross-Site Request Forgery)는 공격자가 사용자의 인증된 세션을 악용하여, 원치 않는 요청을 서버로 보내는 공격입니다.
     
  ### 4. CSRF 공격 방지 방법
  - 포함내용
    - CSRF 토큰 사용: 모든 요청에 난수 기반 CSRF 토큰을 포함하여, 서버에서 이를 검증
    - SameSite 쿠키 설정: 쿠키가 같은 사이트에서만 전송되도록 제한 (SameSite=Strict 또는 SameSite=Lax)
    - Referer 및 Origin 검사: 요청이 올바른 도메인에서 온 것인지 확인
    - CORS 정책 설정: 신뢰할 수 있는 출처에서만 요청을 허용
  
  ### 5. 모범 답안 예시

  > XSS(Cross-Site Scripting)는 악성 스크립트를 웹 페이지에 삽입하여 사용자 브라우저에서 실행되도록 하는 공격입니다.<br />
  > CSRF(Cross-Site Request Forgery)는 사용자의 인증 정보를 악용하여 원치 않는 요청을 실행하는 공격입니다.<br />
  > XSS는 HTML, JavaScript 등을 비활성화하여 비정상적인 스크립트 실행을 막거나, CSP정책을 설정하여 외부 리소스가 불러오거나 실행되는 것을 막을 수 있습니다.<br />
  > 또한 쿠키의 HTTPOnly 설정을 하여 JavaScript를 통한 쿠키의 접근을 막을 수 있습니다.<br />
  > CSRF 토큰을 생성해서 매 요청마다 헤더에 담아서 보내거나, 쿠키의 SameSite 설정을 통해 완전히 동일한 사이트에서만 요청을 보내도록 하여 막을 수 있습니다.<br />
</details>
