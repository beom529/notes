
1. 프로그램시작하고 멤버십 리스트에 누가 있어야되?
2. Once program starts. is it 0 or 1
3. First JOIN message? How to deal with? I am the only one
```
Message (Payload) Structtype Message struct {  
    MessageType MessageType //Enum  
    Operation   Operation  
    SrcID       int //Destination Peer  
    DestID      int  
    RequestID   int  
    ViewID      int //Monotonically Increasing  
    LeaderID    int  
    MemberList  []int //List includes members  
}
```
1. Client 가 JOIN 보낸다
```
MessageType
SrcID
DestID
```
2. JOIN 이 Leader한테 가면 Leader가 REQ를 모든 클라이언트에 보낸다
```
    MessageType  
    Operation
    SrcID
    DestID
    RequestID
    ViewID      
    LeaderID  
	NewPeerID 
```
4. 각 Peer는 OK를 대답한다
```
    MessageType
    SrcID
    DestID
    RequestID
    ViewID
```
5. 전부다 돌아오면 끝~
```
    MessageType
    SrcID
    DestID
```