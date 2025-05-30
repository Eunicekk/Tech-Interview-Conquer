<details>
  <summary><strong> Docker란 무엇이며, 사용하는 주요 이유는 무엇인지 설명해주세요. </strong></summary>

  ### Docker
  컨테이너화 기술을 제공하는 플랫폼으로, 애플리케이션과 해당 종속성을 컨테이너라는 단위로 패키징하여 어디서든 일관된 환경에서 실행할 수 있도록 합니다.

  ### 주요 사용 이유
  - 이식성: 개발 환경과 프로덕션 환경 간의 차이를 줄일 수 있음
  - 경량성: 가상 머신에 비해 리소스 사용이 적음
  - 빠른 배포: 컨테이너는 가볍고 실행 속도가 빠름
  - 확장성: 분산 시스템에서 손쉽게 확장 및 관리를 할 수 있음

</details>

<details>
  <summary><strong> Docker 이미지와 컨테이너의 차이점은 무엇인지 설명해주세요. </strong></summary>

  ### Docker 이미지
  - 컨테이너를 실행하기 위한 불변의 읽기 전용 템플릿입니다. 
  - 애플리케이션 코드, 런타임, 라이브러리 및 환경 설정이 포함되어 있습니다.

  ### Docker 컨테이너
  - 이미지를 기반으로 실행되는 동적인 실행 환경입니다.
  - 이미지를 읽기 전용으로 사용하지만, 컨테이너 내부에서는 데이터를 추가하거나 변경할 수 있습니다. 
  - 실행 중인 컨테이너는 특정 프로세스와 네트워크 환경을 포함합니다.

</details>

<details>
  <summary><strong> Docker에서 볼륨(Volume)은 무엇이며, 왜 필요한지 설명해주세요. </strong></summary>

  ### Docker 볼륨
  컨테이너와 호스트 간에 데이터를 영구적으로 저장하거나 공유하기 위한 방법입니다.

  ### 필요 이유
  - 데이터 지속성: 컨테이너가 삭제되어도 볼륨에 저장된 데이터는 유지됨
  - 공유 및 협업: 여러 컨테이너 간에 데이터를 공유 가능
  - 성능 향상: Docker가 관리하는 볼륨은 일반적으로 바인드 마운트보다 더 나은 성능 제공
  - 유연성: 호스트 파일 시스템의 경로를 직접 지정하지 않고 데이터를 쉽게 관리 가능

</details>

<details>
  <summary><strong> Docker의 컨테이너화 기술은 가상 머신(Virtual Machine)과 어떻게 다른지 설명해주세요. </strong></summary>

  ### 가상 머신
  가상 머신(VM)은 하이퍼바이저를 통해 호스트 시스템 위에 독립적인 운영 체제(OS)를 실행하는 기술입니다. 각 VM은 완전한 OS를 포함하므로 격리가 강력하지만 리소스 소비가 크고 실행 속도가 느립니다.

  ### 차이점
  Docker 컨테이너는 애플리케이션과 필요한 환경만 포함하며, 호스트 OS의 커널을 공유해 경량화된 실행 환경을 제공합니다.

  - 구조: VM은 독립된 OS를 포함, 컨테이너는 호스트 OS를 공유
  - 성능: 컨테이너는 경량화되어 빠르고, VM은 상대적으로 무거움
  - 이식성: 컨테이너는 "Write Once, Run Anywhere" 원칙으로 환경 간 이동이 용이
  - 사용 사례: VM은 OS 단위 격리, 컨테이너는 애플리케이션 중심의 경량 배포에 적합

</details>