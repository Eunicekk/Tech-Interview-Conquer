<details>
  <summary><strong>Program과 Process에 대해서 설명해 주세요</strong></summary>

<br>

  ### Program  
  프로그램은 특정 작업을 수행하기 위해 작성된 코드와 필요한 데이터의 묶음으로 저장 장치에 저장된 정적인 상태입니다.
  
<br>

  ### Process   
  프로세스는 메모리에서 실행중인 프로그램으로 동적인 상태입니다.

<br>

* Processor : 명령어를 해석하고 연산 및 제어 작업을 수행하여 프로그램을 실행하는 컴퓨터의 중앙 처리 장치(CPU)
</details>

<details>
  
  <summary><strong>Process의 상태에는 어떠한 것들이 있나요?</strong></summary>

<br>


프로세스가 생성되는 동안에는 **초기(생성) 상태**가 됩니다. 프로세스가 실행할 준비는 되었으나 프로세서가 다른 프로세스를 실행하는 등의 이유로 대기 중인 경우는 **준비 상태**입니다.  
프로세스가 프로세서에서 실행 중인 상태를 **실행 상태**라고하며, 프로세스가 입출력 요청과 같이 다른 사건을 기다리며 중단된 경우 **대기 상태**가 되고 대기 상태가 끝난 프로세스는 준비 상태가 됩니다.  
종료된 프로세스는 운영체제가 PCB와 사용한 메모리를 정리하는 **종료 상태**가 되는데, 종료 후에도 메모리에 남아 있는 경우 **최종(좀비) 상태**라고 합니다.

<br>

* PCB(Process Control Block) : 프로세스의 상태, PID(식별자), 레지스터 값, 메모리 관리 정보 등 프로세스의 관리를 위한 정보를 저장하는 자료 구조
* 최종(좀비) 상태를 활용하는 경우 : 부모 프로세스가 자식 프로세스가 성공적으로 실행됐는지 확인하는 경우
</details>

<details>
  <summary><strong>프로그램이 실행되는 과정을 설명해 주세요</strong></summary>

<br>

1. 운영체제가 디스크에 저장된 프로그램을 메모리에 로드(지연 로드) 합니다  
2. 실행 시간 스택을 메모리에 할당하고 함수 인자 및 지연 변수를 저장하기 위해 스택을 초기화 합니다. 또한 동적 메모리 할당을 위해 힙 영역을 메모리 영역에 할당합니다  
3. 입출력, 에러 메세지를 처리하기 위해 표준 입력, 출력, 에러와 같은 기본 파일 디스크럽터를 초기화하여
4. 운영체제는 프로그램의 시작 지점(main() 함수와 같은)에서 프로그램을 실행합니다  

* 지연 로드 : 필요할 때 필요한 부분만을 메모리에 로드 하는 방법으로 페이징, 스와핑과 같은 방법을 사용합니다
   
</details>