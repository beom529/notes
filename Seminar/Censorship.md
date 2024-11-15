## DPI
1. Packet Characteristics
2. Geader fingerprints
3. Content fingerprints
4. reaction to probes
5. reaction to perturbations


### 첫번째 Parrot System
다른 프로토콜을 흉내냄 Tor를 Skype 처럼 흉내낸다
#### 작동안됨
Sensor가 프로토콜의 다른 점만 알면 무효화 됨

### 두번째 Tunnel : Piggyback
다른 프로토콜에 언혀저 감
Tor -> Audio Signal 
Modulation해서 음성 신호로 변환한다
Legal/Practical constraints 음성으로 하면 잘못된다

### 새번째 Man has no name
우리가 Nothing처럼 보이면 어떨까?
현재의 Tool은? Signature와 Fingerprint를 못하게 한다

## FE Proxy
Fully Encrypted Proxies

패킷을 전부 Encryption한다
HELO 패킷
L4 위 모든건 Encrypt 된다

1. 2021/11/6 : Dynamic Blocking Started
	1. 갑자기 검열이 중단됨
2. 2021/11/16 : 새 검열 시작
3. 2021/11/18 : 중국 최고위원장 선출
4. 2021/01/04 : 뚫는 프로토콜 만듬

황금방패
1. Measurement 기반
	1. qmfforqkr 블랙박스 Blackbox
2. 트래픽을 보내서 중국에서 어떻게 처리하는지 관찰함

전부 완전히 암호화됨
아무것도 아닌거 같으면 = 막기로 함
1. Fraction of Zeros 패킷의 0이 42.5퍼 미만, 57.5퍼 이상이면 허용
2. 시작이 6바이트가 아스키면  허용
3. 반이상의 바이트가 ASCII 면 허용
4. 20
5. HTTP

Probabilistic 기반 approach
1. 25% 정도만 막는다

AS 기반 IP 필터


ㅁㄴ
