- A group of army generals who lead different parts of the Byzantine army are planning to attack or retreat from a city
- The only way of communication is via a messenger
- They need to agree to strike at the same time in order to win
- The issue is that one or more generals might be traitors who could send a misleading message
- Therefore, there is a need for a viable mechanism that allows for agreement among generals so that the attack can still take place at the same time
---
- As an analogy to distributed systems, the generals can be considered as nodes, the traitors as Byzantine (malicious) modes, and the messenger can be thought as a channel of communication
---
- In RAFT and Paxos algorithm, which heavily relies on that, the faulty nodes never send any vote and the non-faulty nodes send a correct vote
- In Byzantine fault, it may happen that the faulty node selectively sends votes to some of the nodes
- The problem was solved by Practical Byzantine Fault Tolerance (PBFT) algorithm, where consensus is reached after a certain number of messages are received containing the same signed content

## Three Byzantine Generals Problem: Faulty Lieutenant

![[three-byzantine-problem-faulty-lieutenant.svg]]

- This is the case when one of the Lieutenant is faulty
- Commander sends a retreat message to both the Lieutenant(1,2)
- Lieutenant(2), who is faulty, sends an attack message rather than an actual retreat message to Lieutenant(1)
- But, in general, by integrity condition of the Army, the Lieutenant(1) is bound to obey the Commander message
- Although, Lieutenant(2) is faulty and the Commander is correct
- Thus the entire system will work correctly

## Three Byzantine Generals Problem: Faulty Commander

![[three-byzantine-problem-faulty-commander.svg]]

- This is the case when the commander is faulty
- The Commander sends different messages to different Lieutenants
- He sends a retreat message to Lieutenant(1) and an attack message to Lieutenant(2)
- When Lieutenants exchange the messages, then both may feel that the other one is faulty
- Then, they follow the integrity of the Army and both obey the Commander's message
- Thus, this contradicts the agreement condition and no solution for three generals, including one faulty commander
- Even the majority principle won't work here because both the Lieutenants had received two messages { attack, retreat } which may confuse both the Lieutenants

## Four Byzantine Generals Problem: Faulty Lieutenant

![[four-byzantine-problem-faulty-lieutenant.svg]]

- In this case, there are four Byzantine Generals, and one of the Lieutenant is faulty
- They communicate with each other using the message passing technique
- The Commander sends a message to all the Lieutenant and the Lieutenant share the received message
- However, Lieutenant(2), who is faulty, sends the incorrect message to others, whereas the remaining Lieutenants share the correct message
---
- If they go for the majority voting principle,  they can analyze and decide to retreat
- Lieutenant (1) = { Retreat, Attack, Retreat } = Retreat
- Lieutenant (3) = { Retreat, Retreat, Attack } = Retreat
---
- Following the majority voting principle, Lieutenant (1) and Lieutenant (3) can correctly decode the message, although Lieutenant (2) is Byzantine node
- However, the same concept is not valid if two Lieutenants become faulty

## Four Byzantine Generals Problem: Faulty Commander

![[four-byzantine-problem-faulty-commander.svg]]

- In this case, there are four Byzantine generals, out of which three are non-faulty Lieutenants and a faulty Commander
- They communicate with each other using the message passing technique
- The Commander send the retreat message to two Lieutenants (1,3) and an attack message to Lieutenant (2)
- The Lieutenants exchange messages correctly
---
- Using majority voting principle, the can analyze and decode to Retreat
- Lieutenant (1) = { Retreat, Attack, Retreat } = Retreat
- Lieutenant (2) = { Attack, Retreat, Retreat } = Retreat
- Lieutenant (3) = { Retreat, Retreat, Attack } = Retreat
---
- Following the majority voting principle, Lieutenant (1,2,3) can correctly decode the message, although Commander is Byzantine node
- However, if the Commander sends an attack message to more than one Lieutenant and then using the majority voting, they can analyze and decode to attack
- When the Commander is faulty, the system will reach a consensus with the value that the Commander has proposed to the majority of the Lieutenants
---
- In general, to ensure the correct consensus in the system, there should be 
	- maximum of F number of faulty Lieutenants and
	- 2\*F +1 number of Lieutenants plus a Commander

# Byzantine Generals Model

- In this model, we assume an N number of processes out of which 
	- at most F number of processes can be faulty and
	- the system has total of 2\*F + 1 number of processes
- The system should be 
	- fully connected
	- receivers always know the identity of the sender
	- synchronous
	- have reliable communication medium
- Synchronous system means that every process should receive all the messages within some predefined timeout duration