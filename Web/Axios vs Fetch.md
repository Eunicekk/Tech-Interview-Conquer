<details>
  <summary><strong>Axios와 Fetch에 대해 설명해주세요.</strong></summary>

<br>

 ## 웹에서의 비동기 처리 : Axios 와 Fetch

 ### Axios

 ```javascript
   // GET 요청
   axios.get('https://api.example.com/data', {
      // 옵션
      params: {
          id: 123
      },
      headers: {
          'Authorization': 'Bearer token123'
      }
    })
    .then(response => {
      console.log(response.data);
    })
    .catch(error => {
      console.error('에러 발생:', error);
    });
 ```
  1. Node와 클라이언트에서 모두 작동하는 라이브러리 형태로, 따로 npm을 사용하여 설치가 필요함. (thrid-party library)
  2. JSON 형태로 자동 파싱
  3. Interceter, Instance, timeout 등 다양한 기능 제공
  4. catch 블록에서 에러처리가 용이
  5. 번들 사이즈가 커서 로딩 시간이 오래 걸리고, 무겁다.(=상대적으로 느리다)

<br>
 ### Fetch

 ```javaScript
  const res = await fetch(url, {
                                  method: 'GET',
                                  headers: {
                                    'Content-Type': 'application/json'
                                  }
                                });

  res.status;  // response 코드
  res.headers;  // response 헤더
  
  // response body
  await res.json(); // JSON 문자열을 파싱해서 자바스크립트 객체로 변환함.
  await res.text(); // 문자열을 그대로 가져옴.
 ```

 1. 이미 웹 브라우저에 내장되어 있는 API로, 따로 설치가 필요 없어서 가볍다(=빠르다). (웹 표준 API로, 모든 브라우저 호환 가능)
 2. Axios와는 다르게 수동 구현해야 하는 기능들이 존재 (ex. Intercepter)
 3. JSON형태로 응답이 오지 않아서 응답을 JSON으로 받고 싶다면, 파싱을 따로 해줘야 한다.
 4. HTTP 에러코드 중 404, 500 등 HTTP 오류상태코드는 자동 에러처리가 되지 않는다. 네트워크 요청이 성공하면 200번대 코드는 무조건 Promise를 반환한다. → **따라서 상태(status)를 통해 직접 다 핸들링을 해줘야 한다.

![image](https://github.com/user-attachments/assets/afa465a2-c088-498c-b820-99c7e8773ffe)

  
</details>
