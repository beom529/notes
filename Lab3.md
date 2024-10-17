
몇가지를 수정해서 다시 코드를 써줘 대답은 한글로 해줘. 
1. 하트비트 실행과 중단 시기를 결정해야되
	1. 내 생각은 UDP하트비트는 MEMBERSHIP 이 Settle 됬을때만 보내고 Changing 일때는 좀 다르게 처리해야할것 같아
	2. 그러니까 Heartbeat가 NewView기 끝나면 보내기 시작해야되
	3. 근데 궁금한게 NewView가 끝났을때 전 뷰 아이디로 온 Heartbeat는 어떻게 해야될까? 이걸 카운트 할지 말지 모르겠어
2. 그리고 하트비트 페이로드는 다음과 같이 쓰고 싶어
	1. type HeartbeatMessage struct {  
    srcID  int  
    destID int  
}
		2. 페이로드에 뷰 아이디를 추가하는게 나을까?
1. 그리고 RESPONSE_PENDING이 왜 필요한지 모르겠어 
2. 그리고 각 뷰 아이디 별로 하트비트를 관리하는게 좋을까 싶어. 근데 그렇게 되면 하트비트를 어떤 데이터 구조에서 관리하는게 나을까? type RequestState struct {  
    SrcID  int  
    DestID int  
    REQ    bool  
    OK     bool  
}  
type ViewState struct {  
    Requests map[int]*RequestState  
    ViewID   int  
}  
  
var viewStates = make(map[int]*ViewState) 를 수정할까 아니면 type Peer struct {  
    PeerID               int        // PeerID - row number    IP                   string     // IP address    TCPCommunicationPort int        // Port Number  
    UDPHeartbeatPort     int        // Port Number  
    Hostname             string     // Hostname  
    IsLeader             bool       // is Leader?  
    IsSelf               bool       // is Self?  
    ViewID               int        //Current View ID  
    LeaderID             int        //Current Leader ID  
    MemberList           []int      //Membership List  
    PendingOperations    []Message  //Pending Jobs  
    Mutex                sync.Mutex //Mutex  
    HeartbeatReceived    time.Time  //Received Time  
} 에 추가할까?

크래쉬 담당부분
    -c delay
      This delay is a sleep that should start immediately after sending an JOIN
      message. When the sleep ends, the peer should crash (exit). 을 메인함수에서 다르게 처리하게 바꿔야 될것같애