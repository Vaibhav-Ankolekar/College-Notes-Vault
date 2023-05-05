- Each block in the bitcoin blockchain contains a summary of all the transactions in the block using a *Merkle tree*
- It is a binary tree in which the inputs are first placed at the leaves and then the values of pairs of child nodes are hashed together to produce a value for the parent node until a single hash value known as *Merkle root* is achieved
- The cryptographic hash algorithm used in bitcoin's Merkle trees is SHA-256 applied twice, also known as double SHA-256
- The Merkle tree is constructed bottom-up
---
For example

![[merkle-tree-example1.svg]]

- We have 4 transactions, A, B, C and D, which form the *leaves* of the Merkle tree
- The transactions are not stored in the Merkle tree, rather, their data is hashed and the resulting hash is stored in each leaf node as H$_A$, H$_B$, H$_C$ and H$_D$
$$H_A = SHA256(SHA256(Transaction A))$$
- Consecutive pairs of leaf nodes are then summarized in a parent node by concatenating the two hashes and hashing them together
- To construct the parent node H$_{AB}$ the two 32 byte hashes of the children are concatenated to create a 64-byte string
- That string is then double-hashed to produce the parent node's hash
$$H_{AB} = SHA256(SHA256(H_A + H_B))$$
- The process continues until there is only one node at the top, the node known as the Merkle root
- That 32-byte hash is stored in the block header and summarizes all the data in all four transactions
---

![[merkle-tree-example2.svg]]

- The Merkle tree is a binary tree, it needs an even number of leaf nodes
- If there is an odd number of transactions to summarize, the last transaction hash will be duplicated to create an even number of leaf nodes
- This make Merkle tree a *balanced tree*
- Here, If we have only 3 transactions A, B and C then transaction C is duplicated
---

![[merkle-tree-example3.svg]]

- Same method for constructing a tree from four transactions can be generalized to construct trees of any size
- In Bitcoin, it is common to have thousand transactions in a single block
- These are summarized in exactly same way, producing just 32 bytes of data as the single Merkle root
- In above, a tree is built from 16 transactions
- Although the root looks bigger, it is the exact same size, just 32 bytes
- The Merkle root will always summarize hundred thousand transactions into 32 bytes
---

![[merkle-tree-example4.svg]]

- To find if a specific transaction is included in a block, a node only needs to produce $log_2(N)$ 32-byte hashes
- These hashes form a path called *authentication path* or *Merkle path*
- As the number of transaction increases, the base-2 logarithm of number of transaction increases slowly
- This allow Bitcoin nodes to efficiently produce paths of 10 or 12 hashes which can provide proof of a single transaction out of more than a thousand transactions in a block
- A node can find that a transaction K is included in the block by producing a Merkle path that is only four 32-byte hashes long (128 bytes)
- The path consists of the four hashes H$_L$, H$_{IJ}$, H$_{MNOP}$ and H$_{ABCDEFGH}$
- With these 4 hashes provided, the node can find that H$_{K}$ is included in the Merkle root by computing 4 additional pair-wise hashes H$_{KL}$, H$_{IJKL}$, H$_{IJKLMNOP}$ and the Merkle root

Amount of data that needs to be exchanged as a Merkle path to find if a transaction is part of a block or not

| Number of transactions | Aprrox. size of block | Path size (hashes) | Path size (bytes) |
|---|---|---|---|
| 16 transactions | 4 kilobytes | 4 hashes | 128 bytes |
| 512 transactions | 128 kilobytes | 9 hashes | 288 bytes |
| 2048 transactions | 512 kilobytes | 11 hashes | 352 bytes |
| 65,535 transactions | 16 megabytes | 16 hashes | 512 bytes |

- Nodes that do not store a full blockchain is called Simplified Payment Verification (SPV) nodes
- These use Merkle paths to verify transactions without downloading full blocks