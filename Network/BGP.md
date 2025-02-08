<details>
  <summary><strong> BGP의 개념과 특징에 대해 설명해주세요. </strong></summary>
  
  ## BGP
  - 인터넷에 존재하는 수천 개의 ISP와 대형 네트워크(AS)들을 연결하는 프로토콜
  - ISP와 대규모 네트워크 간의 경로를 조정하는 핵심 라우팅 프로토콜 </br>
    ex) 네이버에서 구글로 데이터를 보내야한다면, BGP가 최적의 경로를 찾아준다.
    - ISP : KT,SKT, LG U+등의 인터넷 서비스 제공자
  

  **1) ISP와 AS간의 라우팅 담당(EGP)**
  - BGP는 AS(자율 시스템) 간의 경로를 조정하는 EGP(Exterior Gateway Protocol)
  - OSPF, RIP 같은 내부 라우팅 프로토콜과 다르게, 대형 ISP 및 네트워크 간의 연결을 관리. </br>
    즉, 인터넷 전체에서 데이터가 이동할 경로를 조정하는 프로토콜

  **2) 최단 거리보다 정책 기반 경로 선택** 
  - BGP는 단순히 짧은 길이 아니라, 비용/정책/네트워크 안정성 등을 고려한 최적의 경로를 선택한다.

  **3) 경로(Vector)기반 라우팅**
  - BGP는 경로 벡터 알고리즘을 사용해서 데이터를 보낼 최적의 경로를 계산한다.
  - 이때 AS-Path(거쳐가야할 AS 목록)을 기준으로 경로를 결정한다.

  **4) 2가지 종류의 BGP**
  - eBGP(External BGP) : 다른 AS 간의 라우팅
  - iBGP(Internal BGP) : 같은 AS 내부에서 BGP 사용

    
</details>
