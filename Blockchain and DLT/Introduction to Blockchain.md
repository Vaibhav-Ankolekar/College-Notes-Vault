# Technical definition of Blockchain

- Blockchain is a peer-to-peer, distributed ledger that is cryptographically-secure, append-only, immutable, and updateable only via consensus or agreement among peers.

- Blockchain is an ever-growing, secure, shared record keeping system in which each user of the data holds a copy of the records, which can only be updated if all parties involved in a transaction agree to update.

Important keywords in the definitions

1. **Peer-to-peer**
	- There is no central controller in the network
	- All participants talk to each other directly
2. **Distributed ledger**
	- A ledger is spread across the network among all peers in the network
	- Each peer holds a copy of the complete ledger
3. **Cryptographically-secure**
	- Cryptography has been used to provide security services which make the ledger secure against tampering and misuse
	- These include non-repudiation, data integrity and data origin
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

![[blockchain_generic_structure.svg]]

1. **Address**
	- unique identifiers used in blockchain transaction to denote senders and receivers
	- usually a public key or derived from a public key
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
	- Ethereum Virtual Machine (EVM) is used in Ethereum blockchain while Chain Virtual Machine (CVM) is used in Chain Core blockchain
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
	- These programs run on top of the blockchain and encapsulate the business logic to be executed when certain conditions are met
	- These programs are enforceable and automatically executable

# Features of Blockchain

1. **Distributed consensus**
	- It is the primary feature of blockchain
	- It allows a blockchain to present a single version of the truth
	- It is agreed upon by all the parties without the requirement of a central authority
2. **Transaction verification**
	- Transactions posted from the nodes on the blockchain are verified based on a predetermined set of rules
	- Only valid transactions are selected for inserting in a block
3. **Platform for smart contracts**
	- Blockchain is a platform on which programs can run to execute business logic on behalf of the users
	- Not all blockchain have a mechanism to execute *smart contracts*
	- It is available on Ethereum and MultiChain
4. **Smart Contracts**
	- There are automated and autonomous programs that reside on the blockchain network
	- They encapsulate the business logic and code needed to execute required function when required
	- They can be programmed to perform any actions that blockchain users need and according to their specific business requirements
5. **Transferring value between peers**
	- Blockchain enables the transfer of value between its users via tokens
	- Tokens can be thought of as a carrier of value
6. **Generation of cryptocurrency**
	- This is an optional feature
	- A blockchain can create cryptocurrency as an incentive to its miners who validate the transactions and spend resources to secure the blockchain
7. **Smart Property**
	- It is now possible to link a digital or physical asset to the blockchain in secure and precise manner that it cannot be claimed by anyone else
	- You are in full control of your asset and it cannot be double-spent or double-owned
8. **Provider of security**
	- The blockchain is based on proven cryptographic technology that ensures the integrity and availability of data
	- Confidentiality is not provided due to the requirement of transparency
	- This limitation is the leading barrier of its adoption by financial institutions and other industries that require privacy of transactions
	- In Bitcoin, confidentiality is not an absolute requirement as transparency is preferred
	- Other security services, such as non-repudiation and authentication are also provided, as all actions are secured using private keys and digital signatures
9. **Immutability**
	- Once records are added to the blockchain, they are immutable
	- There is a remote possibility of rolling back changes, but this is to be avoided at all costs as doing so would consume large amount of computing resources
	- This difficulty makes the records on a blockchain essentially immutable
10. **Uniqueness**
	- This feature ensures that every transaction is unique and has not already been spent (double-spend problem)
	- This feature is especially relevant with cryptocurrencies, where detection and avoidance of double spending are a vital requirement

# Type of Blockchain

### Public Blockchain
- They are not owned by anyone
- They are open to the public and anyone can participate as a node in the decision-making process
- Users may or may not be rewarded for their participation
- All users of these *permissionless* or *unpermissioned* ledgers maintain a copy of the ledger on their local nodes
- They use a distributed consensus mechanism to decide the state of the ledger
- e.g. Bitcoin and Ethereum

### Private Blockchain
- They are open only to a group of individuals or organization who have decided to share the ledger among themselves
- e.g. HydraChain and Quorum

### Hybrid Blockchain
- They are also called Semiprivate blockchain
- Part of the blockchain is private and part of it is public
- This is just a concept and no real world POCs have yet been developed
- The private part remains internal and shared among known participants, while the public part is open for participation by anyone
- Blockchain as a whole can be secured using PoW, thus providing consistency and validity for both private and public parts

### Consortium Blockchain