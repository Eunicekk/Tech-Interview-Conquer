<details>
  <summary><strong>슬라이딩 윈도우 기반 ARQ에 대해서 설명하고, 그 종류에는 어떤 것이 있나요?</strong></summary>

<br>

  슬라이딩 윈도우(Sliding Window) 기법은 **일정 크기의 윈도우 내에서 여러 패킷을 연속적으로 전송**하는 방법이고, ARQ(Automatic Repeat reQuest)는 **패킷이 손실되거나 오류 발생 시 자동으로 재전송을 요청**하는 방식입니다.  
  슬라이딩 윈도우 기반 ARQ에는 대표적으로 **GBN**(Go-Back-N)과 **SR**(Selective Repeat) 프로토콜이 있습니다.  
  
</details>

<details>
  <summary><strong>윈도우 크기로 확인 응답(ACK)이 되지 않은 패킷의 수를 제한하는 이유는 어떤 것이 있나요?</strong></summary>

<br>

1. **순서 번호 공간과 혼동 방지**    
- 패킷에 순서 번호를 부여하는데(3비트면 0~7) 순서 비트는 순환하기에(8이면 0으로 돌아옴) 윈도우 크기가 너무 크면 이전 패킷과 새 패킷을 구별하기 어려움
- 일반적으로 윈도우 크기는 순서 번호 공간의 절반으로 제한
2. **데이터 흐름 제어 및 네트워크 자원 최적화**
- 확인 응답이 오지 않은 패킷이 많아질수록 데이터 재전송 횟수가 증가하고 네트워크 혼잡이 발생
  
</details>

<details>
  <summary><strong>GBN 프로토콜에 대해서 설명해 주세요</strong></summary>

<br>

 GBN(Go-Back-N) 프로토콜은 윈도우 크기만큼 패킷을 연속으로 전송하고 특정 패킷 손상, 타임아웃 등 오류가 발생한 경우 **해당 패킷 이후 전송된 모든 패킷을 재전송**하는 프로토콜입니다

 ex)  
패킷 : 0 1 2 3 4 5 6 7 8 9  
윈도우 : 3

- 패킷 전송 성공
 1. 0 -> 1 -> 2 순서로 전송
 2. 0 수신 성공 -> 3 전송 -> 1 수신 성공 -> 4 전송 -> 2 수신 성공 -> 5 전송

- 패킷 전송 실패
 1. 3 수신 성공 -> 6 전송 -> 4 수신 실패 -> 5 수신 성공 -> 6 수신 성공
 2. 4 수신 타임아웃 -> 4부터 다시 전송(5와6은 수신에 성공했지만 다시 전송)
</details>

<details>
  <summary><strong>SR 프로토콜에 대해서 설명해 주세요</strong></summary>

<br>

 SR(Selective Repeat) 프로토콜은 윈도우 크기만큼 패킷을 연속으로 전송하고 특정 패킷 손상, 타임아웃 등 오류가 발생한 경우 **해당 패킷만 재전송하고 수신 받은 패킷은 버퍼에 저장 후 재조립**하는 프로토콜입니다

 ex)  
패킷 : 0 1 2 3 4 5 6 7 8 9  
윈도우 : 3

- 패킷 전송 성공
 1. 0 -> 1 -> 2 순서로 전송
 2. 0 수신 성공 -> 3 전송 -> 1 수신 성공 -> 4 전송 -> 2 수신 성공 -> 5 전송

- 패킷 전송 실패
 1. 3 수신 성공 -> 6 전송 -> 4 수신 실패 -> 5 수신 성공(버퍼에 저장) -> 6 수신 성공(버퍼에 저장) 
 2. 4 수신 타임아웃 -> 4 재전송 -> 4 수신 완료 -> 버퍼에 저장된 5, 6 정렬 후 전달
</details>

<details>
  <summary><strong>GBN과 SR 프로토콜의 장단점을 비교해서 설명해 주세요</strong></summary>

<br>

GBN은 **구현이 단순하고 관리가 쉽지만** 재전송 범위가 넓어 **대역폭 낭비**가 심해질 수 있습니다.  
SR은 오류 발생한 패킷만 재전송하기에 **대역폭 사용 효율이 좋지만** **구현(버퍼링, 순서 정렬 처리 등)이 복잡**합니다.
</details>
