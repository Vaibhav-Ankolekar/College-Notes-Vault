## Structure of a Block

- A block is a container data structure that aggregates transactions for inclusion in the public ledger, the blockchain
- The block is made of 
	- header
	- containing metadata
	- long list of transactions
- The block header is 80 bytes
- The average transaction is at least 250 bytes
- The average blockchain contains more than 500 transactions
- A complete block will all transactions is 1000 times larger than the block header
- The structure of a block

| Field | Size | Description |
|---|---|---|
| Block Size | 4 bytes | The size of the block, in bytes |
| Block Header | 80 bytes | Several fields form the block header |
| Transaction Counter | 1-9 bytes (VarInt) | Total number of transactions in the block |
| Transactions | Variable | All transactions recorded in this block |

## Block Header

- It consist of three sets of block metadata
1. Reference to a previous block hash, which connects this block to the previous block in the blockchain
2. Difficulty, timestamp and nonce
3. Merkle tree root, a data structure used to efficiently summarize all the transactions in the block

| Field | Size | Description |
|---|---|---|
| Version | 4 bytes | A version number to track software/protocol upgrades |
| Previous Block Hash | 32 bytes | A reference to the hash of the previous block in the chain |
| Merkle Root | 32 bytes | A hash of the root of the Merkle tree of this block's transactions |
| Timestamp | 4 bytes | The approximate creation time of this block |
| Difficult Target | 4 bytes | The Proof-of-Work algorithm difficulty target for this block |
| Nonce | 4 bytes | A counter used for the Proof-of-Work algorithm |

- The nonce, difficulty target, and timestamp are used in the mining process

## Block Header Hash

- The primary identifier of a block is its cryptographic hash
- It is a digital fingerprint made by hashing the block header twice through the SHA-256 algorithm
- The resulting 32 byte hash is called the *block hash* or *block header hash*
- It identifies a block uniquely and unambiguously
- It can be independently derived by any node by simply hashing the block header
- It is not included in the block's data structure
- It is computed by each node as the block is received from the network
- It can be stored on a separate database table for indexing and fast retrieval of block from disk

## Block Height

- The secondary identifier of a block is its block height
- It is the position of the block in the blockchain
- The first block created is at block height 0 (zero)
- Each block added on top of the first block is one position *higher* in the blockchain
- It is not a unique identifier
- Two or more block might have the same block height, competing for the same position in the blockchain
- It is also not a part of the block's data structure
- It can be stored as metadata in an indexed database for fast retrieval

![[blockchain-data-structure.svg]]

## The Genesis Block

## Linking Blocks in the Blockchain

## Merkle Tree