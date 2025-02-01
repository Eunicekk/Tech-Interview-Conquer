## tcp 혼잡 제어

<details>
  
<summary>
  <strong>TCP에서 혼잡 제어와 흐름 제어의 차이점은 무엇인가요?</strong>
</summary>

<br>

혼잡 제어(Congestion Control):
네트워크 자체의 혼잡 상태를 방지하기 위해 사용됩니다. 네트워크 경로의 라우터나 스위치의 버퍼가 가득 차서 패킷 손실이 발생하는 상황을 방지하려고 합니다.
  
  - 주요 변수: cwnd (congestion window)
  - 동작 방식: 패킷 손실이나 ACK 지연을 통해 네트워크 혼잡을 감지하고, 송신 속도를 조절합니다.
  - 대표 알고리즘: Slow Start, Congestion Avoidance, Fast Recovery

<br>

흐름 제어(Flow Control):
송신자가 수신자보다 너무 빠르게 데이터를 보내는 것을 방지하기 위해 사용됩니다. 즉, 수신자의 버퍼가 넘치는 상황을 막기 위한 메커니즘입니다.
  
  - 주요 변수: rwnd (receiver window)
  - 동작 방식: 수신자가 자신의 처리 가능 데이터를 rwnd로 알려주면, 송신자는 이를 초과하지 않도록 전송량을 제한합니다.

<br>
</details>
<br>
<details>
  
<summary>
  <strong>TCP의 AIMD 기법은 무엇이며, 왜 사용하나요?</strong>
</summary>

<br>

AIMD(Additive Increase, Multiplicative Decrease) 는 TCP의 핵심 혼잡 제어 전략으로, 전송 속도를 조절하는 방식입니다.
  
  - Additive Increase(선형 증가):
    - 혼잡이 감지되지 않을 경우, TCP는 전송 윈도우(cwnd)를 선형적으로 증가시킵니다. 일반적으로 매 RTT마다 1 MSS씩 증가하여, 네트워크의 여유 대역폭을 탐색합니다.
    - → “안정적인 환경에서는 천천히 속도를 높여본다”
<br>

- Multiplicative Decrease(배수 감소):
  - 혼잡(패킷 손실)이 감지되면, TCP는 즉시 cwnd를 절반으로 감소시킵니다. 이는 네트워크가 과부하 상태임을 의미하므로, 빠르게 전송률을 줄여 혼잡을 완화합니다.
  - → “혼잡이 발생하면 빠르게 속도를 줄인다”
  
  - AIMD를 사용하는 이유:
    - 안정성(Stable): 혼잡이 발생한 경우 전송 속도를 급격히 줄여 네트워크가 붕괴되는 것을 방지
    - 효율성(Efficient): 대역폭을 충분히 활용하기 위해 점진적으로 속도를 증가
    - 공정성(Fairness): 여러 TCP 연결이 병목 구간을 공유할 때, 각 연결이 공정하게 대역폭을 사용할 수 있도록 함
<br>

- AIMD의 시각적 특징:
  - 이 전략은 톱니 모양(Sawtooth) 의 혼잡 윈도우 그래프를 만들어, 지속적으로 대역폭을 탐색(probing)하는 모습으로 나타납니다.

<br>
</details>

