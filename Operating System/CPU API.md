<details>
  <summary><strong>fork, wait, exec 시스템 호출에 대해 각각 설명해주세요.</strong></summary>

<br>

  ### fork() 시스템 콜
  
  - 현재 프로세스의 복사본을 만들어 새로운 프로세스를 생성한다.
  - 자식 프로세스는 자신의 주소공간, 자신의 레지스터, 자신의 PC 값을 갖는다.
  - 반환값 : 부모 프로세스는 자식 프로세스의 PID를 반환받고, 자식 프로세스는 0을 반환받는다.
  - 반환값의 차이로 인해, 부모와 자식 프로세스가 서로 다른 코드를 실행하는 프로그램을 쉽게 작성할 수 있다.

  ### wait() 시스템 콜

  - 부모 프로세스가 자식 프로세스가 종료될때까지 기다린다.
  - 자식 프로세스가 종료되면 wait()는 자식의 종료 상태를 반환한다.

  ### exec() 시스템 콜

  - 현재 프로세스를 종료하고, 새로운 프로그램을 실행한다.
  - 실행 파일의 코드와 데이터를 현재 프로세스의 메모리 공간에 덮어쓴다. exec() 호출 이후에는 기존 프로세스 코드로 돌아가지 않는다.
  
<br>
</details>


<details>
  <summary><strong>왜 fork()와 exec()를 분리해서 사용할까요?</strong></summary>

<br>

  ### 쉘의 기능 구현을 가능하게 하기 위해서 입니다.

  Unix의 쉘은 사용자의 명령을 받아서 새로운 프로그램을 실행하는 역할을 합니다.
  
  사용자가 명령을 입력하면 쉘은 fork()을 호출하여 자식 프로세스를 만들고, 
  exec()을 호출하기 전에 자식 프로세스에서 환경 변수 설정이나 파이프 연결 등의 실행 환경을 설정합니다.
  이후 exec()로 새로운 프로그램을 실행합니다.

  이처럼 fork와 exec를 분리했기 때문에 쉘은 명령 실행 전에 환경을 자유롭게 조정할 수 있습니다.
  
<br>
</details>
