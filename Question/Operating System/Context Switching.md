# 컨텍스트 스위칭

---

## 면접 질문 예시

> “컨텍스트 스위칭이란 무엇인지 설명해주시고, 왜 발생하며 시스템 성능에 어떤 영향을 미치는지 구체적으로 설명해 주실 수 있나요? 또한, 컨텍스트 스위칭의 오버헤드를 줄이기 위한 방법이 있다면 함께 말씀해 주세요.”

---

<details>
  <summary><h2> 평가 요소 및 평가 요소 별 모범 답안</h2></summary>

  ### 1. 컨텍스트 스위칭의 정의 및 개념 이해
  - 포함내용
    - 정의: 컨텍스트 스위칭이란 실행 중인 프로세스나 스레드의 상태(레지스터, 프로그램 카운터, 스택 포인터 등)를 저장하고, 다른 프로세스나 스레드의 상태를 복원하는 과정임.
    - 목적: 멀티태스킹 환경에서 CPU 자원을 효율적으로 분배하기 위한 필수 메커니즘.
      
  - <details>
    <summary>모범 답안 예시 : </summary>
    
      > "컨텍스트 스위칭은 운영체제가 멀티태스킹 환경에서 하나의 프로세스나 스레드의 상태를 저장하고, 다른 프로세스나 스레드의 상태를 복원하여 실행하는 과정을 의미합니다."
    </details>

  ### 2. 컨텍스트 스위칭 발생 원인 및 이유
  - 포함내용
    - 원인: 인터럽트, 시스템 콜, I/O 요청, 또는 선점 스케줄링 등의 이벤트로 인해 발생.
    - 이유: 여러 프로세스 간에 CPU 자원을 효율적으로 할당하기 위해 필요.
  - <details>
    <summary>모범 답안 예시 : </summary>
    
      > "컨텍스트 스위칭은 인터럽트, 시스템 콜, I/O 요청 또는 선점 스케줄링에 의해 발생하며, 이는 CPU를 여러 프로세스에 효율적으로 할당하기 위한 필수 과정입니다."
    </details>

  ### 3. 컨텍스트 스위칭의 오버헤드 및 시스템 성능 영향
  - 포함내용
    - 오버헤드: 상태 저장 및 복원, 캐시 무효화(컨텍스트 스위칭 시, 이전 프로세스의 데이터가 새로운 프로세스에 적합하지 않거나 오래된 정보일 수 있으므로, 해당 데이터를 제거하거나 초기화하는 과정), TLB 플러시(TLB(Translation Lookaside Buffer)는 가상 주소와 물리 주소 간의 매핑 정보를 캐시하는 공간이다. 프로세스 전환 시, 각 프로세스마다 주소 매핑 정보가 다르기 때문에 이전 프로세스의 TLB 엔트리를 제거해 새 프로세스의 올바른 주소 매핑이 반영되도록 하는 과정) 등으로 인한 추가 처리 시간.
    - 성능 영향: 빈번한 스위칭은 CPU 이용률 저하, 캐시 효율 감소, 전체 시스템 성능 저하를 초래할 수 있음.
  - <details>
    <summary>모범 답안 예시 : </summary>

      > "컨텍스트 스위칭은 프로세스 상태를 저장하고 복원하는 동안 캐시 무효화와 TLB 플러시 등으로 인해 오버헤드가 발생하며, 이로 인해 빈번한 스위칭은 CPU 이용률 저하와 캐시 효율 감소로 전체 시스템 성능에 부정적인 영향을 미칠 수 있습니다."
    </details>

  ### 4. 컨텍스트 스위칭 오버헤드 최적화 방안
  - 포함내용
    - 최적화 방법: 타임 슬라이스 조정(타임슬라이스는 CPU가 한 프로세스에 할당하는 일정 시간 단위, 타임슬라이스가 너무 짧으면 잦은 컨텍스트 스위칭으로 오버헤드가 증가하고, 너무 길면 응답 시간이 늘어나는 trade-off가 존재재), 경량 스레드(경량 스레드는 일반 스레드보다 생성, 전환, 관리에 필요한 오버헤드가 낮은 스레드를 의미) 사용, 스케줄링 알고리즘 개선 등을 통한 스위칭 빈도 감소.
    - 추가 고려: 하드웨어 최적화 기술 및 스케줄러 설계 개선.
  - <details>
    <summary>모범 답안 예시 : </summary>

      > "컨텍스트 스위칭 오버헤드를 줄이기 위해, 적절한 타임 슬라이스 설정과 경량 스레드 사용, 그리고 스케줄링 알고리즘 개선을 통해 스위칭 빈도를 최소화할 수 있으며, 최신 CPU의 하드웨어 최적화 기술을 활용하는 것도 효과적인 방법입니다."
    </details>

  ### 5. 실제 사례 및 운영체제 적용 사례
  - 포함내용
    - 실제 적용: 리눅스, 윈도우 등에서 컨텍스트 스위칭 관리 및 최적화 방법.
    - 최적화 사례: 하이브리드 스케줄링 기법이나 커널 최적화를 통한 오버헤드 감소 사례.
  - <details>
    <summary>모범 답안 예시 : </summary>

      > "예를 들어, 리눅스에서는 CFS(Completely Fair Scheduler)를 통해 컨텍스트 스위칭의 오버헤드를 최소화하며, 최신 운영체제들은 하이브리드 스케줄링 기법을 도입하여 응답성과 효율성을 동시에 고려하고 있습니다."
    </details>

  ### 6. 심화 지식
  - 포함내용:
    - 컨텍스트 스위칭 상세 과정:
      - 상태 저장: 현재 실행 중인 프로세스나 스레드의 레지스터, 프로그램 카운터, 스택 포인터 등 필수 상태 정보를 저장합니다.
      - PCB 업데이트: 저장된 상태 정보를 해당 프로세스의 프로세스 제어 블록(PCB)에 기록합니다.
      - 캐시 무효화 및 TLB 플러시: 필요에 따라 이전 프로세스의 캐시 데이터를 무효화하고, TLB(Translation Lookaside Buffer)의 이전 엔트리를 제거합니다.
      - 상태 복원: 스케줄러가 다음 실행할 프로세스를 결정하면, 해당 프로세스의 PCB에 저장된 상태 정보를 복원하여 CPU에 로드합니다.
      - 전환 완료: CPU가 새로운 프로세스로 전환되며 실행을 시작합니다.
    - 고급 최적화 기법: 커널 모드에서 경량 스레드 전환, 코루틴(코루틴은 스레드보다 훨씬 가벼운 실행 단위로, 컨텍스트 스위칭 오버헤드를 최소화할 수 있다) 사용,하드웨어 지원 최적화 기술 등.
  - <details>
    <summary>모범 답안 예시 :</summary>
    
      > "컨텍스트 스위칭은 다음과 같은 단계를 거칩니다. 먼저, 현재 실행 중인 프로세스나 스레드의 레지스터, 프로그램 카운터, 스택 포인터 등 필수 상태 정보를 저장하여 해당 프로세스의 PCB(Process Control Block)에 기록합니다. 그 다음, 필요에 따라 이전 프로세스의 캐시 데이터를 무효화하고 TLB(Translation Lookaside Buffer)의 이전 엔트리를 플러시하여, 잔여 데이터가 새 프로세스에 영향을 주지 않도록 합니다. 이후 스케줄러가 다음 실행할 프로세스를 결정하면, 그 프로세스의 PCB에 저장된 상태 정보를 복원하여 CPU에 로드하고 전환을 완료합니다. 이 과정에서는 커널 모드와 사용자 모드 간 전환이 발생할 수 있으며, 최신 하드웨어는 이러한 전환 오버헤드를 최소화하는 최적화 기술을 제공합니다. 또한, 고급 최적화 기법으로는 커널 모드에서 경량 스레드 전환을 활용하거나, 사용자 모드에서 코루틴을 사용해 스위칭 오버헤드를 줄이는 방법 등이 있습니다."
    </details>
</details>