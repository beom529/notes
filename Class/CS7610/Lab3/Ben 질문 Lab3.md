- [ ] Quorum 공식
	Quorum >= (n/2)+1
		Floor / Ceiling?

- [ ] 
- [ ] Proposer
	- [ ] time.Sleep(1 * time.Second) // Delay 넣어도 되?
- [ ] Proposal Value Format
	- [ ] To generate a new proposal number: Increment maxRound Concatenate with Server Id
		- [ ] Round Number: Hostfile's Number
			- [ ] Case 1
				peer1:proposer1
				peer2:acceptor1
				peer3:acceptor1
				peer4:acceptor1
				peer5:learner1
			- [ ] Case 2
				peer1:proposer1  
				peer2:acceptor1,acceptor2  
				peer3:acceptor1,acceptor2  
				peer4:acceptor1,acceptor2  
				peer5:proposer2
		- [ ] Server ID: Peer ID
		- [ ] String (RoundNumber.ServerID) = Is this correct?
			```"proposal_num":1.1```
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