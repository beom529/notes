
@startuml TokenPassStateDiagram
[*] --> WaitingForToken

WaitingForToken --> HasToken : Receive Token
HasToken --> SendingToken : Send Token to Successor
SendingToken --> WaitingForToken : Token Sent
HasToken --> WaitingForToken : Pass Token after Delay
@enduml

