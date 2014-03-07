# Blockchains

## A note on consensus

There is two parts to the consensus behind Bitcoin et al.

1. Agree on the network protocol
2. Agree on the financial state

The first occurs when a user downloads Bitcoin-QT or w/e. The second occurs while running through the blockchain while calculating the current state.

They can be separated.

## History and Contemporary Blockchains

Blockchains are, obviously, chains of blocks. A chain in this case refers to an append only instruction set for creating the Bitcoin state. Blocks are a collection of transactions organised in a specific way with specific properties (one of these is the PoW requirement). A transaction is an instruction to insert data into the database. This instruction is appended, in a block, to the blockchain, which is then used to calculate the next state of the financial Bitcoin network.

The blockchain has a few functions:

* Act as a governor (like an engine) for database insertions
* Authenticate insertions via PoW
* Record transactions in a chain


## New blockchain idea

The blockchain should be stratified such that financial information and database updates are extricated from one another.

### Suggested network structure

Each node works in three layers:

* PoW Prism (GPDDS node)
* Statemaker
* Interpreter

GPDDS is only concerned with the topmost.

Briefly, the **statemaker** is what takes transactions (which is really just some data) and operates on the data to update the state of the financial network. This level **confirms chain updates are valid and updates the state deterministically**.

The **interpreter** is the most removed and interprets the state into some meaning. This is your wallet, the distributed market client, the voting client, etc. This level **gives data meaning**.

The **PoW prism** manages updates to the append-only database. When you send transactions (again, just blocks of data) you give it to the PoW prism and the prism sends it into the network. If an auditor finds your data acceptable they may choose to include it in their next PoW update.

The PoW prism knows *nothing* about the financial network.

### What happens when a new block is found with GPDDS

So, firstly we need to be clear what a **block** is, since it is currently many things in one big package. Let us describe one:

* Has a block header, which, when hashed should conform to PoW standards
* The header includes a merkle root of the corresponding tree comprising all transactions included in the block
* All transactions are included and counted towards the block size

They can briefly be thought of as PoW, merkle tree, leaves.

That is the relevant part of what Bitcoin thinks a block is.

GPDDS generalises this structure. Forget the idea of a block and a fixed size; there are many assumptions baked into the idea of a block as we understand it now.

In GPDDS when PoW is found the corresponding tree is distributed through the prism. This is the equivalent of Bitcoin distributing block headers.

Let's presume this tree comprises of (key, value) pairs; keys corresponding to a chain's genesis block, and values to the latest hash. The local node then asks the network for the value behind this latest hash. The network responds with the 'block header' which is really just the metadata about what's to come. This includes things like version, transaction merkle root, state merkle root, uncles and the parent block, the hash of the 'root contract' (rules defining the financial protocol, perhaps), and the Chainproof. The data provided must form a merkle tree with the correct merkle root (which is what you originally asked for). This means nodes can't lie about the database, because everything is cryptographically authenticated back to the PoW update.

If we are dealing with a 'full node' then the prism is instructed to attempt to acquire the relevant subtree. In the case of a Bitcoin-like structure, the prism would request the merkle tree of the root provided in the block header. This is the list of all transactions in the block, each of which is then requested from the network. At this point the node has all the data needed to verify the financial state is valid by running through the insertions (transactions).


## Advantages

* Really quick block propogation
* Potentially 'infinite' blockchain
* All currencies using the same PoW can work together but don't need to know about each other
* Financial meaning doesn't penetrate the data network beneath it
* Dark chains
* Easy forks
* Chains can easily provide SPV capability on partner chains

## Other ideas I've included but not fully explained

### Chainproof

An incremental merkle tree describing the past blocks. In this way one can very easily prove that a block was in the main chain, even if it was 100,000 blocks ago. My BOTE calculation puts a worst case operation at about 22 hashes with 280,000 blocks.

### Root Contract

It'd be really cool to have the network rules be described by a protocol written in the network rules. Then people could PoS vote on changing things like block reward or w/e. It also provides a way to track forks in SPV.

### Why not just vote on the PoW target?

Why not just have an ongoing vote on the PoW target? I think there are many advantages to doing this over prescribing how PoW should operate in the network spec.