<details>
  <summary><strong>멀티프로세서 스케줄링에 대해 설명하세요.</strong></summary>

  ### 멀티프로세서 스케줄링(Multiprocessor Scheduling)
  멀티프로세서 스케줄링은 여러 개의 CPU가 존재하는 시스템에서 작업들을 어떻게 효율적으로 할당하고 실행 순서를 정할 것인가를 다루는 개념입니다.
  멀티코어 시대에는 단순히 CPU 수를 늘리는 것만으로 성능 향상이 어렵기 때문에, 효율적 스케줄링을 통해 처리량, 응답 시간, 공정성 등 다양한 성능 목표를 달성하는 것이 중요합니다.

</details>
<br>
<details>
  <summary><strong>단일 큐 스케줄링(SQMS)과 멀티 큐 스케줄링(MQMS)의 차이는 무엇인가요?</strong></summary>

  ### 단일 큐 스케줄링(SQMS)
  하나의 공용 큐를 두고 모든 CPU가 이 큐에서 작업을 가져가는 방식입니다.
  구현이 간단하지만, 락 경쟁 증가, 캐시 친화성 저하, 확장성 한계 등의 문제가 발생할 수 있습니다.
  
  ### 멀티 큐 스케줄링(MQMS)
  CPU별로 큐를 하나씩 두어 확장성과 캐시 친화성을 개선합니다.
  그러나 워크로드 불균형 문제가 생길 수 있으며, 이를 해결하기 위해 CPU 간 작업 이주(migration)가 필요합니다.

</details>

<br>
<details>
  <summary><strong>멀티프로세서 시스템에서 캐시 친화성(Cache Affinity) 문제는 왜 중요한가요?</strong></summary>

  캐시에 이미 적재된 데이터를 재활용할 수 있으므로, 가능한 한 프로세스를 이전에 실행되었던 동일한 CPU에서 계속 실행하면 성능을 개선할 수 있습니다.
  프로세스가 자주 다른 CPU로 옮겨 다니면 매번 캐시를 재구축해야 하므로 성능 저하가 발생합니다. 따라서 스케줄러는 불필요한 CPU 이동을 줄여 캐시 친화성을 유지하려고 합니다.

</details>

<br>
<details>
  <summary><strong>멀티 큐 스케줄링(MQMS)에서 발생하는 워크로드 불균형 문제를 어떻게 해결할 수 있나요?</strong></summary>

  MQMS에서 각 CPU는 별도의 큐를 가지므로 특정 CPU에만 작업이 몰릴 수 있습니다.
  이를 해결하기 위해 작업 이주(migration)를 사용합니다.
  한 CPU에 과부하가 걸리면 다른 CPU 큐로 작업 일부를 옮겨
  전체 시스템의 처리량과 균형을 개선할 수 있습니다.

</details>

<br>
<details>
  <summary><strong>멀티프로세서 스케줄러에서 사용되는 대표적인 성능 지표는 무엇인가요?</strong></summary>

  ### 성능 지표
  처리량(throughput), 응답 시간(response time), 반환 시간(turnaround time), 공정성(fairness),
  CPU 활용도(CPU utilization), 확장성(scalability) 등이 있습니다.
  어떤 지표를 중시하는지에 따라 스케줄링 알고리즘 선택이 달라집니다.

</details>

<br>
<details>
  <summary><strong>멀티프로세서 스케줄링에서 락(lock) 경쟁은 왜 발생하며 어떤 영향이 있나요?</strong></summary>

  단일 큐 방식에서 여러 CPU가 동시에 하나의 큐에 접근하려 할 경우 해당 큐를 보호하기 위한 락 획득 시 경쟁이 발생합니다.
  이는 스케줄러 동작에 드는 오버헤드를 증가시키고 확장성을 저하시켜 전체 성능을 떨어뜨릴 수 있습니다.

</details>

<br>
<details>
  <summary><strong>작업 이주(migration) 빈도를 조정할 때 고려해야 할 트레이드오프는 무엇인가요?</strong></summary>

  이주를 자주 하면 워크로드를 신속히 균형화할 수 있지만 캐시 재구축 및 이주 오버헤드가 증가합니다.
  반면, 이주를 적게 하면 캐시 친화성은 유지되나 불균형 상황이 오래 지속될 수 있습니다.

</details>
