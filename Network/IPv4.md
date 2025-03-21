<details>
  
<summary>
  <strong>IPv4 헤더의 구조와 주요 필드에 대해 설명해 주세요.</strong>
</summary>

<br>

## IPv4 데이터 포맷

IPv4 데이터 포맷은 **헤더(Header)**와 **데이터(Payload)**로 구성됩니다. IPv4 헤더는 송신지에서 목적지로 데이터를 정확히 전달하기 위해 필요한 제어 정보를 포함하며, 총 20바이트의 고정 길이와 옵션 필드를 포함한 가변 길이로 이루어질 수 있습니다.

### IPv4 데이터 포맷의 구조
- Header (20~60바이트): 제어 정보를 포함.
- Payload (데이터): 전송할 실제 데이터.

## IPv4의 주요필드

- Version (4비트): 인터넷 프로토콜의 버전을 지정하며, IPv4에서는 항상 4로 설정됩니다.
- IHL (Internet Header Length, 4비트): IPv4 헤더의 길이를 4바이트 단위로 나타냅니다. 기본적으로 20바이트이며, 옵션 필드가 추가될 경우 길이가 증가합니다.
- Type of Service (ToS, 8비트): QoS를 지원하기 위한 필드로, 데이터그램의 우선순위와 처리 방식을 지정합니다.
- Total Length (16비트): IPv4 데이터그램의 전체 길이(헤더 + 데이터)를 바이트 단위로 나타냅니다. 최대 값은 65,535바이트입니다.
- Identification (16비트): 데이터그램을 고유하게 식별하며, 패킷이 분할(Fragmentation)될 경우 재조립을 위해 사용됩니다.
- Flags (3비트): 패킷 분할 관련 정보를 지정합니다.
- Fragment Offset (13비트): 분할된 패킷의 원래 데이터그램 내 위치를 나타냅니다.
- Time To Live (TTL, 8비트): 데이터그램이 네트워크를 통과할 수 있는 최대 홉(hop) 수를 지정합니다. TTL 값이 0이 되면 패킷은 폐기됩니다.
- Protocol (8비트): 상위 계층 프로토콜(TCP, UDP, ICMP 등)을 지정합니다.
- Header Checksum (16비트): IPv4 헤더의 오류를 검출하기 위해 사용됩니다. 수신 측에서 재계산하여 값이 일치하지 않으면 데이터그램이 폐기됩니다.
- Source Address (32비트): 데이터그램의 송신지 IP 주소.
- Destination Address (32비트): 데이터그램의 목적지 IP 주소.
- Options (가변 길이): 추가적인 제어 정보를 포함할 수 있는 필드로, 보안, 라우팅, 타임스탬프 등을 설정할 수 있습니다.

<br>
</details>
