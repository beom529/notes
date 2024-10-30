- [ ] Quorum 공식
	Quorum >= (n/2)+1
- [ ] Persistence
	- [ ] The **given docker file does not have volume or file mapping**. 
	- [ ] Proposer: "Proposers must persist maxRound on disk: must not reuse proposal numbers after crash/restart." - Should I have to do this?
	- [ ] Acceptor: "Acceptors must record minProposal, acceptedProposal, and acceptedValue on stable storage (disk)." - Should I have to do this?
- [ ] Proposal Value Format
	- [ ] To generate a new proposal number: Increment maxRound Concatenate with Server Id
		- [ ] Round Number : Hostfile's Number
		- [ ] Server ID : Peer ID
		- [ ] String (RoundNumber.ServerID) = Is this correct?
			```"proposal_num":1.1```
- [ ] Proposer 
	- [ ] Prepare Message **Recipient**
		- [ ] To ALL: Includes non-acceptors? or Acceptors with same integer in the host file?
		- [ ] To Myself? - Am I counting in the quorum?
	 - [ ] Prepare Message **Print**
			1. Proposer (Message Value is Empty)
				```{"peer_id":1, "action": "sent", "message_type":"prepare","message_value":"", "proposal_num":1.1}```
			2. Acceptor (If there's no chosen proposal yet) = (Message Value/Proposal Number)
				1. ```peer1  | {"peer_id":2, "action": "received", "message_type":"prepare_ack","message_value":"", "proposal_num":0.0}```
	- [ ] Prepare message Quorum handling.
		- [ ] Quorum is calculated by $$Total Hosts Sent PrepareACKmessage/Total hosts in the hostsfile$$
- [ ] Payload
	- [ ] Gob to handle byte data NOT string
		- [ ] Can Proposal Value can be a string?
- [ ] Learner
	- [ ] No instructions about "Learner" - Should I have to include a learner handling? 