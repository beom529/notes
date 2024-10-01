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
