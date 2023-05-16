# Overview

#### Bulletproofs

The range proofs are derived from a zero-knowledge proof scheme called _Bulletproofs_. This is an instantiation of a special class of range proofs where the sender proves in zero-knowledge (i.e. without revealing any other information about the transaction) that the masked (or committed) amount falls within a certain range. In particular, a sender can use this scheme to prove that the amount he sent is non-negative and does not exceed his balance, which is necessary to prevent double-spending on the chain. This is a _transparent_ scheme, meaning it does not require any preprocessing phase or trusted setup. The security of Bulletproofs relies on the hardness of the discrete logarithm problem in elliptic curves, which is one of the oldest and most battle-tested assumptions in cryptography.

We first describe a straightforward albeit inefficient way to create a range proof. The Prover decomposes the integer representing the amount into its binary representation. He then creates commitments to each of those bits and then sends a proof attesting to the claim that each of these commitments is to a bit and that the amount is the aggregation of these bits. But this proof size is linear in the bit length of the amount, which is quite inefficient in practice. Bulletproofs is an efficient range proof which is logarithmic in the size of the amount. The core of the bulletproof protocol hinges on a technique called the _recursive inner product argument_.

[Check this link](basics/bulletproofs.md) for details on the Bulletproofs-based mixing protocol
