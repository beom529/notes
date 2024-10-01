```mermaid
stateDiagram-v2
[*] --> Idle
Idle --> Processing : Token Received
Processing --> Waiting : Marker Sent
Waiting --> Idle : Snapshot Complete
```

```mermaid
stateDiagram-v2
[*] --> Idle
Idle --> Processing :Token Received
Processing --> Waiting : Marker Sent
Waiting --> Idle : Snapshot Complete
```

보내는 입장
1. Snapshot initiated
2. Record its own state
3. Send Marker to each channel (Every processes)
	1. Marker MEssage is NOT a state that the snapshot algorithm is trying to record
	2. Snapshot 찍을때는 아무런 작업하지마라

Receiver
1. Marker Message Arrived
	1. Has seen
	2. First
		1. Record its state
		2. Mark the channel (Close)
			1. NO MORE MESSAGE TO COME
			2. OR) Not gonna be recorded
		3. Send Marker to everyone
		4. $C_ki$ 빼고는 전부 다 record


# Sender
```mermaid
stateDiagram-v2
[*] --> Idle
Idle --> Recording: Snapshot Starts
Recording --> Waiting: Send Marker Messages to all the other processes
Waiting --> Waiting: Receive Messages fro the individual hosts
Waiting --> End: Received messages from every other processes
```
s1 --> s2: A transition
s2 : This is a state description

## Receiver


```mermaid
stateDiagram-v2
    [*] --> Idle: Program IDLE
    Idle --> FirstMarkerReceived: Receiving the first marker from the sender
    FirstMarkerReceived --> RecordingLocalState: Recording the current STATES
    RecordingLocalState --> SendingMarkers: Send Markers to outgoing channels BUT outgoing channel from the first sender
    SendingMarkers --> RecordingChannelStates: 채널 상태 기록 중
    RecordingChannelStates --> WaitingForMoreMarkers: 다른 채널로부터 Marker 수신 대기

    WaitingForMoreMarkers --> MarkerReceivedBefore: 이미 Marker 수신한 채널에서 Marker 수신
    MarkerReceivedBefore --> ClosingChannel: 해당 채널 닫기
    ClosingChannel --> WaitingForMoreMarkers: 다른 채널의 Marker 수신 대기

    WaitingForMoreMarkers --> AllChannelsClosed: 모든 채널에서 Marker 수신 후 종료
    AllChannelsClosed --> SnapshotComplete: 스냅샷 완료

    FirstMarkerReceived --> ClosingInitialChannel: 첫 Marker 수신 시 해당 채널 닫기
    ClosingInitialChannel --> RecordingChannelStates: 다른 채널 기록 시작
```


예를 들어 P1,P2,P3,P4가 있으면

  

1. P1이 스냅샷을 시작한다
2. P1이 상태를 저장한다
3. P1 이 P2,P3,P4에 마커를 보낸다
4. P2,P3,P4는 마커를 받은 채널을 폐쇠한다 (더이상 받지 않음)
	1. 폐쇠된 채널
		1. P1->P2
		2. P1->P3
		3. P1->P4
5. P2,P3,P4는 상태저장을 시작한다 (순간저장이 아니라 지속적으로 저장한다)
6. 각각 다른채널로 마커를 보낸다
	1. P2->P3,P4
	2. P3->P2,P4
	3. P4->P3,P4