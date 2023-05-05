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

![[blockchain-generic-structure.svg]]

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

## Public Blockchain

- They are not owned by anyone
- They are open to the public and anyone can participate as a node in the decision-making process
- Users may or may not be rewarded for their participation
- All users of these *permissionless* or *unpermissioned* ledgers maintain a copy of the ledger on their local nodes
- They use a distributed consensus mechanism to decide the state of the ledger
- e.g. Bitcoin and Ethereum

Advantages
- They are completely independent of organizations, so if the organization that started it disappear or leaves, the public blockchain will still be able to run
- Some blockchains provides rewards for users who commit computer power to secure the network
- The network's transparency and security

Disadvantages
- The network can be slow and companies can't restrict access or use. The network slows down as more nodes join the network
- If hackers gain 51% or more of the computing power of a public blockchain network, they can alter it
- They don't scale well

Uses cases
- Mining and exchanging cryptocurrencies like Bitcoin
- Creating fixed record with an auditable chain of custody such as electronic notarization of affidavits and public records of property ownership

### Private Blockchain
- They are open only to a group of individuals or organization who have decided to share the ledger among themselves
- They work in a restrictive environment like a closed network or under the control of a single entity
- Also known as permissioned or enterprise blockchain
- e.g. HydraChain and Quorum

Advantages
- Controlling organization sets permission levels, security authorizations and accessibility
- It determines which nodes can view, add or changed data
- It prevents third parties from accessing certain information
- Because they're limited in size, private blockchains can be very fast and can process transactions much more quickly than public blockchain

Disadvantages
- They aren't considered true blockchain
- Difficult to fully achieve trust in the information, since centralized nodes determine what is valid
- Small number of nodes can also mean less security and also biased consensus method

Use cases
- Speed of private blockchain makes them ideal for cases where the blockchain needs to be cryptographically secure
- Supply chain management, asset ownership and internal voting

### Hybrid Blockchain
- They are also called Semiprivate blockchain
- It combines elements of both private and public blockchain
- It lest organizations set up a private, permission-based system alongside a public permissionless system
- It allows them to control who can access specific data stored in the blockchain and what data will be open up publicly
- Transactions and records in a hybrid blockchain are not make public but can be verified when needed, by allowing access through a smart contract
- When user joins a hybrid blockchain, they have full access to the network
- The user's identity is protected from other users, unless they engage in a transaction

Advantages
- Works within a closed ecosystem, outside hackers can't mount a 51% attack on the network
- It also protects privacy but allows for communication with third parties
- Transactions are cheap and fast
- It offers better scalability than a public blockchain network

Disadvantages
- This isn't completely transparent because information can be shielded
- Upgrading can also be a challenge
- There is no incentive for users to participate or contribute to the network

Use cases
- Companies can use a hybrid blockchain to run systems privately but show certain information, such as listings, to the public
- Medical records can be stored in a hybrid blockchain

### Consortium Blockchain
- Also known as a federated blockchain
- It is similar to a hybrid blockchain, i.e. having both private and public blockchain features
- Multiple organizational members collaborate on a decentralized network
- It is private blockchain with limited access to a particular group, eliminating the risks that come with just one entity controlling the network on a private blockchain
- The consensus procedures are controlled by preset nodes
- It has a validator node that initiates, receives and validates transactions
- Member nodes can receive or initiate transactions

Advantages
- These tends to be more secure, scalable and efficient than a public blockchain
- Like private and hybrid blockchain, it also offers access controls

Disadvantages
- It is less transparent than public blockchain
- It can still be compromised if a member node is breached
- The blockchain's own regulations can impair the network's functionality

Use cases
- Banking and payment are two uses for this type of blockchain
- Different banks can band together and form a consortium, deciding which nodes will validate the transactions
- Research organizations can also create a consortium model
- It's ideal for supply chains, particularly food and medicine applications