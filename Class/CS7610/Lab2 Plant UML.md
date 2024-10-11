
@startuml
[*] --> Waiting : Start / Receive Passtoken

Waiting --> Processing : Process Passtoken
Processing --> Sending : Forward Passtoken
Sending --> Waiting : Wait for Passtoken

[*] --> Sending : Initiate Passtoken (Initiator)

@enduml



as
