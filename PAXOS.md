Proposers

1) Choose new proposal number n

2) Broadcast Prepare(n) to all servers

4) When responses received from majority:

}If any acceptedValues returned,  replace value with acceptedValue for highest acceptedProposal


5) Broadcast Accept(n, value) to all servers

7) When responses received from majority:

}Any rejections (result > n)?  goto (1)

}Otherwise, value is chosen


Acceptors

3) Respond to Prepare(n):

}If n > minProposal then minProposal = n

}Return(acceptedProposal, acceptedValue)

}

6)Respond to Accept(n, value):

}If n ≥ minProposal then  acceptedProposal = minProposal = n  acceptedValue = value

}Return(minProposal)

Acceptors must record minProposal, acceptedProposal, and acceptedValue on stable storage (disk)



Proposers

1) Choose new proposal number n

2) Broadcast Prepare(n) to all servers

●

4) When responses received from majority:

}If any acceptedValues returned,  replace value with acceptedValue for highest acceptedProposal

}

5) Broadcast Accept(n, value) to all servers

●

●

7) When responses received from majority:

}Any rejections (result > n)?  goto (1)

}Otherwise, value is chosen

1.Quorum 공식
	Quorum >= (n/2)+1
1. Prepare에 비어 있다