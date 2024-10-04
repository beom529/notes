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
		1. Stop Recording
	2. First
		1. Record its state - 기록하고
		2. Mark the channel (Close) - 들어온 큐 막고
			1. NO MORE MESSAGE TO COME
			2. OR) Not gonna be recorded
		3. Send Marker to everyone - 마커 init 한애 빼고 다 보내기
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

```mermaid
stateDiagram-v2
    [*] --> NormalOperation

    NormalOperation --> RecordingState: Initiate Snapshot
    NormalOperation --> RecordingState: Receive First Marker

    RecordingState --> RecordingState: Send Markers on Outgoing Channels
    RecordingState --> RecordingState: Receive Application Message on Recording Channel / Record Message
    RecordingState --> RecordingState: Receive Marker on Recording Channel / Stop Recording on Channel
    RecordingState --> SnapshotComplete: Markers Received on All Incoming Channels

    SnapshotComplete --> NormalOperation: Resume Normal Operation
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


MARKER 주석

```mermaid


`````


```mermaid
flowchart TD
    A[Client Request] --> B[Send REQUEST to Leader]
    B --> C[Leader p0 Broadcasts PRE-PREPARE]
    C --> D[Omission Fault]
    D --> E[PRE-PREPARE Not Received by p3]
    E --> F[p3 Does Not Participate]
    F --> G[p2 Collects PREPARE Messages]
    G --> H[p2 Collects COMMIT Messages]
    H --> I[p2 Sends REPLY to Client]
    I --> J[Omission Fault]
    J --> K[REPLY Not Delivered to Client]
    K --> L[Client Request Incomplete]
```

```mermaid
graph TD
    Controller["Controller"]
    s1["Switch s1"]
    s2["Switch s2"]
    h1["Host h1"]
    h2["Host h2"]
    h3["Host h3"]
    h4["Host h4"]

    Controller -- "P4Runtime API" --> s1
    s1 --> h1
    s1 --> h2
    s1 --> s2
    s2 --> h3
    s2 --> h4
```

```mermaid
graph TD
    subgraph Spine Layer
        Spine1["Spine 스위치 1"]
        Spine2["Spine 스위치 2"]
    end

    subgraph Leaf Layer
        Leaf1["Leaf 스위치 1"]
        Leaf2["Leaf 스위치 2"]
        Leaf3["Leaf 스위치 3"]
        Leaf4["Leaf 스위치 4"]
    end

    subgraph Hosts
        H1["호스트 H1"]
        H2["호스트 H2"]
        H3["호스트 H3"]
        H4["호스트 H4"]
        H5["호스트 H5"]
        H6["호스트 H6"]
        H7["호스트 H7"]
        H8["호스트 H8"]
    end

    %% Spine-Leaf 연결
    Spine1 --- Leaf1
    Spine1 --- Leaf2
    Spine1 --- Leaf3
    Spine1 --- Leaf4

    Spine2 --- Leaf1
    Spine2 --- Leaf2
    Spine2 --- Leaf3
    Spine2 --- Leaf4

    %% Leaf-호스트 연결
    Leaf1 --- H1
    Leaf1 --- H2

    Leaf2 --- H3
    Leaf2 --- H4

    Leaf3 --- H5
    Leaf3 --- H6

    Leaf4 --- H7
    Leaf4 --- H8

    %% 컨트롤러 연결
    Controller["컨트롤러"] --> Spine1
    Controller --> Spine2
    Controller --> Leaf1
    Controller --> Leaf2
    Controller --> Leaf3
    Controller --> Leaf4
```




```mermaid
sequenceDiagram 
    participant Client
    participant p0
    participant p2
    participant p3

    Client->>p0: REQUEST (r1)
    p0-->>p2: PRE-PREPARE (n=0)
    p0-->>p3: PRE-PREPARE (n=1) (Faulty)
    p2-->>p0: PREPARE (n=0)
    p3-->>p0: PREPARE (n=1)
    p2-->>p0: COMMIT (n=0)
    p3-->>p0: COMMIT (n=1)
    p0-->>Client: REPLY (r1)
    
    Client->>p0: REQUEST (r2)
    p0-->>p2: PRE-PREPARE (n=1)
    p0-->>p3: PRE-PREPARE (n=1)
    p2-->>p0: PREPARE (n=1)
    p3-->>p0: PREPARE (n=1)
    p2-->>p0: COMMIT (n=1)
    p3-->>p0: COMMIT (n=1)
    p0-->>Client: REPLY (r2)
```

