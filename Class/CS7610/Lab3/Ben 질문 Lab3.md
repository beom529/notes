- [ ] Quorum 공식
	Quorum >= (n/2)+1
 - [ ] Prepare Message Print
		1. Proposer
			``` {"peer_id":1, "action": "received", "message_type":"prepare","message_value":"", "proposal_num":1.1}```
		2. Acceptor
			1. ```peer1  | {"peer_id":2, "action": "received", "message_type":"prepare_ack","message_value":"", "proposal_num":0.0}
3. Proposal Value - String 써도 되는지
2. Proposer, 나한테도 보내야되?
3. Proposer가 어디로 보내?
4. Learner처리는 빼도 되?
7.
특정애들한테 보내면 Quorum계산은 전체 기준이야 아니면 Accepter보낸애들 기준이야?