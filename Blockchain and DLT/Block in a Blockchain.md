![[blockchain-data-structure.svg]]

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

## Structure of a Block Header

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

## The Genesis Block

- It is the first block in the **Bitcoin** blockchain
- It is common ancestor of all the blocks in the blockchain
- If you start at any block and follow backward in time, you will arrive at the genesis block
- The genesis block is statically encoded within the bitcoin client software, such that it cannot be altered
- Every node always *knows* the genesis block's hash and structure, the time it was created and the single transactions inside it
- Every node has the starting point for the blockchain, a secure *root* from which to build a trusted blockchain
- It is in the *chainparams.cpp* file
- The identifier hash of the genesis block is : `000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f`
- Using  the Bitcoin Core reference client on the command line :

`$ bitcoin-cli getblock 000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f`
```json
{
	"hash" : "000000000019d6689c085ae165831e934ff763ae46a2a6c172b3f1b60a8ce26f",
	"confirmations" : 308321,
	"size" : 285,
	"height" : 0,
	"version" : 1,
	"merkleroot" : "4a5e1e4baab89f3a32518a88c31bc87f618f76673e2cc77ab2127b7afdeda33b",
	"tx" : [
		"4a5e1e4baab89f3a32518a88c31bc87f618f76673e2cc77ab2127b7afdeda33b"
	],
	"time" : 1231006505,
	"nonce" : 2083236893,
	"bits" : "1d00ffff",
	"difficulty" : 1.00000000,
	"nextblockhash" : "00000000839a8e6886ab5951d76f411475428afc90947ee320161bbf18eb6048"
}
```

- The genesis block contains a hidden message within it
- The coinbase transaction input contains the text :
> The Time 03/Jan/2009 Chancellor on brink of second bailout for banks
- This message was intended to offer proof of the earliest date this block was created, referencing the headline of the British newspaper *The Times*
- The message was embedded in the first block by **Satoshi Nakamoto**, bitcoin's creator

## Linking Blocks in the Blockchain

- Bitcoin full nodes maintain a local copy of the blockchain, starting at the genesis block
- The local copy of the blockchain is constantly updated as new blocks are found and used to extend the chain
- As a node receives incoming blocks from the network, it will validate these blocks and then link them to the existing blockchain
- To establish a link, a node will examine the incoming block header and look for the *previous block hash*
---
- For example, a node has 277,314 blocks in the local copy of the blockchain
- The last block the node knows about is block 277,314 with a block header hash of : `00000000000000027e7ba6fe7bad39faf3b5a83daed765f05f7d1b71a1632249`
- The node then receives a new block from the network :
```json
{
  "size" : 43560,
  "version" : 2,
  "previousblockhash" : "00000000000000027e7ba6fe7bad39faf3b5a83daed765f05f7d1b71a1632249",
  "merkleroot" : "5e049f4030e0ab2debb92378f53c0a6e09548aea083f3ab25e1d94ea1155e29d",
  "time" : 1388185038,
  "difficulty" : 1180923195.25802612,
  "nonce" : 4215469401,
  "tx" : [
	"257e7497fb8bc68421eb2c7b699dbab234831600e7352f0d9e6522c7cf3f6c77",
	#[... many more transactions omitted ...]
	"05cfd38f6ae6aa83674cc99e4d75a1458c165b7ab84725eda41d018a09176634",
  ]
}
```
- The node finds the `previousblockhash` field, which contains the hash of its parent block
- It is a hash known to the node which is of the last block on the chain at height 277,314
- Therefore, this new block is a child of the last block on the chain and extends the existing blockchain
- The node adds this new block to the end of the chain, making the blockchain longer with a new height of 277,314

![[linking-blocks.svg]]

