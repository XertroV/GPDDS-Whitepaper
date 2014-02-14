# GPDDS Spec

GPDDS stands for General Purpose Distributed Data Structure

## What this document is

This is the working draft of what may eventually become the GPDDS standard, which aims to describe how GPDDS nodes should communicate.

This document does not specify anything about the nature of data stored in GPDDS. Provided there is consensus on what should be returned for a particular query potentially anything can be stored. Baked into the idea of GPDDS is the notion of hash trees in order to efficiently reference data, and also provide provable membership.

## The Gist

GPDDS describes a network of nodes which self-organise such that the topology of the network reflects the data the client is concerned with. In the same way that Bitcoin nodes operate over the internet and self-organise into the network we call Bitcoin, nodes of GPDDS organise based around the particular branches they wish to explore.

Nodes talk to one another their communication is simple. They know how to:

* Handshake
* Advertise Tree
* Request Tree
* Request Branch
* Friend operations

Everything beyond those operations is considered to be state based operations and outside the scope of GPDDS.

GPDDS is a network of distributed data structures where each structure is organised into a tree. 