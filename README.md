# MerkleRootCalculator

## How do Merkle trees work?

A Merkle tree summarizes all the transactions in a block by producing a digital fingerprint of the entire set of transactions, thereby enabling a user to verify whether or not a transaction is included in a block.

Merkle trees are created by repeatedly hashing pairs of nodes until there is only one hash left (this hash is called the Root Hash, or the Merkle Root). They are constructed from the bottom up, from hashes of individual transactions (known as Transaction IDs).

Each leaf node is a hash of transactional data, and each non-leaf node is a hash of its previous hashes. Merkle trees are binary and therefore require an even number of leaf nodes. If the number of transactions is odd, the last hash will be duplicated once to create an even number of leaf nodes.

Let’s look at an example of four transactions in a block: A, B, C, and D. Each of these is hashed, and the hash stored in each leaf node, resulting in Hash A, B, C, and D. Consecutive pairs of leaf nodes are then summarized in a parent node by hashing Hash A and Hash B, resulting in Hash AB, and separately hashing Hash C and Hash D, resulting in Hash CD. The two hashes (Hash AB and Hash CD) are then hashed again to produce the Root Hash (the Merkle Root).

This process can be conducted on larger data sets, too: consecutive blocks can be hashed until there is only one node at the top. Hashing is usually conducted using the SHA-2 cryptographic hash function, though other functions can also be used.

The Merkle Root summarizes all of the data in the related transactions, and is stored in the block header. It maintains the integrity of the data. If a single detail in any of the transactions or the order of the transactions changes, so does the Merkle Root. Using a Merkle tree allows for a quick and simple test of whether a specific transaction is included in the set or not.

A Merkle tree differs from a hash-list in that with a Merkle tree, one branch can be downloaded at a time and the integrity of each branch can be immediately verified, even if the rest of the tree is not yet available. This is advantageous because files can be split up into very small data blocks, such that only small blocks need to be downloaded again if the original version is damaged.
