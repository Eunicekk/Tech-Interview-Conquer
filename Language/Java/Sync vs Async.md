
<details>
  <summary><strong>동기(Synchronous)와 비동기(Asynchronous)의 차이점은 무엇인가요?</strong></summary>

  동기는 요청 후 결과가 올 때까지 기다리는 방식이고, 비동기는 요청 후 결과를 기다리지 않고 다음 작업을 진행하는 방식입니다.  
  동기는 코드가 순차적으로 실행되어 이해가 쉽지만, 대기 시간이 긴 작업에서 비효율적입니다.  
  비동기는 자원을 효율적으로 활용할 수 있지만, 복잡한 콜백 처리나 동시성 문제를 고려해야 합니다.
</details>

<details>
  <summary><strong>자바에서 동기와 비동기를 구현하는 방법은 무엇인가요?</strong></summary>

  동기는 synchronized 키워드를 사용하거나, 메소드가 순차적으로 실행되도록 블로킹 호출로 구현합니다.  
  비동기는 CompletableFuture, ExecutorService, 또는 외부 라이브러리(예: RxJava)를 사용해 비동기 작업을 수행하며, 콜백 함수나 thenApply 같은 체이닝 메서드를 통해 결과를 처리합니다.
</details>

<details>
  <summary><strong>자바에서 비동기 처리가 유리한 상황은 언제인가요?</strong></summary>

  비동기 처리는 대기 시간이 긴 작업(예: 네트워크 요청, 파일 입출력)에서 효율적입니다. CPU 작업을 블로킹하지 않아 자원을 최적화할 수 있으며, 고성능 서버 애플리케이션이나 병렬 작업 처리에 적합합니다. 하지만 동시성 문제와 에러 처리를 신중히 다뤄야 합니다.
</details>