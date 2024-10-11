
@startuml
[*] --> Waiting : Start / Receive Passtoken

Waiting --> Processing : Process Passtoken
Processing --> Sending : Forward Passtoken
Sending --> Waiting : Wait for Passtoken

[*] --> Sending : Initiate Passtoken (Initiator)

@enduml



@startuml
[*] --> Idle

Idle --> InitiateSnapshot : Start Snapshot (Initiator)

InitiateSnapshot --> RecordState : Record Current State
RecordState --> SendMarkers : Send Marker to All Outgoing Channels
SendMarkers --> WaitingForMarkers : Await Markers from Incoming Channels

WaitingForMarkers --> SnapshotComplete : All Markers Received
SnapshotComplete --> Idle : Snapshot Completed

Idle --> MarkerReceivedFirstTime : Receive Marker (Non-Initiator, First Time)
MarkerReceivedFirstTime --> RecordStateSnapshot : Record State
RecordStateSnapshot --> SendMarkers : Send Marker to All Outgoing Channels
@enduml
