- The theory states that any distributed system cannot have all three of the much-desired properties simultaneously, i.e. Consistency, availability and partition tolerance

	- **Consistency** is a property which ensures that all nodes in a distributed system have a single, current and identical copy of the data
	
	- **Availability** means that the nodes in the system are up, accessible for use, and are accepting incoming requests and responding with data without any failure as and when required
	
	- **Partition tolerance** ensures that if a group of nodes is unable to communicate with other nodes due to network failure, the distributed system continues to operate correctly

- Consider a distributed systems only with two nodes
	- Consistency is achieved if both nodes have the same shared state; i.e., they have the same up-to-date copy of the data
	- Availability is achieved if both nodes are up and running and responding with latest copy of data
	- Partition tolerance is achieved if communication does not break down between two nodes (due to network issue, byzantine faults, etc.), and they are able to communicate with each other
- Now if a partition occurs and nodes can no longer communicate with each other.
	- If new updated date comes in, it can only be updated on one node
	- If the node accepts the update, then only that one node in the network is updated and therefore consistency is lost
	- Now if the update is rejected by the node, that would result in loss of availability
	- In that case due to partition tolerance, both availability and consistency are unachievable

What actually happens in blockchain
- To achieve fault tolerance (ability of a system to operate when components fails), replication is use
- Consistency is achieved using consensus algorithm
- This is called **state machine replication** which is achieved using blockchain
- There are two types of faults a node can experience
	1. **Fail-Stop fault** 
		- Occurs when a node has crashed
		- These are easier to deal with
		- Paxos protocol is used to deal with this type of fault
	2. **Byzantine fault**
		- Occurs when a faulty node exhibits malicious or inconsistent behavior
		- This can be result of an attack by enemy, a software bug or data corruption
		- PBFT protocol was developed to address this type of fault
- In blockchains, consistency is sacrificed in favor of availability and partition tolerance
- Consistency is not achieved simultaneously with Availability and Partition tolerance, but is achieved over time
- This is called eventual consistency where consistency is achieved as a result of validation from multiple nodes over time