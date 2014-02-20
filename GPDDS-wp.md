# GPDDS - General Purpose Distributed Data Structure

## The infinite blockchain and other tales

Max Kaye
Rev 01 - 13/2/14

## Introduction

Bitcoin introduced the blockchain - a method for establishing consensus over a distributed (and potentially anonymous) community. While Bitcoin's blockchain is adequate for Bitcoin's purposes, we suggest novel improvements to the data structure to allow for far greater flexibility, unification of chains using the same proof-of-work (PoW) algorithm, the potential to provide consistency for an arbitrary amount of data, and cross-chain awareness.

To do this, we separate the notion of consensus on the *state* of a Bitcoin-like network (which is based on common agreement), from the notion that suggested increments to the state (a.k.a. a block) must be difficult to create.

## The Purpose of a Blockchain

Often simply explained as a 'distributed consensus mechanism', the blockchain is an incredibly useful device. It keeps memory usage predictable thus helping keeping the network safe from spam. It resolves differences of opinion if an attempt to doublespend occurs.

However, PoW is not enough on its own, it is also very important to maintain the append-only data structure; if PoW were offered on every transaction (just as hashcash is suggested to be used for an individual email) that could provide mechanisms to resolve or prevent doublespends, but it would not provide a way to organise the transaction graph into a chronological and stable structure.

So, we can see there are many functions of the blockchain: rate-limiting / spam prevention, doublespend prevention, and chronological, stable scaffolding.

### The Blockchain as a Governor

A [governor](http://en.wikipedia.org/wiki/Governor_%28device%29) is a rate-limiting device in an engine designed to regulate the operational speed.  This is achieved through the creation and enforcement of a stable equilibrium.

Part of the function of a blockchain is to keep the volume of insertions to the ledger manageable by creating a great barrier to that insertion. Currently - according to the Bitcoin protocol - this takes the form of requiring a user to craft an insertion such that applying the SHA256 hashing algorithm twice results in a number less than a specified target. The target is recalculated regularly and deterministically to allow the network to grow and shrink while maintaining a pre-determined rate of block production. When an auditor overcomes said barrier they are rewarded, as defined by the agreed upon coin protocol.

In this way, the target acts as a governor for the blockchain, preventing updates occurring too frequently, both for manageability and as a way to minimise waste. Bitcoin, and many alt-chains, suffer from wasted work to a small degree. As the target rate is increased (blocks become more frequent) the degree to which work is wasted also increases. These issues were solved (in part) by GHOST [2], a proposed structural addition to a blockchain which integrates the PoW from blocks not included in the main chain. This allows a large uncertainty at the end of the chain, but still guarantees the *most agreed upon* blocks are used as insertions to the chain, so that after a short period of time (perhaps a few minutes) the superposition at the end of the chain has collapsed into a stable state.






## References

* [1] S. Nakamoto [Bitcoin: A peer-to-peer electronic cash system](http://bitcoin.org/bitcoin.pdf)
* [2] Y. Sompolinsky and A. Zohar [Accelerating Bitcoin's Transaction Processing](https://eprint.iacr.org/2013/881.pdf)
* 
