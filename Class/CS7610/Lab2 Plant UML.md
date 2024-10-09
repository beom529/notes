
@startuml
[*] --> Idle

Idle --> InitiateToken : If Initiator and No Token
InitiateToken --> EnqueueToken : Create Token and Enqueue to Outgoing Channel
EnqueueToken --> HoldingToken : Token Enqueued

HoldingToken --> SendingToken : After Token Delay

WaitingForToken --> EnqueueToken : Receive Token
SendingToken --> WaitingForToken : Token Sent to Successor
@enduml



@startuml
[*] --> Idle

Idle --> InitiateSnapshot : Start Snapshot (Initiator)

InitiateSnapshot --> RecordState : Record Current State
RecordState --> SendMarkers : Send Marker to All Outgoing Channels
SendMarkers --> WaitingForMarkers : Await Markers from Incoming Channels

WaitingForMarkers --> MarkerReceivedFirstTime : Receive First Marker
MarkerReceivedFirstTime --> RecordStateSnapshot : Record State if Not Initiator
RecordStateSnapshot --> WaitingForMarkers : Continue Waiting for Remaining Markers

WaitingForMarkers --> MarkerReceivedSecondTime : Receive Marker Again
MarkerReceivedSecondTime --> SnapshotComplete : All Markers Received
SnapshotComplete --> Idle : Snapshot Completed

Idle --> MarkerReceivedFirstTime : Receive Marker (Non-Initiator, First Time)
MarkerReceivedFirstTime --> RecordStateSnapshot : Record State
RecordStateSnapshot --> WaitingForMarkers : Continue Waiting

WaitingForMarkers --> MarkerReceivedSecondTime : Receive Marker Again
MarkerReceivedSecondTime --> SnapshotComplete : All Markers Received
@enduml