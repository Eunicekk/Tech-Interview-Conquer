# Spring MVC 요청 흐름

---

## 면접 질문 예시

> "Spring MVC 요청 처리 흐름은 어떻게 되나요?"

---

<details>
  <summary><h2> 평가 요소 및 모범 답안</h2></summary>

![Spring MVC 요청 흐름](https://github.com/liarreez/Tech-Interview-Conquer/blob/main/Question/Language%20%26%20Framework/img/RequestLifecycle.png)

  ### 1. Spring MVC 요청 처리 흐름 및 각 과정의 역할 이해
  - 포함내용
    1) **DispatcherServlet** : Spring에서 모든 요청을 받아 처리하는 프론트 컨트롤러
    2) **HandlerMapping** : 요청 URL을 처리할 수 있는 Controller 탐색
    3) **HandlerAdapter** : 컨트롤러의 비즈니스 로직 처리를 호출
    4) **Controller** : 비즈니스 로직을 수행하고 처리 결과를 Model에 담은 후 View 이름을 HandlerAdapter에 반환
    5) **ViewResolver** : View 이름에 해당하는 View 탐색 후 반환
    6) **View** 렌더링 : View는 Model을 이용하여 화면 표시
    
  ### 2.모범 답안 예시
      "Spring MVC에 요청이 오면 DispatcherServlet이 받아서 HandlerMapping에 보내 처리할 수 있는 Controller를 찾습니다  
      HandlerAdapter는 해당 Controller를 호출하고 Controller는 비즈니스 로직 수행 후 결과를 Model에 담아 View 이름과 함께 반환합니다  
      ViewResolver는 View 이름에 해당하는 View를 탐색 후 반환하고 View에서 렌더링을 거쳐 화면에 표시됩니다"
