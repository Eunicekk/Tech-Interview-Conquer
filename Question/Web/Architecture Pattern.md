# 아키텍처 패턴(MVC, MVP, MVVM)

---

## 면접 질문 예시

> "알고 계신 아키텍처 패턴(MVC, MVP, MVVM)에 대해서 설명해 주세요”

---

<details>
  <summary><h2> 평가 요소 및 모범 답안</h2></summary>

  ### 1. MVC 정의 및 장단점 이해
  - 포함내용
    * 정의 : 애플리케이션을 Model, View, Controller 세 가지 역할로 분리한 아키텍처 패턴
    * 역할
      - Model : 데이터 및 비즈니스 로직 담당
      - View : 사용자에게 보여지는 부분 담당(UI)
      - Controller : 사용자의 요청을 받아 Model의 적절한 함수를 호출
    * 동작 과정
      1) 사용자의 요청이 Controller에 전달
      2) Controller는 요청에 알맞는 Model의 함수 호출
      3) Model에서 데이터 및 비즈니스 로직을 통해 요청 처리
      4) Model에서 처리한 결과를 View에 전달
      6) View는 전달받은 결과를 화면에 표시
    * 장점 : 역할 분리로 인한 유지보수 용이, 단순한 구조로 관리 용이
    * 단점 : Model과 View의 직접적인 의존관계, Controller의 규모가 거대해짐
    * Controller와 View는 1 : N 관계
   
  ### 2. MVP 정의 및 장단점 이해
  - 포함내용
    * 정의 : 애플리케이션을 Model, View, Presenter 세 가지 역할로 분리한 아키텍처 패턴
    * 역할
      - Model : 데이터 및 비즈니스 로직 담당
      - View : 사용자에게 보여지는 부분 담당(UI), 사용자의 요청을 받음
      - Presenter : View와 Model의 중간다리 역할
    * 동작 과정
      1) 사용자의 요청이 View 전달
      2) View는 요청을 Presenter에 전달
      3) Presenter는 요청에 알맞는 Model의 함수 호출
      4) Model에서 데이터 및 비즈니스 로직을 통해 요청 처리
      5) Model에서 처리한 결과를 Presenter에 전달
      6) Presenter는 결과를 View에 전달
      7) View는 전달받은 결과를 화면에 표시
    * 장점 : View와 Model의 의존성이 낮아짐, View 추상화 사용 -> 테스트와 유지보수에 용이
    * 단점 : View 인터페이스 관리가 어려움, Presenter 규모가 거대해짐
    * Presenter와 View는 1 : 1 관계
   
  ### 3. MVVM 정의 및 장단점 이해
  - 포함내용
    * 정의 : 애플리케이션을 Model, View, ViewModel 세 가지 역할로 분리한 아키텍처 패턴
    * 역할
      - Model : 데이터 및 비즈니스 로직 담당
      - View : 사용자에게 보여지는 부분 정의(UI), 데이터 바인딩을 통한 화면 업데이트, 사용자의 요청을 받음
      - ViewModel : View와 Model의 중간다리 역할, View가 필요로 하는 데이터를 가공하거나 준비하여 노출(바인딩)하는 로직 담당
    * 동작 과정
      1) 사용자의 요청이 View 전달
      2) View는 요청을 ViewModel에 전달
      3) ViewModel 요청에 알맞는 Model의 함수 호출
      4) Model에서 데이터 및 비즈니스 로직을 통해 요청 처리
      5) Model에서 처리한 결과를 ViewModel에 전달
      6) ViewModel은 결과를 저장
      7) View는 ViewModel과의 데이터 바인딩을 통해 결과를 화면에 표시
    * 장점 : 데이터 바인딩을 통한 UI 갱신 로직 단순화, View와 Model의 의존성 감소
    * 단점 : 데이터 바인딩 초기 설정 어려움, ViewModel 규모가 거대해짐
    * ViewModel과 View는 1 : N 관계
  
  ### 2.모범 답안 예시
    
      "MVC 패턴은 Model, View, Controller 세 가지 역할로 분리한 아키텍처 패턴으로 Model은 데이터 및 비즈니스 로직을 담당하고, View는 사용자에게 보여지는 부분을 담당하고, Controller는 사용자의 요청을 받아 Model에 전달하는 역할을 담당합니다  
      이 패턴은 Model과 View에 의존성이 높다는 단점이 있는데, 이를 극복하기 위한 패턴으로 MVP와 MVVM 패턴이 있습니다  
      MVP 패턴은 Controller 대신에 Presenter를 사용하고 데이터의 요청은 View가 받고 Presenter는 View와 Model의 중간다리 역할을 합니다  
      MVVM 패턴은 Controller 대신에 ViewModel을 사용해서 데이터의 요청은 View가 받고 ViewModel과의 데이터 바인딩을 통해 UI를 갱신하는 방식을 사용합니다"
  
    
