# Consensus Mechanism

- backbone of blockchain
- provides decentralization of control
- choice of consensus algorithm is based on the type of blockchain used
- not all consensus mechanisms are suitable for all types of blockchain
- for e.g. in public permissionless blockchain, it would make sense to use Proof-of-Work instead of Proof-of-Authority
- it is essential to choose an appropriate consensus algorithm for a particular blockchain
---
- Consensus is a process of agreement between distributing nodes on the final state of data
- To achieve consensus, different algorithms are used
- It is easy to reach agreement between two nodes but difficult when multiple nodes are participating in a distributed system
- The process of attaining agreement common state or value among multiple nodes despite the failure of some nodes is known as **Distributed consensus**
---
- It is a set of steps taken by most or all nodes in a blockchain to agree on a proposed state or value
- There are various requirements that must be met to provide the desired results in a consensus mechanism
- The following describes these requirements :
	- **Agreement** : All honest nodes on the same value
	- **Termination** : All honest nodes terminate execution of the consensus process and eventually reach a decision
	- **Validity** : The value agreed upon by all honest nodes must be the same as the initial value proposed by at least on honest node
	- **Fault tolerant** : The consensus algorithm should be able to run in the presence of faulty or malicious nodes (Byzantine nodes)
	- **Integrity** : No node can make the decision more than once in a single consensus cycle

## Types of Consensus mechanisms

- All consensus mechanisms are developed
	- to deal with faults in a distributed system and 
	- to allow distributed systems to reach a final state agreement
- There are two general categories of consensus mechanisms
	1. Traditional Byzantine Fault Tolerance (BFT)-based
		- This method relies on a simple scheme of nodes
		- Based on round of votes
		- When certain number of messages are received, then an agreement is reached
		- Also known as *consortium* or *permissioned* type
		- This performs well in limited number of nodes, but they do not scale well
	2. Leader election-based
		- This method requires nodes to compete in a leader-election lottery
		- A leader is elected and proposes a final value
		- Also known as *fully decentralized* or *permissionless* type
		- For example, the PoW used in Bitcoin and Ethereum
		- This scales very well but perform very slowly
---
- Practical Implementation of consensus protocols
1. Paxos
	- Most famous protocol
	- Nodes are assigned various roles such as
		- Proposer
		- Acceptor
		- Learner
	- Nodes or processes are named replicas
	- Consensus is achieved in the presence of faulty nodes by agreement among a majority of nodes
1. RAFT
	- Works by assigning any of three states
		- Follower
		- Candidate
		- Leader
	- Leader is elected after a candidate node receives enough votes
	- All the changes have to go through the leader
	- Leader commits the proposed changes once replication on the authority of the follower nodes in completed

## List of Consensus Algorithms

1. **Proof of Work (PoW)**
	- It relies on proof that adequate computational resources have been spent before proposing a value for acceptance by the network
	- It is used in Bitcoin, Litecoin and other cryptocurrency blockchains
	- It is only algorithm that has proven to be  successful against any collusion attacks on blockchain network
2. **Proof of Stake (PoS)**
	- It works on the idea that a node has an adequate stake in the system
	- i.e. the user has invested enough in the system so that any malicious attempt by that user would outweigh the benefits if performing such as attack on the network
	- *Coin Age* is a criterion derived from the amount of time and number of coins that have not been spent 
	- The chances of proposing and signing the next block increase with the coin age
3. **Delegated Proof of Stake (DPoS)**
	- This is an innovation over standard PoS
	- Each node that has a stake in the system can authorize the validation of transaction to other nodes by voting
4. **Proof of Elapsed Time (PoET)**
	- It uses a *Trusted Execution Environment (TEE)* to provide randomness and safety in the leader election process via a guaranteed wait time
	- It requires Intel *Software Guard Extensions (SGX)* processor to provide the security guarantee for it to be secure
5. **Proof of Deposit (PoD)**
	- Nodes that wish to participate in the network have to make a security deposit before they can mine and propose blocks
6. **Proof of Importance (PoI)**
	- In order to establish trust and importance, it relies on
		- how large a stake a user has in the system and
		- it also monitors the usage and movement of tokens by the user 
7. **PBFT**
	- It achieves state machine replication
	- It provides tolerance against Byzantine nodes
8. **Proof of Activity (PoA)**
	- In this method, PoW and PoS are combined together to achieve consensus and good level of security
	- It is more energy-efficient mechanism as compared to PoW
	- It uses PoW in the first stage of mechanism and switches to PoS which consumes negligible energy
9. **Proof of Capacity (PoC)**
	- It uses hard disk space as a resource to mine the blocks
	- This is different from PoW, where CPU resources are used
	- In PoC, hard disk space is utilized for mining and known as *hard drive mining*
10. **Proof of Storage (PoS)**
	- It is based the concept that a particular piece of data is probably stored by a node which serves as a means to participate in the consensus mechanism