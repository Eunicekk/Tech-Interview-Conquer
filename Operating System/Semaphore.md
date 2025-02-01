<details>
  
<summary>
  <strong>세마포어와 기본 연산에 대해 설명하세요.</strong>
</summary>

<br>

  ### 세마포어 (Semaphore)
  - 두 개의 원자적 함수로 조작되는 정수 변수입니다.
  - 다중 스레드나 프로세스가 공유하는 자원에 대한 접근을 제어하여, 임계 구역에 안전하게 접근할 수 있도록 조율합니다.
  - 병렬 프로그래밍에서 동기화를 제공합니다.

  #### 세마포어 초기화
  세마포어를 사용하기 전에 반드시 초기화해야 합니다.
  
  ```c
  #include <semaphore.h>
  sem_t s;
  sem_init(&s, 0, 1);
  ```
  - 첫 번째 인자: 세마포어 객체
  - 두 번째 인자: 0은 같은 프로세스 내 스레드 간 공유를 의미
  - 세 번째 인자: 세마포어 초기값

  세 번째 인자인 초기값은 사용 용도에 따라 달라집니다.
  
  락으로 사용할 경우 초기값은 1, 특정 조건 대기를 위해 사용할 경우 초기값은 0으로 설정합니다.

  #### sem_wait()
  ```c
  int sem_wait(sem_t *s) {
    decrement the value of semaphore s by one;
    wait if value of semaphore s is negative;
  }
  ```
  세마포어 값을 1씩 감소시키고 값이 음수일 경우 호출자를 대기 상태로 전환합니다.

  #### sem_post()
  ```c
  int sem_post(sem_t *s) {
    increment the value of semaphore s by one;
    if there are one or more threads waiting, wake one;
  }
  ```
  세마포어 값을 1씩 증가시키며 대기 중인 스레드가 있다면 하나를 깨웁니다.

<br>
</details>

<details>
  
<summary>
  <strong>이진 세마포어와 그 동작 과정에 대해 설명하세요.</strong>
</summary>

<br>

  ### 이진 세마포어 (락)
  - 이진 세마포어는 값이 0 또는 1만 가지는 세마포어로, 락과 동일한 기능을 합니다.
  - 락은 하나의 스레드만 임계 영역에 접근하도록 보장합니다.

  ```c
  sem_t lock;
  sem_init(&lock, 0, 1);  // 초기값 1
  sem_wait(&lock);        // 락 획득
  // 임계 영역
  sem_post(&lock);        // 락 해제
  ```

  #### 동작 과정
  1. 세마포어 값이 1인 상태에서 sem_wait()를 호출하면 값이 0이 되고 락을 획득합니다.
  2. 다른 스레드가 락을 요청하면 세마포어 값이 음수가 되고 대기 상태에 들어갑니다.
  3. 락 보유 쓰레드가 sem_post()를 호출하면 대기 중인 쓰레드가 깨어납니다.

<br>
</details>

<details>
  
<summary>
  <strong>컨디션 변수로의 세마포어와 그 동작 과정에 대해 설명하세요.</strong>
</summary>

<br>

  ### 컨디션 변수로의 세마포어
  세마포어는 특정 조건이 만족될 때까지 스레드를 대기시키는 컨디션 변수처럼 사용할 수 있습니다.

  ```c
  // 예시: 부모 스레드가 자식 스레드의 종료를 기다리는 경우우
  sem_t s;

  void* child(void *arg) {
    printf("child\n");
    sem_post(&s);  // 부모에게 신호 전달
    return NULL;
  }
  
  int main() {
    sem_init(&s, 0, 0);  // 초기값 0
    printf("parent: begin\n");
    pthread_t c;
    pthread_create(&c, NULL, child, NULL);
    sem_wait(&s);        // 자식이 신호를 줄 때까지 대기
    printf("parent: end\n");
    return 0;
  }
  ```

  1. 부모 쓰레드는 sem_wait()를 호출하여 대기 상태로 들어갑니다.
  2. 자식 쓰레드는 작업을 완료한 뒤 sem_post()를 호출해 부모를 깨웁니다.
  3. 부모는 대기 상태에서 깨어나 이후 작업을 이어갑니다.
  
<br>
</details>

<details>
  
<summary>
  <strong>생산자/소비자(유한 버퍼) 문제를 해결하는 방식을 설명하세요.</strong>
</summary>

<br>

  ### 생산자/소비자(유한 버퍼) 문제 해결
  생산자가 버퍼에 데이터를 채우고, 
  소비자가 버퍼에서 데이터를 꺼내는 문제에서 세마포어를 사용하여 버퍼에 대한 접근을 제어하고, 
  생산자와 소비자 간의 동기화를 이룰 수 있습니다.
  
  ```c
  sem_t empty;
  sem_t full;
  sem_t mutex;
  
  void *producer(void *arg) {
      for (int i = 0; i < loops; i++) {
          sem_wait(&empty);      // 버퍼 공간 확보
          sem_wait(&mutex);      // 임계 영역 진입
          put(i);                // 데이터 추가
          sem_post(&mutex);      // 임계 영역 해제
          sem_post(&full);       // 데이터 추가 알림
      }
  }
  
  void *consumer(void *arg) {
      for (int i = 0; i < loops; i++) {
          sem_wait(&full);       // 데이터 확인
          sem_wait(&mutex);      // 임계 영역 진입
          int tmp = get();       // 데이터 소비
          sem_post(&mutex);      // 임계 영역 해제
          sem_post(&empty);      // 공간 추가 알림
          printf("%d\n", tmp);
      }
  }
  ```

  1. 임계 영역 보호를 위한 mutex 세마포어: 
  put()과 get() 함수의 호출이 여러 스레드에서 동시에 실행되지 않도록 보호하여 경쟁 조건을 방지합니다.
  2. 락 순서 유지: 
  empty/full 세마포어를 먼저 기다린 후, mutex를 사용하는 방식으로 교착 상태를 방지합니다.
  3. 락 범위 최소화: 
  임계 영역의 범위를 최소화하여 동시성 수준을 높이고 불필요한 락 점유를 방지합니다.

<br>
</details>
