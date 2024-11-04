- [ ] Proposal Value Format
- [ ] Proposer 
	- [ ] Prepare Message **Recipient**
		- [ ] **To ALL**: Includes non-acceptors? or Acceptors with the same integer in the host file? : Send a message. 
		- [ ] To Myself? - Am I counting in the quorum?
	 - [ ] Prepare Message **Print**
			1. Proposer (Message Value is Empty)
				```{"peer_id":1, "action": "sent", "message_type":"prepare","message_value":"", "proposal_num":1.1}```
			2. Acceptor (If there's no chosen proposal yet) = (Message Value/Proposal Number)
				1. ```peer1  | {"peer_id":2, "action": "received", "message_type":"prepare_ack","message_value":"", "proposal_num":0.0}```
	- [ ] Prepare message Quorum handling
		- [ ] Quorum is calculated by $$Total Hosts Sent PrepareACKmessage/Total Hosts In The Hostsfile$$ 2/5 OR  $$Total Hosts Sent PrepareACKmessage/TotalAcceptorHosts $$
	- [ ]텍스트파일전체
	- 

	- [ ] PREPARE_ACK message AFTER quorum is reached
		- [ ] Ignore?
		- [ ] Wait? - Asynchronous
- [ ] Payload
	- [ ] Gob to handle byte data, NOT string.
		- [ ] Can Proposal Value can be a string?
- [ ] Learner
	- [ ] No instructions about "Learner" - Should I have to include a learner handling?  And what?

1. Would the Proposer itself be counted towards the PREPARE quorum?
2. When would Proposer COMMIT accepted value? Is it when sending "ACCEPT" message or after finishing retrieving "ACCEPT_ACK" from the quorum? More specifically, when does the Proposer print the "CHOSE" message?

[ ] Payload
	- [ ] Gob to handle byte data, NOT string.
		- [ ] Can Proposal Value can be a string?
- [ ] Format
	- [ ] {"peer_id":2, "action": "received", "message_type":"accept_ack","message_value":"", "proposal_num":1.5}
	- [ ] {"peer_id":3, "action": "received", "message_type":"prepare_ack","message_value":"", "proposal_num":0.0}



```
```


Learner
```
2024-11-04 16:35:29 {"peer_id":3, "action": "received", "message_type":"accept_ack","message_value":"", "proposal_num":1.1}
2024-11-04 16:35:31 {"peer_id":1, "action": "sent", "message_type":"accept","message_value":"X", "proposal_num":1.1}
2024-11-04 16:35:31 {"peer_id":4, "action": "received", "message_type":"accept_ack","message_value":"", "proposal_num":1.1}
2024-11-04 16:35:33 {"peer_id":1, "action": "sent", "message_type":"accept","message_value":"X", "proposal_num":1.1}
2024-11-04 16:35:35 {"peer_id":1 "action": "chose","message_type":"chose","message_value":"X","proposal_num":1.1}
```
![[Screenshot 2024-11-04 at 4.37.25 PM.png]]

2024-11-04 16:35:33 {"peer_id":1, "action": "received", "message_type":"accept","message_value":"X", "proposal_num":1.1}

Rejection 처리?

끝나면 종료?
Hostfile host2개 이상은?
peer1:proposer1  
peer2:acceptor1,acceptor2  
peer3:acceptor1,acceptor2  
peer4:acceptor1,acceptor2  
peer5:proposer2

멀티롤?
proposer1  
acceptor1,acceptor2  
learner1