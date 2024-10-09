
@startuml
[*] --> Idle

InitiatePasstoken --> SendPasstoken : Generate Passtoken (Initiator)


Idle --> ReceivePasstoken : Receive Passtoken (Non-Init)
ReceivePasstoken --> ProcessPasstoken : Process Passtoken
ProcessPasstoken --> SendPasstoken : Forward Passtoken (To Next)
SendPasstoken --> Idle : Wait for the token
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
