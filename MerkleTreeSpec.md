# Balance Merkle Tree Spec

The conceptual framework is as follows:

* Each node leads has one or two children.
* If a node has **two children** both must be nodes. In this case, the hash of the node is equal to `H( C0 ++ D ++ C1 )`. 

	`Cn` is the hash of the `n`th child.
	H( ) is the hash function
	++ is concat
	D is the 'depth', or distance from the leaves of the children.
	D is expressed as one byte. 0 <= D <= 255
	assert Depth(C0) == Depth(C1)

* If the node has **one child** and that *child is a node*, the hash of the node is equal to `H( C0 ++ D ++ C0 )`.
* If the node has **one child** and that *child is data*, the hash of the node is equal to `C0`. 
* *Note:* `Cn` refers to the hash of the 0th child, which is `H( <data> )` in the case of data. Practically: `Cn = child[n].gethash()`
* Each node has a depth parameter. Three things are true:

	node.depth = node.child[0].depth + 1
	assert node.child[0].depth == node.child[1].depth
	data.depth = -1

There is an obvious exception here for nodes with only one child, in the case of the second rule.

# Byte Array Number Things spec (BANT) (WORKING/NONFINAL)

A BANT can be simultaneously thought of as a byte array, string, or number. When arithmetic options are applied it acts as a number, and when string/array operations (slice, reverse, concat, etc) are applied they act as expected.

BANTs are hashed as though they were a string.

All data is a BANT.