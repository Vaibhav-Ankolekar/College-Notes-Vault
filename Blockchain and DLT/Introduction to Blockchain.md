# Technical definition of Blockchain

- Blockchain is a peer-to-peer, distributed ledger that is cryptographically-secure, append-only, immutable, and updateable only via consensus or agreement among peers.

- Blockchain is an ever-growing, secure, shared record keeping system in which each user of the data holds a copy of the records, which can only be updated if all parties involved in a transaction agree to update.

Important keywords in the definitions

1. **Peer-to-peer**
	- There is no central controller in the network
	- All participants talk to each other directly
2. **Distributed ledger**
	- A ledger is spread across the network among all peers in the network
	- Each peer holds a copy of thr complete ledger
3. **Cryptographically-secure**
	- Cryptography has been used to provide security services which make the ledger secure against tampering and misuse
	- These include non-repundiation, data integrity and data origin
4. **Append-only**
	- Data can only be added to the blockchain in _time-ordered sequential order_
	- Once data is added to the blockchain, it is almost impossible to change that data (immutable)
	- It can be changed in rare scenarios wherein collusion against the blockchain network succeeds in gaining more than 51% of the power.
5. **Updateable via consensus**
	- Consensus - agreement between group of people
	- No central authority is in control of updating the ledger
	- Any update made to the blockchain is validated against strict criteria defined by the blockchain protocol
	- Any updated in added to the blockchain only after a consensus has been reached among all participating peers/nodes on the network

# Elements of a blockchain

![[blockchain_generic_structure.png]]

1. **Address**
	- unique identifiers used in blockchain transaction to denote senders and receivers
	- usually a public key or dervied from a public key
	- Addresses are unique i.e. users generate new address for each transaction
2. **Transaction**
	- Record of an event
	- Represents a transfer of value from one address to another
3. **Block**
	- Made up of transactions i.e. selection of transactions bundled together and organized logically
	- It consist of multiple transactions, previous block hash, timestamp and nonce
4. **Peer-to-peer network**
	- Network topology wherein all peers can communicate with each other and send and receive messages
5. **Scripting/Programming Language**
	- Scripts or programs perform various operations on a transaction in order to facilitate various functions
	- Bitcoin uses Script language and Ethereum uses Solidity language.
6. **Virtual machine**
	- It allows code to be run on a blockchain as smart contracts
	- Ethereum Virtual Machine (EVM) is uded in Ethereum blockchain while Chain Virtual Machine (CVM) is used in Chain Core blockchain
7. **State machine**
	- Blockchain can be viewed as a state transition mechanism
	- State is modified from initial form to the next one and eventually to a final form by nodes
	- This is the result of a transaction execution, validation and finalization process
8. **Node**
	- A node performs various functions depending on the role that is takes on
	- It can propose and validate transactions and perform mining to facilitate consensus and secure the blockchain
	- It can perform simple payment verification and validation.
	- It can also perform transaction signing function.
9. **Smart Contract**
	- These programs run on top of thr blockchain and encapsulate the business logic to be executed when certain conditions are met
	- These programs are enforceable and automaticcaly executable

# Features of Blockchain

# Type of Blockchain

1. Public Blockchain
2. Private Blockchain
3. Hybrid Blockchain
4. Consortium Blockchain