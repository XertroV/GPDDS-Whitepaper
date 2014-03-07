# General Purpose Distributed Hash Tables

Authors:

* Jack Murray
* Max Kaye
* ??

2014/2/3

## Abstract

Existing Distributed Hash Table (DHT) implementations verify the integrity of
shared data by comparing it against a known hash. For example, the "exact
topic" part of the Magnet URI scheme is simply a hash of the desired data.

This method only works in cases where a hash of the data is known in advance,
and a secure timestamp of the data is not required.

The proof-of-work block chain used in the Bitcoin protocol could be used to
solve both these problems if valid blocks could contain arbitrary data.
However, it is not immediately clear that anybody would mine on a such a block
chain where there are no inherent rewards.

We speculate that this kind of modular block chain would soon see "plugin
protocols" that offer their own form of reward for the inclusion of data into
the block chain, and that this secondary reward would be enough to pay for the
proof of work.

This paper explores the use of a single block chain as a means of implementing
a secure, general purpose DHT that is available for use by different protocols
simultaneously. This has the added benefit of combining proof of work to
increase the security of every participating protocol.

### Background

### Problems

### A Solution

## Previous Blockchain Implementations

### Structure

### Functions

### Assumptions and Superfluous Structure

### Merged Mining

## Amorphous Hash Tree

### Overview

### Self Similarity

### Advantages in a Heterogeneous Network

### Differences to Previous Implementations

#### Advantages

#### Disadvantages

### The Role of Consensus

## Roles and Functions

### Mining

### Block Explorer

### Provability

## Example Use

### Every Currency is a Metacurrency

### Incentivising Miners

### Building Under *coin

### Cross Chain Payments, Markets, and Interdependance

## Conclusion

